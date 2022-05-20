OpenCV를 이용한 실시간 FaceSwap 응용 프로그램 구축 및 실습
=======================================================


## 과제명 : C++을 이용한 프로젝트 계획서 제출
#### 팀명 : 4팀
   
      
      
      
### 팀원   
- 20201419/팀장/김민수/컴퓨터공학과/3학년/010-8779-****   
- 20201114/팀원/천효민/컴퓨터공학과/3학년/010-7766-****   
- 20201491/팀원/이은비/컴퓨터공학과/3학년/010-7583-****          
    
    
    
### 1. 과제요약
> C++ 기반으로 OpenCV와 dlib를 활용하여 실시간 FaceSwap을 구축해보고 실습하는 연구를 진행한다.        
> >알고리즘은 프레임에서 두 개의 면을 찾을 때까지 검색한다. 그런 다음 dlib 얼굴 랜드마크를 사용하여 얼굴 랜드마크를 추정한다. 얼굴 랜드마크는 프레임에서 얼굴을 "자르기"하고 한 얼굴을 다른 얼굴 위로 이동하는 데 사용되는 변환 행렬을 추정하는 데 사용된다.
>  >  >그러면 히스토그램 일치를 사용하여 얼굴의 색상을 보정하고 결국 얼굴의 가장자리에 페더를 적용하고 원본 프레임에서 혼합한다.
    
    
### 2. 과제 개요

1) 과제 배경
* 

2) 과제 필요성

3) 과제 선택 동기


### 3. 과제 목표 및 내용

1) 정량적/정성적 목표 (평가기준이 있으면 좋음)

![image](https://user-images.githubusercontent.com/93712785/169517967-92e350b1-0c2e-4992-a58c-176cd909911f.png)

<img src="https://user-images.githubusercontent.com/93712785/169517967-92e350b1-0c2e-4992-a58c-176cd909911f.png"  width="600" height="600"/>

* OTT시장이 매해마다 규모가 꾸준히 상승하고 있다. OTT시장은 새롭게 콘텐츠를 제작하도록 투자하기 보다는 과거의 시청률이 높았던 드라마나 흥행하였던 영화들을 가지고 와서 공개한다. 왜냐하면 새롭게 영화나 드라마를 제작하려면 시간이나 투자 비용이 과거 콘텐츠를 가져오는 것보다 훨씬 많이 나오고 만약 흥행하지 않았을 경우 투자 대비 이익을 보지 못 하여, OTT시장 측에서는 믿고 수익 보장이 될 수 있는 과거 영상들을 선호하는 경향이 있다. 이로 인해 넷플릭스라는 플랫폼에서 많은 이용자들이 2만원 내고도 볼 영상이 없다고 입 모아 말을 하고 있다. 이러한 문제점을 해결하기 위하여 과거의 콘텐츠보다 새롭게 콘텐츠를 제작할 경우 지금의 규모보다 훨씬 더 큰 규모를 예상해볼 수 있다. 영화나 드라마의 공급이 현재보다 더 많이 생산하려면 시간이나 금액을 줄여야 하는데 앞서 말했던 FaceSwap 기술을 이용하면 시간을 줄여 인건비도 많이 줄일 수 있으므로 해당 기술을 이용해 20년도에 OTT 규모보다 1.5배를 상승시키도록 할 것이다. 


2) 과제의 내용 (글, 그림, 표, 사진 등으로 이 내용을 보면

다른 사람이 동일한 작품을 만들 수 있도록 한다.)


### 4. 결과물

1) 예상 결과물

2) 기대효과 및 활용방안


5. 수행일정(도표)

번호/내용 / 추진일정/비고


6. 참고문헌 및 자료 (멀티미디어 학회 양식 참고)

[1]

[2] 
