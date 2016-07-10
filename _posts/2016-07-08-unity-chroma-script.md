---
layout: post
title:  Chroma Script 
date:   2016-07-08 오전 7:28:19   
categories: Unity
tags: Script
---

- - -

플랫한 크로마키 영상을 360 영상과 접목시킬때 카메라의 움직임에 따라 회전을 하게 만들어 봅니다.

### 계층 구조 설계

- 빈 게임오브젝트를 생성
- 자식으로 크로마키 영상을 게임오브젝트로 추가


### 구현 시나리오

- 부모인 빈 게임오브젝트는 카메라가 회전함에 따라 계속 쳐다볼 수 있게
- 자식인 영상 게임오브젝트는 카메라의 평면으로 보일 수 있게 회전값 지정


### 스크립트 구현

- 자식인 게임오브젝트의 x축을  90 로도 수정
- 부모인 빈 게임오브젝트에 스크립트 추가
 
{% highlight csharp %}

public class BillboardTest : MonoBehaviour{

	public Transform target;

	void Update()
	{
		//TransformLookAt은 타겟을 항상 바라본다.
		tranform.LookAt(target);
	}

}

{% endhighlight %}

- - -

빌보드 되는 크로마 영상을 움직이고 싶다면 부모 오브젝트의 Position을 수정하여 컨트롤이 가능합니다.

