---
layout: post
title:  Chroma Script 
date:   2016-07-08 오전 7:28:19   
categories: Unity
tags: Unity VR CG
---


# 플랜 이미지 빌보드

플랫한 크로마키 영상을 360 영상과 접목시킬때 카메라의 움직임에 따라 회전을 하게 만들어 봅니다.

{% highlight csharp %}

public class BillboardScript : MonoBehaviour {

    public Camera referenceCamera;
	
	// 화면이 갱신될 때마다 reference 카메라를 쳐다봅니다.
	void Update () {

        //transform.LookAt( );

        transform.LookAt(referenceCamera.transform);
	}
}

{% endhighlight %}

- 플랜 추가> 빈 게임 오브젝트 추가> 플랜을 빈 게임오브젝트이 자식으로 연결
- 플랜의 Rotation x 값을 90으로 변경
- 부모 게임 오브젝트에 위의 스크립트를 붙입니다.
- 레퍼런스 카메라로 구글카메라를 연결
- 부모 게임 오브젝트를 원하는 곳으로 배치

- - -


# 크로마 영상 빌보드

