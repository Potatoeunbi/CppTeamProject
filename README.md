OpenCV를 이용한 실시간 FaceSwap 응용 프로그램 구축 및 실습
=======================================================


## 과제명 : C++을 이용한 프로젝트 계획서 제출
### 팀명 : 4팀
   
      
      
      
## 팀원   
- 20201419/팀장/김민수/컴퓨터공학과/3학년/010-8779-****   
- 20201114/팀원/천효민/컴퓨터공학과/3학년/010-7766-****   
- 20201491/팀원/이은비/컴퓨터공학과/3학년/010-7583-****          
    
    
    
## 1. 과제요약
> C++ 기반으로 OpenCV와 dlib를 활용하여 실시간 FaceSwap을 구축해보고 실습하는 연구를 진행한다.        
> >알고리즘은 프레임에서 두 개의 면을 찾을 때까지 검색한다. 그런 다음 dlib 얼굴 랜드마크를 사용하여 얼굴 랜드마크를 추정한다. 얼굴 랜드마크는 프레임에서 얼굴을 "자르기"하고 한 얼굴을 다른 얼굴 위로 이동하는 데 사용되는 변환 행렬을 추정하는 데 사용된다.
>  >  >그러면 히스토그램 일치를 사용하여 얼굴의 색상을 보정하고 결국 얼굴의 가장자리에 페더를 적용하고 원본 프레임에서 혼합한다.
    
    
## 2. 과제 개요

### 1) 과제 배경
* 최근 OTT 시장이 급속도로 성장하면서 미디어 콘텐츠의 수요가 늘어나고 있는 추세다. 그러나 늘어난 수요에 비해 콘텐츠 제작에 주어진 기간은 길지 않다. 예를 들어 우리나라 드라마 평균 제작기간은 약 1년 정도이다. 혹여나 주연배우들이 부상이라도 당하면 더 긴 시간이 소요가 된다. 이러하게 너무 길게 소요되는 시간을 축소하기 위하여 FaceSwap의 기술을 이용하여 배우가 부상을 당하게 되었을 때 다른 보조 배우를 연기하게 하고 그 기술을 사용하면 시간 절약에 큰 효과를 기대할 수 있다.

### 2) 과제 필요성 & 과제 선택 동기   
* 최근 전 세계적으로 정치인 및 연예인 합성 동영상에 사용되는 인공지능 기반의 FaceSwap은 점점 더 큰 사회적 문제를 야기시킨다. 특히, FaceSwap이 단순 재미, 유희 및 풍자를 넘어서 가짜 뉴스를 만들어내며, 더 큰 범주로서 언론을 조작한다. 더불어 불법 음란물을 제작하고 유포하면서 이로 인해 논란과 정신적 피해를 받는 사람이 늘어나고 있다. 이와 같이 딥페이크의 위험이 부각되고 기술의 오남용을 막기 위해서 기술의 근본적인 과정 연구의 필요성을 느끼게 되었다. 이 과제에서 OpenCV 및 dlib를 활용하여 실제 FaceSwap이 어떻게 이루어지는지에 관해 연구를 진행한다. 불법적인 활용을 제재하기 위한 기술에 추가 기능에 관한 연구의 필요성을 생각하게 되었다.   
* 최근 꾸준히 성장해왔던 OTT 시장이 코로나19의 급증함에 따라 빠른 속도로 규모가 발전하고 있는 추세이다. 그러나 늘어난 수요에 비해 콘텐츠 제작에 주어진 기간은 길지 않다. 이로 인해 많은 스태프들이 근로기준법에 명세된 주 52시간을 위반한 초과 근무를 한다. 이러한 발생 가능한 위험 문제와 공급에 주어진 촉박한 시간 대비 효율적으로 제작하기 위해 FaceSwap 기술을 활용하여 생산하는 사례가 늘어나고 있다. 이 기술을 사용하여 시간 절약 및 경제적 이익을 기대할 수 있다. 
* 콘텐츠 제작에 필요한 기술의 과정에 대해 학습의 필요하다. 본 연구에서 위와 같은 배경 및 필요성을 바탕으로 이 주제를 선택하게 되었다.


## 3. 과제 목표 및 내용

### 1) 정량적/정성적 목표

#### ①정량적 목표
<img src="https://user-images.githubusercontent.com/93712785/169517967-92e350b1-0c2e-4992-a58c-176cd909911f.png"  width="600" height="600"/>

* OTT시장이 매해마다 규모가 꾸준히 상승하고 있다. OTT시장은 새롭게 콘텐츠를 제작하도록 투자하기 보다는 과거의 시청률이 높았던 드라마나 흥행하였던 영화들을 가지고 와서 공개한다. 왜냐하면 새롭게 영화나 드라마를 제작하려면 시간이나 투자 비용이 과거 콘텐츠를 가져오는 것보다 훨씬 많이 나오고 만약 흥행하지 않았을 경우 투자 대비 이익을 보지 못 하여, OTT시장 측에서는 믿고 수익 보장이 될 수 있는 과거 영상들을 선호하는 경향이 있다. 이로 인해 넷플릭스라는 플랫폼에서 많은 이용자들이 2만원 내고도 볼 영상이 없다고 입 모아 말을 하고 있다. 이러한 문제점을 해결하기 위하여 과거의 콘텐츠보다 새롭게 콘텐츠를 제작할 경우 지금의 규모보다 훨씬 더 큰 규모를 예상해볼 수 있다. 영화나 드라마의 공급이 현재보다 더 많이 생산하려면 시간이나 금액을 줄여야 하는데 앞서 말했던 FaceSwap 기술을 이용하면 시간을 줄여 인건비도 많이 줄일 수 있으므로 해당 기술을 이용해 20년도에 OTT 규모보다 1.5배를 상승시키도록 할 것이다. 

#### ②정성적 목표
*  본 연구를 통해 C++를 활용한 OpenCV를 다룰 수 있다.
      - 구축할 수 있는가?
      - OpenCV가 무엇인지 아는가?
*  사진이 아닌 영상을 FaceSwap을 구현할 수 있다.
      - 실제로 구현할 수 있는가?
* FaceSwap이 됐을 때, 바뀐 얼굴에 맞게 얼굴의 색상을 보정할 수 있다.    
      - 이질감이 없는가?

### 2) 과제의 내용
   
      
* OpenCV 및 dlib 다운로드

* OpenCV 설정
   - 다운로드한 OpenCV 실행 파일을 실행하고 OpenCV 라이브러리를 추출할 디렉토리를 선택(예: D:\opencv)

* dlib 설정
   - 다운로드한 zip 파일을 디렉토리에 추출(예: D:\dlib).

* Visual Studio 2015 이상 버전 다운로드 및 설치

* Visual Studio 실행

* 비어 있는 새 프로젝트를 만들고 이름을 지정(예: MyProject).

* "debug" solution 구성이 선택되어 있는지 확인

* Visual Studio에서 Solution Exlplorer 창을 연다.

* MyProject를 마우스 오른쪽 버튼으로 클릭하고 속성을 선택

* 왼쪽 상단 모서리에 있는 "구성 관리자..." 버튼을 클릭

* Debug 구성 설정

   - active solution 플랫폼에서 x64 선택
   - 구성 관리자 창 닫기
   - 속성 창 왼쪽 상단에서 선택한 구성이 "debug"이고 플랫폼이 "x64"인지 확인
   - 왼쪽 패널에서 C/C++를 선택
   - [디렉토리 추가] 필드에 두 개의 디렉토리를 추가
      + "D:\opencv\opencv\build\include"
      + "D:\dlib\dlib-19.2"
      + dlib 버전이 다른 경우 경로가 다를 수 있음
   - 왼쪽 패널에서 링커 > 일반을 선택
   - 추가 라이브러리 디렉토리에서 "D:\opencv\opencv\build\x64\vc14\lib"를 추가
      + 아키텍처 또는 VS 버전이 다른 경우 경로가 다를 수 있음
   - 왼쪽 패널에서 링커 > 입력을 선택
   - 추가 종속성에서 "opencv_world320d.lib"를 추가
   - 적용 클릭
 
* 왼쪽 상단의 구성을 "Release"로 변경하고 반복

* 릴리스 구성 설정
   - 왼쪽 패널에서 C/C++를 선택
   - [디렉토리 추가] 필드에 두 개의 디렉토리를 추가
      + "D:\opencv\opencv\build\include"
      + "D:\dlib\dlib-19.2"
      + dlib 버전이 다른 경우 경로가 다를 수 있음
   - 왼쪽 패널에서 링커> 일반을 선택
   - 추가 라이브러리 디렉토리에서 "D:\opencv\opencv\build\x64\vc14\lib"를 추가
      + 아키텍처 또는 VS 버전이 다른 경우 경로가 다를 수 있음
   - 왼쪽 패널에서 링커 > 입력을 선택
   - 추가 Dependencies에서 "opencv_world320.lib"를 추가

* 속성 창 닫기

* Solution Explorer에서 소스 파일을 마우스 오른쪽 버튼으로 클릭

* "기존 항목 추가..."를 선택하고 이 프로젝트에서 .cpp 파일을 추가

* Solution Explorer에서 헤더 파일을 마우스 오른쪽 버튼으로 클릭

* "기존 항목 추가..."를 선택하고 이 프로젝트의 .h 파일을 추가

* OpenCV sources/data/haarcascades 디렉토리에서 프로젝트 디렉토리로 haarcascade_frontalface_default.xml를 복사

* http://sourceforge.net/projects/dclib/files/dlib/v18.10/shape_predictor_68_face_landmarks.dat.bz2 에서 shape_predictor_68_face_landmarks.dat를 다운로드 하고 프로젝트 디렉토리에 배치

#### -> 그 후에 FaceSwap이 작동!


## 4. 결과물

### 1) 예상 결과물

* Before   

![image](https://user-images.githubusercontent.com/93712785/169538395-60e05456-bdec-45c9-9288-88dff0acbe6e.png)

* After   

![image](https://user-images.githubusercontent.com/93712785/169538430-b2633456-67d7-4bea-a2cb-8d0e520d98fa.png)


### 2) 기대효과 및 활용방안
* 기대효과
   - 본 연구를 통해서 시간 절약과 경제적 이익에 큰 효과를 기대 할 수 있고 실제 FaceSwap이 어떻게 이루어지는지에 대한 지식을 학습 할 수 있다. 게다가 불법적으로 악용하는 것을 방지하는 기능을 제시할 수 있다.
* 활용 방안
   - 의료분야 이미지 패턴 매칭기능을 활용하여 질병 진단용 인공지능을 개발했다. 뤼벡대 연구진은 적대관계생성긴경망(GAN)을 이용하여 원본 영상과 진위여부를 구별할 수 없는 정확도의 FaceSwap 의료영상을 만들어 냈다. FaceSwap 영상은 인공지능이 질병을 학습하고 정확히 진달할 수 있도록 딥러닝 하는데 사용된다. 환자의 사생활 침해에 대한 우려와, 의료용 3D 이미지 합성에 필요한 비용 때문에 의료영상을 분석할 데이터가 충분치 않았는데, FaceSwap 기술로 이를 해결한 것이다. 
   - 더빙을 진행하는데 있어 각 나라마다 언어가 달라 진행자의 입 모양이 다른 상황이 발생합니다. 이 기술을 활용하여 그 문제를 방지할 수 있습니다.
   - 할리우드를 비롯한 영상 제작 업계에서는 딥페이크 기술로 특수효과를 만들어 내고 있다. 특히 과거를 재현하거나 더 이상 실존하지 인물을 그리고자 할 때 유용하게 활용되고 있다. 2016년에 개봉한 영화 <Rogue One>4 에는 1977년 작 <Star Wars: A New Hope>에 출현한 배우가 당시의 모습 그대로 등장했다. <Rogue One> 제작진은 배우와 외형적으로 유사한 대역 배우를 섭외한 후, 모션 캡처 기법과 딥페이크 기술을 활용하여 대역 배우의 얼굴에 과거 배우의 얼굴을 합성하는 방식으로 영화를 촬영했다. Netflix도 딥페이크 기술을 활용해 주연 배우의 현재와 과거 모습을 동시에 재현해 낸 <The Irishman>의 출시를 예고했다. 
* FaceSwap 기술은 영상뿐 아니라, 오디오, 사진, 문서 등에서 다방면으로 활용이 가능하다.
   
## 5. 수행일정

|번호|내용|추진일정|비고|
|--|----------|------|---|
|1|주제선정|2022-05-18||
|2|자료 조사|2022-05-20| |
|3|계획서 작성|2022-05-22| |
|4|구현|2022-05-XX| |
|5|테스트|2022-05-XX| |
|6|논문 양식의 보고서 제작|2022-05-XX| |
|7|발표자료 PPT 제작|2022-05-XX| |
|8|리플렛 제작|2022-05-XX| |
|9|동영상 제작|2022-05-XX| |
|10|발표|2022-06-XX| |



## 6. 참고문헌 및 자료

[1] Be into OTT bring the TV age to an end(2016). https://bravo.etoday.co.kr/view/atc_view.php?varAtcId=4899 (accessed May 19, 2022)   
[2] An employee's labor contract that hasn't taken a step back "KBS first"(2021). http://www.mediatoday.co.kr/news/articleView.html?idxno=213153 (accessed May 19, 2022)   
[3] "The fare has gone up, but there's nothing to watch." Annoying Netflix users, "Oh My!"(2022). http://mbiz.heraldcorp.com/view.php?ud=20220506000561 (accessed May 20, 2022)      
[4] Korea Creative Content Agency, "딥페이크 기술의 빛과 그림자", https://www.kca.kr/fileDownload.do?action=fileDown&mode=&boardId=TRENDS&seq=5310642&fileSn=1 (accessed May 20, 2022) 
 
