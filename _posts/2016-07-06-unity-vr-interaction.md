---
layout: post
title:  인터렉션 처리
date:   2016-07-06 오전 2:10:33 
categories: Unity
tags: UnityVR
---


#### VR 카메라 이동
VR 카메라는 위치가 변하지 않기 때문에 위치를 변경하고 싶다면 상위 게임 오브젝트를 추가하여 해당 오브젝트로 위치를 변경하면 하위인 VR 카메라도 상위 게임오브젝트에 영향을 받게 된다.
  
#### 렌더 스케일
렌더링을 해상도 배수로 해주는 것인데 스케일 값에 따라 퍼포먼스와 선명함 사이에서 트레이드 오프 해야 합니다.

이 코드로 렌더 스케일을 조정할 수 있습니다.

{% highlight csharp %}

using UnityEngine;
using System.Collections;
using UnityEngine.VR;

namespace VRStandardAssets.Examples
{ 
    public class ExampleRenderScale : MonoBehaviour
    {
        [SerializeField] private float m_RenderScale = 1f;              //The render scale. Higher numbers = better quality, but trades performance

        void Start ()
        {
            VRSettings.renderScale = m_RenderScale;
        }
    }
}

{% endhighlight %}

