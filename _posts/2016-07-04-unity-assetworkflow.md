---
layout: post
title:  Unity WorkFlow
date:   2016-07-05 오전 1:18:39 
categories: Unity
tags: Unity
---

- - -

# 에셋 워크 플로우

유니티에서 외부 데이터를 에셋으로 변환하거나 에셋을 생성하는 방법들을 소개합니다.
외부 데이터는 Project/Asset/ 폴더안에 직접 추가하거나 그림과 같이 파일을 프로젝트 뷰에 드래그 앤 드롭으로 추가가 가능합니다.

![](http://docs.unity3d.com/kr/current/uploads/Main/AssetWorkflowImportingFiles.png ){:class="img-responsive"}

- - -

# 임포트 셋팅

다양한 타입의 애셋들을 유니티에서 지원하는데, 프로젝트 뷰에서 애셋을 클릭하면 인스펙터 뷰에서 해당 애셋의 임포트 속성을 지정할 수 있습니다. 

![](http://docs.unity3d.com/kr/current/uploads/Main/AssetWorkflowImportSettings.png ){:class="img-responsive"}

그림과 같이 텍스쳐의 경우 텍스쳐 타입과 그와 관련된 속성들을 볼 수 있고, 오디오 애셋의 경우 오디오 속성과 관련된 파라미터들을 볼 수 있습니다.

![](http://docs.unity3d.com/kr/current/uploads/Main/ImportSettingsAudioExample.png ){:class="img-responsive"} 

이러한 애셋의 임포트 속성을 수정하여 해당 애셋이 게임 프로젝트에 어떻게 적용시킬지를 결정하게 됩니다.

- - -
 
# 에셋 스토를 통한 에셋 임포트

유니티의 특징 중 하나인 에셋 스토어는 스크립트 코드에서 부터 3D 모델 데이터, 완성된 프로젝트 등등, 다양하게 사용할 수 있는 애셋들을 사고 팔수 있는 스토어입니다. 무료와 유료로 구분되며 자신에게 필요한 기능이 있는 애셋을 구매할 수 있으며, 또한 자신이 직접 구현한 애셋을 스토어에서 팔 수 있습니다.

![](http://docs.unity3d.com/kr/current/uploads/Main/AssetStore-floating.png ){:class="img-responsive"}

프로젝트 내에서 메뉴탭의 Windows - Asset Store 로 접속하거나 웹페이지를 통해 접속할 수 있습니다.

- - -