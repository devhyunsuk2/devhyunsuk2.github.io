---
layout: post
title: "쉐이더 그래프 만지기_01_오브젝트 디졸브 효과"
date: 2019-05-27
excerpt: "유니티 쉐이더 그래프"
tags: [Unity, Shader]
comments: true
---
# 쉐이더그래프 - 오브젝트 디졸브 효과
#### 쉐이더그래프 입문!
>쉐이더를 시작해보려 여러 방법으로 이 분야를 시도했었다. 첫번째는 서적을 이용하여서 두번째는 강의로. 그렇지만 쉐이더 코드를 짜는일은 체감이 어려워 흥미를 잃었었다. 그러다가 유니티에서 지원하는 쉐이더그래프에대한 소개를 받고 유튜브 강의를 통해 시작해본순간 예전에 프로젝션맵핑 수업에서 사용해본 쿼즈컴포저가 생각나면서 흥미가 생겼다. 무엇보다도 결과를 바로바로 확인해 볼 수 있는것이 매력적인것같다. 쉐이더공부를 처음 시작할때 가장 먼저 해보고싶었던 효과인 Dissolve를 시작으로 틈틈히 그리고 차근히 쉐이더를 이해보고자 한다.

## INDEX
* 프로젝트 생성하기
* 3D 오브젝트 가져오기
* 쉐이더 그래프 만들기
* Dissolve 쉐이더 만들기
* 결과

---

## 프로젝트 생성하기

<figure>
    <img src="https://i.imgur.com/Q7EAGdU.jpg">
</figure>

쉐이더그래프를 사용하기 위해서는 Template을 기존(3D or 2D)과는 다른 세팅으로 프로젝트를 생성해야한다.
또한 유니티 버전을 설치할 때 18버전중에서도 18.3 이상부터가 가장 이상적인 버전이므로 최신버전을 다운받는것이 좋다.
프로젝트 생성시에 Template을 Lightweight RP로 설정한뒤 프로젝트를 생성하면 된다.


## 3D 오브젝트 가져오기
3D 모델링을 직접하면 좋겠으나, Asset Store 또는 https://free3d.com/ko/3d-models/fbx 에서 무료로 오브젝트를 사용하는것도 방법이다. fbx파일로 다운받아 유니티 프로젝트로 불러오면 된다.


## 쉐이더 그래프 만들기
쉐이더 그래프는 Project에서 오른쪽 클릭 -> Create -> Shader -> PBR Graph를 눌러 생성한후 생성된 파일을 더블클릭하여
쉐이더 그래프 창을 띄우는것으로 시작한다.

<figure>
    <img src="https://i.imgur.com/HzaPjDj.png">
</figure>

왼쪽상단의 Save Asset을 통해 저장이 가능하며 Show In Project을 통해 파일의 위치를 유니티 내에서 확인할 수 있다.
노드를 만드는 방식은 Space를 누르거나 빈 곳에서 오른쪽 클릭 -> Create Node 를 통해 만들 수 있다.
생성된 노드를 오른쪽 클릭하여 Covert to Property를 선택하면 유니티 에디터에서 수치를 조정하며 적용된 모습을 확인하고 변경하기 용이해 진다.

## Dissolve 쉐이더 만들기

<figure>
    <img src="https://i.imgur.com/EnKW1no.png">
</figure>

Dissolve는 AlphaClipThrehold를 조금 이해하고있는것이 좋다. PBR Master의 AlphaClipThrehold의 방식은 0.7을 기준으로
텍스처의 데이터가 0.7보다 작으면 0, 즉 Invisible으로 표현하고 작으면 1, 즉 Visible로 표현한다.
이를 이용하여 Noise 노드를 통해 Dissolve 효과를 제작할 수 있다.

또한 Step 노드에 Noise와 Time이 적용된 Remap 애니메이션을 넣고 PBR Master의 Emission노드로 연결하여 컬러감을 줄 수 있다. Post Processing 까지 사용하면 제법 그럴싸한 효과를 완성시킬 수 있다.

## 결과

<img src="https://i.imgur.com/YyRZGcX.gifv">
<img src="https://i.imgur.com/Ojmsfvs.gifv">
<img src="https://i.imgur.com/d4omPzu.gifv">

수치를 조정하여 여러효과를 낼 수 있다.
아티스트라면 Parameter를 조정해가면서 컨셉에 맞는 비주얼 솔루션을 쉽게 도출해낼수있을것같다.