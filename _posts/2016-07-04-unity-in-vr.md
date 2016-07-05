---
layout: post
title:  Unity In VR
date:   2016-07-04 오전 4:37:31
categories: Unity
tags: Unity VR
---

# 유니티 VR 소개
유니티에서 VR 기능을 사용하려면 VR 디바이스의 라이브러리가 필요.

- 엔진에 탑재된 VR Device Type 은
	- 다이렉트3D 11 또는 OpenGL을 통한 스테레오 3D
	- 스테레오 3D 스크린을 분할한 타입
	- 오큘러스 리프트
	- 플레이스테이션 VR
- HTC Vive와 같이 다른 HMD 장치들과 호환 가능

- - -
 
# 프로젝트에 VR 환경 셋팅

필수설치 : 오큘러스 런타임 0.8 , 유니티 5.3 이상 버전

Edit> Project Settings> Player> Other Settings> Rendering

![](https://unity3d.com/sites/default/files/learn/1_enable_vr.png ){:class="img-responsive"}
   
Virtual Reailty Supported 활성화

![](https://unity3d.com/sites/default/files/learn/2_enable_vr.png ){:class="img-responsive"}

게임 실행시 VR 세팅이 잘 되었는지 확인하려면

{% highlight ruby %}
using UnityEngine;
using UnityEngine.VR;

public class ToggleVR : MonoBehaviour
{
    //Example of toggling VRSettings
    private void Update ()
    {
        //If V is pressed, toggle VRSettings.enabled
        if (Input.GetKeyDown(KeyCode.V))
        {
            VRSettings.enabled = !VRSettings.enabled;
            Debug.Log("Changed VRSettings.enabled to:"+VRSettings.enabled);
        }
    }
}
{% endhighlight %}

- - -
- 
# 프리뷰 VR 유니티

유니티 에디터로 VR Support를 활성화했고, DK2가 연결되어 있다면 플레이시 게임뷰에서 동작하는 DK2를 볼 수 있습니다.

![](https://unity3d.com/sites/default/files/learn/3_enable_vr_cube.png ){:class="img-responsive"}

따로 추가적인 카메라를 생성하지 않아도 렌더 텍스쳐를 제외한 모든 카메라가 VR 환경에서 렌더링 됩니다.

[공식 문서 링크](http://docs.unity3d.com/kr/current/Manual/UnityOverview.html) , 
[VR 관련 스크립트 API](http://docs.unity3d.com/ScriptReference/30_search.html?q=VR&_ga=1.54576939.1427559285.1467735054)

하드웨어 및 소프트웨어의 제약사항이 있는데 공식 문서를 참고하면 됩니다.

- - -

# VR 샘플 프로젝트
   
샘플 프로젝트는 애셋 스토어에서 다운 받을 수 있습니다. 
[샘플 프로젝트](https://www.assetstore.unity3d.com/kr/#!/content/51519)

- - -
[유니티 VR 공식 문서](http://unity3d.com/kr/learn/tutorials/topics/virtual-reality)

![](https://d2ujflorbtfzji.cloudfront.net/package-screenshot/c9c66f7a-7df3-45cf-8167-becd144397f3_scaled.jpg ){:class="img-responsive"}

