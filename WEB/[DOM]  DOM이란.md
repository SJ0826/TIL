# DOM이란?

DOM은 Document Object Model의 줄임말로, **웹브라우저가 html을 읽어오는 방식**을 뜻합니다.<br><br>

브라우저는 html의 태그들을 javaScript의 노드로 변환합니다.<br><br>

노드는 eventTarget을 상속합니다.<br><br>

즉, 모든 노드는 이벤트가 발생하는데 document도 노드를 상속하기 때문에 document에서도 이벤트가 발생합니다.<br><br>

브라우저가 실행될때 웹페이지를 읽으면 글로벌 오브젝트에는 윈도우가 들어있고, 윈도우에는 document가 들어있습니다.<br><br>

이 document는 나무형태로 뿌리를 내리는 이것을 **document tree**라고 합니다.

작성하는 모든 html문서는 document tree의 형태로 구성됩니다.<br><br>
