---
layout: post
title:  Unity Build Setting 
date:   2016-07-08 오전 3:59:25  
categories: Unity
tags: Unity VR
---
- - -

# 빌드 환경 셋팅

- - -

### 빌드 할 씬을 등록
먼저 빌드를 하기 위해선 작업한 씬들을 등록해야 빌드가 가능합니다. 참고로 어플리케이션이 실행하면 최상단 씬에서 먼저 시작합니다. 씬을 전환시키는 스크립트 명령어를 통해 각 씬들의 전환이 가능합니다.

- File> Build Settings> Scene In Build> 안에 작업한 씬파일을 가져다 놓기
-  ![]({{site.url}}/downloads/unity-buildinscene.png ){:class="img-responsive" height="400px" width="800px"}

추가된 씬은 DELETE 키를 이용해 등록해제가 가능하고, 드래그를 통해 순서를 변경할 수 있습니다.
  

[예시] 스크립트가 실행시 씬파일명이 Scene1 을 불러온다면  

{% highlight csharp %}

using UnityEngine.SceneManagement;

public class BuildTest : MonoBehaviour{

	void Start()
	{
		//빌드세팅에 등록된 파일명으로 불러올 때
		SceneManager.LoadScene("Scene1");

		//빌드세팅에 등록된 인덱스 번호로 불러올 때
		SceneManager.LoadScene(0);

		//현재 불러온 씬을 다시 불러오기 할 떄(재시작 같은 효과)
 		SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex);

	}

	//외부 인터렉션 후 트리거 활성화 - 씬파일명으로
	public void LoadScene(string name)
	{
		SceneManager.LoadScene(name);
	}


	//외부 인터렉션 후 트리거 활성화 - 인덱스으로
	public void LoadScene(int index)
	{
		SceneManager.LoadScene(index);
	}

}

{% endhighlight %}


### 플랫폼 변경

빌드 환경에서 어떤 플랫폼으로 빌드할지를 결정해야 합니다.

원하는 플랫폼을 클릭 후 Switch Platform 버튼을 눌러 빌드 환경을 바꿀 수 있습니다. 현재 세팅되어 있는 플랫폼은 유니티 아이콘 표시로 확인 가능하며, 각 플랫폼 빌드 환경에 따라 빌드에 관한 옵션을 조정할 수 있습니다. 
 

![]({{site.url}}/downloads/unity-build-platform.png ){:class="img-responsive" height="400px" width="600px"}

- - -

# 안드로이드 빌드

플랫폼을 Android 로 변경하고 Player Settings 를 클릭합니다.

![]({{site.url}}/downloads/unity-build-playersetting.png ){:class="img-responsive" height="400px" width="400px"}

- - -

### 필수적인 변경 

플레이어 세팅
- Other Settings> Identification> Bundle Identifier 의 값의 변경이 필요.
- com.[상단의 Company Name].[상단의 Product Name] 으로 값을 맞춰야 합니다.

JDK 및 안드로이드 SDK 지정

![]({{site.url}}/downloads/unity-buildinscene.png ){:class="img-responsive" height="400px" width="600px"}

-  툴바> Edit> Preference> SDK 폴더 위치 지정
-  툴바> Edit> Preference> JDK 폴더 위치 지정
-  없다면 Download 버튼을 눌러 링크를 타고 각 파일을 받아 설치합니다.

- - -

### 그 외 모바일 관련 세팅

플레이어 세팅

- 가로/세로, 자동회전 여부를 설정
	- Resolution and Presentation> Default Orientation
- 앱 아이콘 변경
	- 상단의 Default Icon 에 이미지를 지정
- 안드로이드의 최소 API 설정(앱 실행에 필요한 최소한의 안드로이드 버전)
	- Other Settings> Identification> Minimum API Level
- 앱 파일에 쓰기 허용
	- Other Settings> Configuration> Write Access
		- Internal Only 내부
		- External (SD Card) SD카드 같은 외부 저장소
		
빌드 세팅

- 모바일 텍스쳐 압축 설정 File> Build Settings> Texture Compression
	- 아이폰 PVRCT
	- 안드로이드(Tegra) DXT
	- 안드로이드(Adreno) ATC
	- 안드로이드(공통) ETC1, ETC2
	- 압축된 RGB 텍스쳐 포맷 ASTC

- - -


### 출시 가능한 릴리즈 버전

릴리즈 버전은 플레이스토어에 등록가능한데 플레이스토어에 등록하려면 키스토어와 키 파일이 지정되어 있어야 합니다.

![]({{site.url}}/downloads/unity-build-publish-setting.png ){:class="img-responsive" height="400px" width="400px"}

키스토어 설정

- 새로운 키스토어를 생성 Create New KeyStore
- 키스토어를 파일로 저장 Brose KeyStore - 이름 설정 및 저장
- 비밀번호 설정 KeyStore password / Confirm password

키 설정

- 키를 새로 만를기 Key> Alias> Create a new Key
- ![]({{site.url}}/downloads/unity-build-createKey.png ){:class="img-responsive" height="400px" width="400px"}
- 이름 입력 Alias
- 비밀번호 설정 Password/confirm
- 해당 키의 유효기간 설정 50(50년을 의미, 거의 무제한)
- 키 생성 Create Key
- 키 선택 Alias 에 생성된 키를 선택

