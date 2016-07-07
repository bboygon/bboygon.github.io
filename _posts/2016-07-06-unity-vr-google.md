---
layout: post
title:  Unity VR with Google Cardboard
date:   2016-07-04 오전 4:37:31
categories: Unity
tags: Unity VR
---

- - - 

# 구글 VR 셋팅 및 인터렉션

시나리오 : 구글 안드로이드 VR 형태로 인터렉션을 처리해보자.

모바일 기기에서 자동 회전과 L/R Eye로 보기 위해 가로뷰로 고정  

- PlayerSetting> Orientation> Default Orientation> Landscape Left 로 설정

안드로이드 타겟이면 성능을 위해 텍스쳐 압축을 하는데 ETC2로 설정

- BuildSetting> TextureCompression> ETC2(GLES 2.0) 선택

이미 셋팅되어 있는 구글 VR 프리팹을 가져와서 VR 렌더링 환경을 만들기

- Project> GoogleVR> Prefabs> GvrMain 프리팹을 계층뷰에 가져다 놓기
- VR 카메라로 렌더링할 것이므로 계층뷰에 존재하는 Main Camera 게임 오브젝트 삭제

모바일 기기마다의 뷰 설정을 위해

- GvrMain 의 GvrViewer 속성 중 Screen Size 를 자신의 모바일에 맞게 변경
- GvrMain 의 GvrViewer 속성 중 Viewer Type 을 구글 카드보드 버전에 맞게 변경

UI 인터렉션을 위해 UI Event System 적용해보기

-  GvrMain> Head> Main Camera 의 인스펙터창에 Add Component로 Physics RayCaster 추가
-  툴바> GameObject> UI> Event System 선택
-  Event System 게임오브젝트에 Gaze Input Module 컴포넌트 추가
-  Gaze Input Module을 Standalone Input Module 보다 상위로 변경

오브젝트가 인터렉션 이벤트를 받을 수 있게 설정

- 툴바> GameObject> 3D Object> Cube 선택
- Cube 이름 변경 "EventTarget"
- EventTarget 오브젝트에 Event Trigger 컴포넌트 추가
- EventTrigger 에 Add New Event Type 선택

EventTarget 게임 오브젝트에 인터렉션시 어떤 변화를 줄지를 설정

- Event Trigger> Point Enter> [+] 버튼 클릭> None 에 자기 자신을 끌어다 놓기
- No Function 클릭> Mesh Rendeer> Material material 선택
- 아래에 빈 영역에 (0)버튼 클릭> CubeActiveMaterial 선택
- Add New Event Type> Point Exit> 방금 처럼 (0)버튼 클릭> CubeInactiveMaterial 선택


![]({{site.url}}/downloads/unity_gvr_interaction_headTracking.png ){:class="img-responsive" height="400px" width="800px"}


결과 : EventTarget 오브젝트가 헤드 트랙킹이 Enter/Exite 될 떄마다 마테리얼이 변화한다. 

- - -

# 응용 실습

- 활성화되었던 헤드 트랙 포인트가 오브젝트를 벗어나면 해당 게임 오브젝트가 사라지게 해본다.
- 힌트 : SetActive()를 사용

- - -

# 3D Radial Button 만들기



{% highlight csharp %}

using UnityEngine;
using System.Collections;
 
public class RadialCutoutMenu : MonoBehaviour {
 
    // How long to look at Menu Item before taking action
    public float timerDuration = 2f;
 
    // This value will count down from the duration
    private float lookTimer = 0f;
 
    // My renderer so I can set _Cutoff value
    private Renderer myRenderer;
 
    // Box Collider
    private BoxCollider myCollider;
 
    // Is player looking at me?
    private bool isLookedAt = false;
 
    // MonoBehaviour Start
    void Start() {
        // My Collider
        myCollider = GetComponent<BoxCollider>();
        // Get my Renderer
        myRenderer = GetComponent<Renderer>();
        // Set cutoff
        myRenderer.material.SetFloat("_Cutoff", 0f);
    }
   
    // MonoBehaviour Update
    void Update() {
        // While player is looking at me
        if (isLookedAt) {
            // Reduce Timer
            lookTimer += Time.deltaTime;
 
            // Set cutoff value on material to value between 0 and 1
            myRenderer.material.SetFloat("_Cutoff", lookTimer / timerDuration);
 
            if (lookTimer > timerDuration) {
                // Reset timer
                lookTimer = 0f;
   
                // disable collider
                myCollider.enabled = false;
 
                // Do something
                Debug.Log("BUTTON HAS BEEN SELECTED!");
 
                // Disappear
                gameObject.SetActive(false);
            }    
        }  else {
            // Reset Timer
            lookTimer = 0f;
            // Reset Cutoff
            myRenderer.material.SetFloat("_Cutoff", 0f);
        }
    }
 
    // Google Cardboard Gaze
    public void SetGazedAt(bool gazedAt) {
        // Set the local bool to the one passed from Event Trigger
        isLookedAt = gazedAt;
    }
}

{% endhighlight %}

Raw Parse Data


{% highlight csharp %}

using UnityEngine;
using System.Collections;

public class RadialCutoutMenu : MonoBehaviour {

    // How long to look at Menu Item before taking action
    public float timerDuration = 2f;

    // This value will count down from the duration
    private float lookTimer = 0f;

    // My renderer so I can set _Cutoff value
    private Renderer myRenderer;

    // Box Collider
    private BoxCollider myCollider;

    // Is player looking at me?
    private bool isLookedAt = false;

    // MonoBehaviour Start
    void Start() {
        // My Collider
        myCollider = GetComponent<BoxCollider>();
        // Get my Renderer
        myRenderer = GetComponent<Renderer>();
        // Set cutoff
        myRenderer.material.SetFloat("_Cutoff", 0f);
    }
    
    // MonoBehaviour Update
    void Update() {
        // While player is looking at me
        if (isLookedAt) {
            // Reduce Timer
            lookTimer += Time.deltaTime;

            // Set cutoff value on material to value between 0 and 1
            myRenderer.material.SetFloat("_Cutoff", lookTimer / timerDuration);

            if (lookTimer > timerDuration) {
                // Reset timer
                lookTimer = 0f;
    
                // disable collider
                myCollider.enabled = false;

                // Do something
                Debug.Log("BUTTON HAS BEEN SELECTED!");

                // Disappear
                gameObject.SetActive(false);
            }     
        }  else {
            // Reset Timer
            lookTimer = 0f;
            // Reset Cutoff
            myRenderer.material.SetFloat("_Cutoff", 0f);
        }
    }

    // Google Cardboard Gaze
    public void SetGazedAt(bool gazedAt) {
        // Set the local bool to the one passed from Event Trigger
        isLookedAt = gazedAt;
    }
}

{% endhighlight %}