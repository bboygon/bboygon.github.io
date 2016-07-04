---
layout: post
title:  Unity Scene View
date:   2016-07-05 오전 2:07:01  
categories: Unity
tags: Unity
---

- - -

# 씬 뷰에서의 네비게이션


씬 뷰(작업창)에서 실제 카메라가 아닌 작업을 위한 시야를 움직이고 싶다면 마우스를 우클릭 한 상태로 WASD를 이용해 이동이 가능합니다.

- 마우스 우클릭만 한다면 현재 작업 화면의 Y축을 기준으로 회전
- 마우스 우클릭을 유지한 상태에서
	- W 는 전진
	- S 는 후진
	- A 는 왼쪽 횡 이동
	- D 는 오른쪽 횡 이
- 훨 버튼을 누른 상태의 움직임은 위 아래 종 이동
- Shift 키를 누르고 있다면 네비게이션 가속


계층 뷰의 게임 오브젝트를 더블 클릭하면 씬 뷰에서 해당 오브젝트로 포커싱 됩니다.

# 게임 오브젝트의 네비게이션

계층 뷰에 등록되는 모든 게임 오브젝트는 Transform 컴포넌트를 가지고 있습니다. Transform  컴포넌트는 위치 좌표, 회전값, 스케일 값을 가지고 있기 때문에 주어진 원할한 이동이 가능합니다.

![](http://docs.unity3d.com/kr/current/uploads/Main/UI-ViewTool.png ){:class="img-responsive"}


툴바를 직접 클릭하여 Translate(좌표 이동), Rotate(회전), Scale(크기)를 제어 할 수 있고, 단축키를 이용할 수도 있습니다.

![](http://docs.unity3d.com/kr/current/uploads/Main/TransformGizmo35.png ){:class="img-responsive"}

# 기즈모

기즈모는 좌표 축을 보여주는 것으로 각 축의 정보를 나타냅니다. 씬 뷰의 오른쪽 상단에 큰 기즈모가 있는데 이것은 씬 뷰의 축을 나타냅니다. 각각의 축을 클릭하면 Front, Back, Left, Right 등등의 축 회전을 한뒤 화면에 나타납니다.

![](http://docs.unity3d.com/kr/current/uploads/Main/Editor-SceneGizmo.png ){:class="img-responsive"}

- 레드는 X축
- 블루는 Z축
- 그린은 Y축 

마찬가지로 게임 오브젝트를 클릭하면 해당 기즈모가 나타나며 이를 통해 위치를 변경하거나, 회전시키거나, 크기를 제어할 수 있습니다.

- - -

# 기즈모의 토클 

![](http://docs.unity3d.com/kr/current/uploads/Main/HandlePositionButtons.png ){:class="img-responsive"}

위치
- Center 는 오브젝트의 렌더링 바운드의 중심에 기즈모를 배치
- Pivot 은 메쉬의 실제 피벗 정점에 기즈모를 배치

회전
- Local은 오브젝트의 회전 축의 중심으로 기즈모를 배치 
- Global은 해당 오브젝트의 회전과 관계없이 월드 공간을 중심으로 기즈모를 배치




