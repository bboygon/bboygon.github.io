---
layout: post
title:  Unty Basic
date:   2016-07-04 오전 4:33:22
categories: Unity
tags: Unity
---


* * *

# 유니티 개념 학습
유니티 공식 문서를 통한 유니티3D 엔진의 기본 개념과 워크 플로우, 인터페이스를 학습합니다.

[공식 문서 링크](http://unity3d.com/kr/learn/tutorials/topics/virtual-reality)

- 유니티 다운로드 및 설치
- 유니티 작업 프로세스
- 에디터 컨트롤 및 기능 창 설명
- 게임 플레이를 위한 설명
	- 게임 씬
	- 게임오브젝트
	- 프리팹
	- 스크립트
	- 입력
	- 라이팅
	- 카메라
- 빌드 세팅 및 배포


- - -



# 스크립트를 통한 오브젝트 컨트롤
유니티에서 지원하는 스크립트의 동작과정을 살펴보고 어떻게 만들어 적용하는지에 대해 알아봅니다.

시나리오 : 오브젝트를 일정하게 회전시키고 싶다.

- GameObject -> 3D Object -> Cube
- Project View
	- 우클릭 -> Create -> C# Script -> 'Cube Script' 로 명명
	- Rename 'Cube'
	- Cube Script 를 Cube 오브젝트에 끌어다 놓기
	- ![]({{site.url}}/downloads/aaa.png ){:class="img-responsive" height="400px" width="800px"}

- CubeScript 파일 더블 클릭
- 열린 스크립트 파일 내부의 Update 함수를 수정

{% highlight ruby %}
void Update()
{
	transform.Rotate(new Vector3(1.0f, 1.0f, 1.0f));
}
{% endhighlight %}

시나리오 구현

- 오브젝트를
	- Cube
- 일정하게
	- new Vector3(1.0f,1.0f,1.0f)
- 회전시키고 싶다. 
	- transform.Rotate()

- - - 

# 키입력을 통한 오브젝트 컨트롤
유니티에서 오브젝트를 컨트롤하는 데 있어 입력처리를 어떻게 하는지 알아봅니다.  

시나리오 : 오브젝트 속도가 다르게 회전시키고 싶다.

**CubeScript에서 다음과 같이 수정**

{% highlight ruby %}

public class CubeScript : MonoBehaviour{
	public float rotationSpeed;

	void Update(){
		transform.Rotate(new Vector3(rotationSpeed,rotationSpeed,rotationSpeed));
	}
}
{% endhighlight %}

- Cube 오브젝트를 클릭
	- Play 클릭
	- 인스펙터창에서 Cube Script 컴포넌트의 Rotation Speed 값을 1로 변경
	- Cube 동작 확인
	- Play 끄기, Roation Speed 값 확인
- Rotation Speed 값을 5으로 변경
	- Play 클릭, Cube 동작 확인
	- Rotation Speed 속성에 마우스 오버 후 좌우 드래그 
	- Cube 동작 확인

시나리오 구현

- 오브젝트 속도
	-  변수를 만들고 public float rotationSpeed
- 가 다르게 회전시키고 싶다.
	- Rotate 함수에 변수를 지정 Rotate(rotationSpeed, ...)

**키입력을 통해 해당 Rotation Speed 값을 제어**

시나리오 : 스페이스 바를 누르는 동안만 회전한다.

{% highlight ruby %}
void Update () {
        if(Input.GetKey(KeyCode.Space))
            transform.Rotate(new Vector3(rotationSpeed, rotationSpeed, rotationSpeed));
    }
{% endhighlight %}


시나리오 구현

- 스페이스 바를
	- KeyCode.Space
- 누르는 동안만
	- if(Input.GetKey(...))  

