# 인터뷰 정리

# HTML

## **DOCTYPE이란?**

DOCTYPE은 document type의 약어입니다. DOCTYPE은 항상 **DTD(Document Type Definition)**와 관련됩니다.

DTD는 특정 문서가 어떻게 구성되어야 하는지 정의합니다(예시: button은 span을 포함할 수 있지만, div는 포함할 수 없다.), 반면, DOCTYPE은 문서가 대략 존중할만한 DTD를 선언합니다. (예시: 이 문서는 HTML DTD를 존중한다.)

html문서 작성시 브라우저에게 버전을 알려주기 위하여 맨 처음에 html 버전을 표시하는데 이를 "DTD = document type definition = DOCTYPE = 독타입"이라고 부른다.

현재의 html5 버전의 독타입은 `<!DOCTYPE html>`로 표시한다.

위 html문서의 소스코드에서 보는 것처럼 맨 처음에 `<!DOCTYPE html>`를 표시하여 웹브라우저가 이 소스코드를 읽을때 이 웹문서가 html5로 작성되었음을 알려 준다.

웹 페이지의는 DOCTYPE 선언이 필요합니다. 유저 에이전트에게 문서가 존중하는 HTML 사양의 버전을 알리는데 사용됩니다.

## **cookie, sessionStorage, localStorage 사이의 차이점을 설명하세요.**

위 세 가지 기술은 모두 클라이언트 측에서 값을 저장하는 key-value 저장소 매커니즘입니다. 모두 문자열로만 값을 저장할 수 있습니다.

|                             | cookie                                                         | sessionStorage | localStorage |
| --------------------------- | -------------------------------------------------------------- | -------------- | ------------ |
| 생성자                      | 클라이언트나 서버. 서버는 Set-Cookie 헤더를 사용할 수 있습니다 | 클라이언트     | 클라이언트   |
| 만료                        | 수동으로 설정                                                  | 영구적         | 탭을 닫을 때 |
| 브라우저 세션 전체에서 지속 | 만료설정 여부에 따라 다름                                      | O              | X            |
| 용량(도메인당)              | 4kb                                                            | 5MB            | 5MB          |
| 접근성                      | 모든 윈도우                                                    | 모든 윈도우    | 같은 탭      |

## **`<script>`, `<script async>`, `<script defer>` 사이의 차이점을 설명하세요.**

`<script>` - HTML 파싱이 중단되고, 스크립트를 즉시 가져오고 실행되며, 스크립트 실행 후 HTML 파싱이 다시 시작됩니다.

`<script async>` - 이 스크립트는 HTML 파싱과 병렬적으로 가져오며, 가능할 때 즉시 실행됩니다(아마 HTML 파싱이 끝나기 전). 스크립트가 페이지의 다른 스크립트들과 독립적인 경우 async를 사용하세요. 예) analytics.

`<script defer>` - 이 스크립트는 HTML 파싱과 병렬적으로 가져오지만, 페이지 파싱이 끝나면 실행됩니다. 이 것이 여러개 있는 경우, 각 스크립트는 페이지에 등장한 순서대로 실행됩니다. 스크립트가 완전히 파싱된 DOM에 의존되는 경우 defer 속성은 스크립트를 실행하기 전에 HTML이 완전히 파싱되도록 하는데 유용합니다. `<body>`의 끝부분에 일반 `<script>`를 두는 것과 별 차이가 없습니다. defer 스크립트는 document.write를 포함하면 안됩니다.

주의: src 속성이 없는 스크립트 태그는 async 와 defer 속성이 무시됩니다.
