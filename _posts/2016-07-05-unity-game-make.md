---
layout: post
title:  Unity Game Making
date:   2016-07-05 오전 6:34:50  
categories: Unity
tags: Unity
---

- - -

# Scene 

Scenes에는 게임의 오브젝트가 포함되어 있습니다. 씬을 사용하여 메인 메뉴, 각각의 레벨 을 만들 수 있습니다. 하나의 씬 파일은 한 레벨로 생각하십시오. 각 씬에서는 환경과 장애물, 장식을 배치하고 주로 게임을 세세하게 디자인하고 만듭니다.

![](http://docs.unity3d.com/kr/current/uploads/Main/NewEmptyScene.png ){:class="img-responsive"}


# 씬 만들기

상단메뉴탭의 File - Save Scene 을 통해 현재 씬을 저장할 수 있습니다.

![](http://docs.unity3d.com/kr/current/uploads/Main/SceneAssetsInProjectView.png ){:class="img-responsive"}

저장을 하게 되면 그림과 같은 파일이 생성되고, 씬 파일을 열어 편집하거나 저장할 수 있습니다.

- - -  
  
# 게임 오브젝트(Game Objects)

게임 내의 모든 오브젝트는 모두 본질적으로 GameObject가 됩니다. 그러나 GameObject는 스스로 아무것도 하지 않습니다. 캐릭터나 환경, 특수 효과가 되려면 특수 속성이 필요합니다. 이 오브젝트는 모든 동작이 다릅니다. 모든 오브젝트가 GameObject인 경우, 스태틱 룸(Static room) 에서 파워 업 오브젝트를 어떻게 구별하는 걸까요? 이 GameObject를 서로 차별화하는 것은 무엇일까요?

![](http://docs.unity3d.com/kr/current/uploads/Main/GameObjectsExamples.png ){:class="img-responsive"}

이 질문에 대한 답변은, GameObject는 컨테이너(container)입니다. 이들은 빈 상자에서 라이트 맵 된 외딴 섬, 또는 물리적 특성 구동 차량을 구성하는 다양한 조각들을 저장할 수 있는 빈 상자입니다. 따라서 GameObject를 정말 이해하려면 각 부분을 이해해야 합니다. 이러한 조각은 Components라고 합니다. 생성할 오브젝트의 종류에 따라 다른 조합의 컴포넌트를 GameObject에 추가합니다. GameObject는 빈 냄비, 컴포넌트는 게임 플레이라는 요리법을 구성하는 각종 재료라고 생각해주세요. 스크립트를 사용하여 직접 컴포넌트를 만들 수 있습니다.

# 게임 오브젝트 활성화

게임오브젝트는 활성화/비활성화 기능이 있어 씬에서 일시적으로 기능을 제어할 수 있습니다. 

![](http://docs.unity3d.com/kr/current/uploads/Main/GOActiveBox.png ){:class="img-responsive"}

- - -

# 태그와 레이어
태그는 해당 게임오브젝트를 정의하는 단어입니다. 태그의 목적은 스크립트에서 제어하기 위함인데 "Player", "Enemy" 와 같은 태그를 가진 오브젝트를 찾을 때 사용할 수 있습니다.

{% highlight csharp %}

using UnityEngine;
using System.Collections;

public class Example : MonoBehaviour {
    public GameObject respawnPrefab;
    public GameObject respawn;
    void Start() {
        if (respawn == null)
            respawn = GameObject.FindWithTag("Respawn");
        
        Instantiate(respawnPrefab, respawn.transform.position, respawn.transform.rotation) as GameObject;
    }
}

{% endhighlight %}
  
레이어는 태그와 비슷하지만 게임 오브젝트가 어떠한 계층에 있을지를 지정합니다.  

- - -
 
# 컴포넌트 (Components)

게임 오브젝트 에는 여러 컴포넌트가 포함되어 있습니다. 가장 일반적인 컴포넌트로는 Transform 컴포넌트로 오브젝트의 좌표, 회전, 스케일에 관한 정보를 가지고 있습니다.

![](http://docs.unity3d.com/kr/current/uploads/Main/EmptyGO.png ){:class="img-responsive"}

이와 유사하게 다른 컴포넌트들도 각자의 기능과 역할에 맞는 정보를 가지고 있고, 빈 게임오브젝트에 컴포넌트를 부착하여 필요한 기능을 하는 게임 오브젝트로 변화하게 됩니다. 

![](http://docs.unity3d.com/kr/current/uploads/Main/GameObject-maincamera.png){:class="img-responsive"}

- - - 

# 속성 (Property)

속성은 컴포넌트 안에 있는 값들을 말합니다. 고로 컴포넌트는 기능을, 속성은 제어를 하는 것으로 이해하면 됩니다.

![]({{site.url}}/downloads/unity_go_comp_script_relation.png ){:class="img-responsive" height="400px" width="800px"}

- - -
 