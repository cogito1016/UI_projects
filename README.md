# UI_projects

안쓰는 버릇하니까 잊어버려서 만든 HTML CSS 레포

- SCSS
- Grid
- FlexBox
- etc...

## SCSS

- CSS로 작업하는것의 표준이 됨
- Sassy CSS

### block은 box이다.

따라서 width와 height가 존재한다.

### inline은 box가 아니라 element이다.

element는 유동적이라서 높아와 너비가없음.  
예를들어 text는 inline이다.

Div요소는 기본적으로 block 요소이다.  
따라써 Div를 세개 연속으로 생성하게되면 수직배치가 되게 된다.  
그러나 display속성을 inline-block으로 수정하게되면,  
수평배치가 될 수 있다.

block디스플레이의 특성으로 width와 height가 있지만,  
inline디스플레이의 특성으로 하나의 요소처럼 취급된다.

#### div를 수평배치한 후 수평에 알맞은 너비로 정렬하기 위해

1. 각 요소마다 :nth-child(n)을 통해 margin을 준다면 정렬이 가능하다.

근데 구리다.  
하나하나 계산하고 하는것도 구리고, 안멋있음.  
그리고 css코드를 다시보는것도 진짜싫을것같다.

그리고 무엇보다 px을 주며 맞춘 디자인은, 윈도우 크기가 변화되었을때  
디자인이 파괴된다.

2. Flexbox를 사용한다.  
   Flexbox를 사용하면 요소 별 margin의 px을 지정하여 할 필요 없이 정렬이 가능하다.

### FlexBox

Flexbox를 사용하기 위해서는 FlexCointainer가 필요하다.  
Flexbox를 적용할 요소들을 담는 요소에 display='flex'로 설정가능하다.

그렇다면 inline-block을 해줄때와 달리,  
수평정렬된 각 요소마다 생기는 사이간격도 없이 수평간격이 만들어진다.

- Flex-children정렬방식  
  flex-direction : row || coluumn  
  기본값은 row(수평)

- Flex-children배치

1. justify-content : center || space-between...  
   main-axis을 기준으로 flex-children의 위치를 변경한다.

2. align-item : center :: space-between...  
   cross-axis을 기준으로 flex-children의 위치를 변경한다.

- 메인축(Main-axis)
  flex-direction의 기본값인 row일때는, 메인축이 horizen  
  column일때는, 메인축이 vertical.

- 크로스축(Cross-axis)
  flex-direction의 기본값인 row일때는, 크로스축이 vertical  
  column일때는, 크로스축이 horizen.

- align-self  
  align-item과 비슷한일을함, 즉 cross-axis를 다룬다.  
  그러나 하나의 요소만을 다룰때 사용한다.

부연설명  
flexContainer에는 여러 flexitem 자식요소들이 존재하기마련이다.  
align-item을 통해 cross-axis를 전부 배치할 수 있지만,  
개별적인 요소마다 개별적인 cross-axis를 설정해줄 필요가 있다.  
그 때 사용된다.

- order  
  html을 바꿀 수 없을 때 사용한다.  
  기본적으로 box의 order는 0이다.  
  2번박스의 order를 1로바꾸면 맨 뒤로가게될 것.  
  즉, 숫자가 작을수록 순서가 앞이다.

- flex-wrap(default:nowrap)
  FlexBox는 Flex-direction에 맞게 요소들을 배치하는것이 목적이다.  
  따라서 flex-direction row일 시, 개별요소의 width는 신경쓰지 않는다.  
  같은 라인에 배치할 뿐.

그러나 flex-wrap을 wrap으로 설정하게된다면,  
flex요소들의 개별 width를 유지하라고 하는것과 같다.  
따라서 요소들의 width가 뭉게지지않고 여러 층으로 나눠지게된다.

- flex-flow  
  flex-direciton 과 flex-wrap은 같이 자주쓰인다.  
  따라서 이 둘을 공백문자로 구분하여 한번에 처리하는 속성이다.  
  ex) flex-flow : row wrap

- reverse()  
  reverse는 flex-direction의 값들 중 하나이다.  
  row-reverse || column-reverse가 있으며, 요소의 순서를 반전시킨다.

- align-content(default:space-around)  
  justify-content와 비슷하지만 line에 대한 것 이다.  
  어떤 line 이냐면, flex-wrap을 wrap으로 설정하였을때 생기는 층 별 라인이다.(⭐️cross-axis line⭐️)  
  flex-start로 설정하면 라인이 사라진다.

- flex-shrink(default:1)  
  element의 행동을 정의한다.  
  flexbox가 쥐어짜질때말이다.  
  무슨말이냐하면 flex가 nowrap일때는 width가 뭉게질 수 있는데,  
  뭉게질 때 어떤 요소가 더 많이 찌그러지는지(nth-child())를 정의.  
  2로 설정시에는 다른 박스들보다 더 찌그러진다.

- flex-grow(default:0)  
  flex-shrink와 같지만 반대로 작용한다.  
  여분의 공간(빈 공간)만큼 가져간다.

- flex-basis  
  width와 비슷하다.(대체가능하다)  
  그러나 element에게 처음 크기를 주는 것.  
  찌그러지거나 늘어나기전에 말이다.  
  main-axis방향의 요소의 크기를 의미한다.

### Grid

왜 필요한가?  
flex-box에서 그리드(격자무늬)를만들기 어렵다.  
1 2 3  
4 5  
display : flex

- grid-template-columns : 100px 100px 100px;
- grid-template-rows : 50px 50px 50px;
- gap : 10px;

gap(inclues row-gap, column-gap)

- gird-column-start|end  
  이 때의 column은 column의 의미가 아니라 Line이라고 보면 됨.  
  grid-column-start : 1  
  grid-column-end : 2  
  위의 의미는 1번라인에서 시작해서 2번라인에서 끝난다.  
  grid child(cell)의 영역을 어디까지 사용할지 지정해주는 역할을 함.

- grid-column(-grid-row)  
  grid-column-start|end 를 한번에 쓸 수 있는 방법  
  grid-column : 1 / 2;

- grid-column의 -1  
  -1의 의미는 끝 이라는 뜻  
  grid-column : 1 / -1 #1부터 끝까지

더 정확하게는...  
역순으로 라인을 표시하는 역할이다.  
라인을 역순으로 셀때, -1은 역순의 첫 번째 이므로 마지막의 의미이다.

- span(gird-row|template에 사용)  
  몇개의 셀을 가지게할 건지 정하는 속성  
  grid-row : span 2

- Line에 이름붙이기  
  grid-template-column : [first-line] 100px [second-line] 200px ...  
  grid-column : first-line / third-line

이걸 써 ??  
==> 별로안쓰는듯..?

- grid-template-areas
  한번에 템플릿을 잡을 때 유용  
  grid-area와 함께 쓰임

- grid-template  
  grid-template-areas와 비슷.  
  그러나 row의 크기와 column의 크기를 한번에 지정할 수 있다.  
  또한, line-naming도 할 수 있다. (생략가능)  
  "footer footer footer footer" 1fr / 1fr 1fr 1fr 1fr;
  grid-template-areas + grid-template-row|colums

- fr  
  fraction의 준말  
  px처럼 단위이다.  
  grid container의 width에서 사용가능한 범위를 뜻한다.  
  그리고 비율을 의미한다.  
  100width에 row가 1fr 1fr 1fr 1fr일 때, 각각 동일한 비율이지만  
  100width에 row가 4fr 1fr 1fr 1fr일 때, 첫 번째 row는 다른 것들보다 4배 더 크게 비율이 잡힌다.

- justify-items(default:stretch)
  row해당  
  grid container는 grid children이 있고 이 자식들을 stretch하여 채워놓는 형태로 존재한다.  
  정해진 grid row와 column의 크기는 존재하나,  
  grid child의 크기에 해당되는 말이다.  
  ex) start시 grid child의 내부요소의 크기에 맞춘 후 맨 앞 위치.  
  end시 grid child의 내부요소의 크기에 맞춘 후 맨 뒤 위치.

- align-items(default:stretch)  
  column해당  
  위와 동일

- place-items
  justify-items & align-items 를 합친 속성  
  place-items : y x;  
  place-items가 가장 short-cut

- justify-content
  grid자체를 위치시키는 속성  
  grid의 row를 위치시키는 속성

- align-content
  grid자체를 위치시키는 속성  
  grid의 column을 위치키시는 속성

- place-content
  = place-items과 달리 모든 요소들에 적용 됨

- align-self
  개별 요소에 대한 align-items 속성이다.

- jusitfy_self
  개별 요소에 대한 justify-items 속성이다.

- place-self
  align-self와 justify-self의 short-cut  
  place-self : start end

- 데이터에 비해 row가 더 적어 gird-template-row에 적용이 안되는 경우.

1. 그럴때마다 grid-template-row : repeat(4, 100px)에 숫자를 증가시켜준다?  
   => Bad Solution.
2. 우리가 지정하지 않은 요소들의 크기를 '자동'으로 지정해주는 설정을 잡아준다.  
   => Good Solution 🥰  
   => 이럴 때 사용하는 것이 grid-auto-rows  
   따라서, grid-auto-rows 를 사용하자.

- grid-auto-flow(default:row)  
  요소가 늘어나는 flow를 어떻게 지정할 것 인가?  
  column으로 지정 시 왼쪽위->왼쪽아래 방향으로 채워진다.  
  (따라서 row는 고정, column이 증가한다)  
  (그리고 이 때, grid-auto-column이 사용될 수 있다 !)  
  디폴트인 row인 경우 왼쪽위->오른쪽위 방향으로 채워진다.  
  (column은 고정, row가 증가한다)

- minmax()
  ex) repeat(10, minmax(100px, 1fr));  
  윈도우크기를 줄이면 요소의 크기가 작아지게되는데,  
  요소의 최소값과 최대값을 설정하는것이 minmax이다.

- autofill
  row에 요소를 최대한 많이 채운다.  
  컬럼이 비어져있더라도 말이다.

- autofit
  딱 맞춘다.  
  요소들을 stretch해서 row에 Fit하게 맞춘다.

Auto Fill 과 Auto Fit은 반응형의 기본이라고한다.  
아직은 뭔말인지 잘 모르겠지만.. 알아만두자.

- mincontent
  컨텐츠가 작을 수 있는 만큼의 크기

- maxcontent
  컨텐츠의 필요한 만큼의 크기

### SCSS

CSS preprocessor  
(scss, stylus,less ...)
SCSS -> 컴파일 -> CSS로 변환됨  
프로그래밍언어처럼 사용함.  
생산성이 빨라짐.  
Compile과 Build과정이 필요함

#### GULP

Gulp란, 컴파일 or 트랜스폼 해주는 Nodejs package.  
NewCode->OldCode  
Scss->Css

GULP랑 SCSS가 설정되어있는 레포지토리 사용하려다  
에러폭탄 맞고 해결하려고 시간쏟다가  
개 비효율적인것같아서 관둠.

#### 그래서 사용한 방법

scss 를 css 로 컴파일 해주는 명령어를 입력함.  
sass style.scss style.css  
근데 이것만 하면 맨날 수동으로 컴파일 하는거니까  
sass 의 watch라는 옵션을 써서 상시 컴파일되게함  
sass --watch styles.scss styles.css  
혹은 scss, css폴더를 구분해두었다면 폴더왓칭  
sass --watch scss:css

- variable
  variable은 scss에만 사용한다.  
  따라서 css로 변환하기를 원하지 않는다.  
  css로의 변환을 원하지않는것들엔 \_을 맨 앞에 둔다.  
  $bg: red;와 같이 선언,  
  @import "\_variable"로 적재해서 사용한다.

- Nesting
  CSS를 계층구조로 작성가능  
  가상클래스선택자의 경우 &:active로 사용

- Mixins
  @mixin name {}  
  @mixin name($color) {}   
a{@include name() or name(blue)}   
문자열을보낼수도 있다. @include name('str')   
@mixin name($word) {@if $word === 'str'{}@else{} }

- Extends
  같은코드를 중복하고싶지 않을때 사용  
  (mixin은 상황에 따라 다르게 코딩하고 싶을 때 사용,  
  또, if~else처리의 유무 ? )  
  코드확장 or 재사용  
  %를 사용  
  include %extendsName
