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
4   5   
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
1. 그럴때마다 grid-template-ow : repeat(4, 100px)에 숫자를 증가시켜준다?   
=> Bad Solution.   
2. 우리가 지정하지 않은 요소들의 크기를 '자동'으로 지정해주는 설정을 잡아준다.   
=> Good Solution 🥰   
=> 이럴 때 사용하는 것이 grid-auto-rows   
따라서, grid-auto-rows 또는 grid-template-rows에 100px과 같이   
크기만 지정한다면 모든 row의 크기를 자동으로 지정한다.   

- grid-auto-flow(default:row)   
gird-template-row|column으로 지정한 갯수 보다   
요소가 넘쳐버릴 경우, 어느방향으로 추가시킬것인가?   
column인 경우, 열이 늘어난다.   
(그리고 이 때, grid-auto-column이 사용될 수 있다 !)   

 