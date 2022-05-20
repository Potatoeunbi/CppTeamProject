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

1) 과제 배경
* 

2) 과제 필요성

3) 과제 선택 동기


## 3. 과제 목표 및 내용

### 1) 정량적/정성적 목표 (평가기준이 있으면 좋음)
<img src="https://user-images.githubusercontent.com/93712785/169517967-92e350b1-0c2e-4992-a58c-176cd909911f.png"  width="600" height="600"/>

* OTT시장이 매해마다 규모가 꾸준히 상승하고 있다. OTT시장은 새롭게 콘텐츠를 제작하도록 투자하기 보다는 과거의 시청률이 높았던 드라마나 흥행하였던 영화들을 가지고 와서 공개한다. 왜냐하면 새롭게 영화나 드라마를 제작하려면 시간이나 투자 비용이 과거 콘텐츠를 가져오는 것보다 훨씬 많이 나오고 만약 흥행하지 않았을 경우 투자 대비 이익을 보지 못 하여, OTT시장 측에서는 믿고 수익 보장이 될 수 있는 과거 영상들을 선호하는 경향이 있다. 이로 인해 넷플릭스라는 플랫폼에서 많은 이용자들이 2만원 내고도 볼 영상이 없다고 입 모아 말을 하고 있다. 이러한 문제점을 해결하기 위하여 과거의 콘텐츠보다 새롭게 콘텐츠를 제작할 경우 지금의 규모보다 훨씬 더 큰 규모를 예상해볼 수 있다. 영화나 드라마의 공급이 현재보다 더 많이 생산하려면 시간이나 금액을 줄여야 하는데 앞서 말했던 FaceSwap 기술을 이용하면 시간을 줄여 인건비도 많이 줄일 수 있으므로 해당 기술을 이용해 20년도에 OTT 규모보다 1.5배를 상승시키도록 할 것이다. 


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

-> 그 후에 FaceSwap이 작동!


## 4. 결과물

1) 예상 결과물

2) 기대효과 및 활용방안


5. 수행일정(도표)

번호/내용 / 추진일정/비고


6. 참고문헌 및 자료 (멀티미디어 학회 양식 참고)

[1] Be into OTT bring the TV age to an end(2016). https://bravo.etoday.co.kr/view/atc_view.php?varAtcId=4899 (accessed May 20, 2022)   
[2] An employee's labor contract that hasn't taken a step back "KBS first"(2021). http://www.mediatoday.co.kr/news/articleView.html?idxno=213153 (accessed May 20, 2022)
[3] http://mbiz.heraldcorp.com/view.php?ud=20220506000561
 
