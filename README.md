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

