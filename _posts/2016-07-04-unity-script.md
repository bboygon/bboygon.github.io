---
layout: post
title:  Unity Script
date:   2016-07-04 오후 10:31:30 
categories: Unity
tags: Unity
---

- - -

# 유니티 스크립트

- - -

# 변수 Variable
변수는 값을 저장할 수 있는 데이터로 변수를 선언하고 값을 대입하는 방식으로 구성됩니다.

{% highlight csharp %}

float sample; //선언
sample = 0.1f; //대입

//선언과 대입을 동시에
bool hasChecked = true;

{% endhighlight %}

또한, 변수는 외부로 노출되어 어디서든 접근이 가능하게 할지, 안할지를 결정합니다.

- 특정 변수를 외부(인스펙터 뷰)에 노출시켜 값을 제어하고 싶을 땐 public을 사용합니다.
- 외부에 노출시키지 않고 스크립트 내부, 함수 안에서만 제어하고 싶을 땐 private를 붙이거나 아무것도 붙이지 않습니다.

{% highlight csharp %}

// 접근제어정도 데이터타입 변수명
public float sample; //public 이므로 외부에서 접근가능
private float sample; //private 이므로 내부에서만 제어가능, 외부 노출 안됨.
float sample; 위와 동일

{% endhighlight %}

# 변수의 범위
변수를 사용할 때 선언하는 위치에 따라 동작방식이 달라집니다. 아래와 같이 함수내에서 변수를 선언한다면 지역 변수(Local Variable)라고 하며, 함수가 시작할 때 변수가 생성되고, 실행이 끝나면 변수도 없어집니다.

{% highlight csharp %}

void Update()
{
	float move = 0.1f;
	transform.Translate(move, 0f, 0f);
}

{% endhighlight %}


- - -


# 스크립트를 통한 오브젝트 컨트롤
유니티에서 지원하는 스크립트의 동작과정을 살펴보고 어떻게 만들어 적용하는지에 대해 알아봅니다.

시나리오 : 오브젝트를 일정하게 회전시키고 싶다.

- GameObject -> 3D Object -> Cube
- Project View
	- 우클릭 -> Create -> C# Script -> 'Cube Script' 로 명명
	- Rename 'Cube'
	- Cube Script 를 Cube 오브젝트에 끌어다 놓기
	- ![]({{site.url}}/downloads/unity_project_drag_cube.png ){:class="img-responsive" height="400px" width="800px"}

- CubeScript 파일 더블 클릭
- 열린 스크립트 파일 내부의 Update 함수를 수정

{% highlight csharp %}
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

{% highlight csharp %}

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

{% highlight csharp %}
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

- - -

# 간단한 오브젝트 이동을 구현

시나리오 : 키입력을 받아 전/후진, 회전을 하고 싶다.

{% highlight csharp %}
{	
	void Update()
	{
		float speed = Input.GetAxis("Vertical");
		float rotation = Input.GetAxis("Horizontal");
		
		speed = speed * Time.deltaTime;
		rotation = rotation * Time.deltaTime;

		transform.Translate(0, 0, speed);
		transform.Rotate(0, rotation, 0);
	}
}
{% endhighlight %}

![]({{site.url}}/downloads/unity-geyaxis.jpg ){:class="img-responsive" height="400px" width="800px"}

- Input.GetAxis("Horizontal")은 플레이어가 왼쪽/오른쪽 키를 눌렀는지를 알 수 있습니다.
- Input.GetAxis("Vertical")은 플레이어가 위/아래 키를 눌렀는지를 알 수 있습니다.
- 눌려진 방향에 해당하는 키값을 리턴하기 때문에 방향과 키값으로 오브젝트를 컨트롤 할 수 있습니다.


- - - 