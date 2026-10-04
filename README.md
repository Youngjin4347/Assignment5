## 22200635 장영진 OSS 2026-2 week 5
## Key Learning
1. DOM에 대해 배웠다. document.getClementByID(), querySelector()등을 통해 특정 요소를 선택하거나 element.textContent, element.innerHTML등으로 내용을 변경, 또 appendChild()등을 통해 추가, 삭제하는 법을 알게 되었다.
2. 이벤트에 대해 배웠다. 이벤트로 상호작용(click, mousemove)을 처리하는 법에 대해 알게 되었다.

## 이번 주에 배운 핵심 내용 3가지
1. DOM을 조작, 처리하는 것을 실습을 통해 익히게 되었다.
2. 서버없이 배열을 데이터 저장소로 활용하는 법에 대해 알게 되었다.
3. 이벤트로 상호작용을 처리하는 법에 대해 알게 되었다.

## CRUD Service

# 구현한 서비스 주제
week3에서 연습한 도서관리 프로그램의 코드를 일부분 따와서 도서관리 프로그램(수정, 삭제, 추가)를 구현했습니다. 
각 도서는 도서ID, 도서명, 장르, 저자, 출판사, 대여상태(대여가능, 대여중)으로 정보를 나타냈습니다.
사용자는 새로운 도서를 추가할 수 있으며 이때 추가하는 양식이 다를 경우 목록에 추가되지 않는 기능도 구현했습니다.
추가 뿐만 아니라 사용자는 기존의 데이터를 삭제하거나 수정하는 기능도 구현했습니다.
또한 웹페이지 하단에 홈버튼(index.html)울 추가하여 돌아갈 수 있도록 구현하였습니다.

# 사용하는 데이터 Field
1. 도서ID : 숫자 6개로 구성된 도서 ID
2. 도서명
3. 장르
4. 저자
5. 출판사
6. 대여상태(대여가능, 대여중) : select를 사용하여 두 개 중 하나를 선택해야 함

## Create / Read / Update / Delete 구현 방법
1. Create : 입력한 도서 정보를 JavaScript Array에 push하여 추가합니다.
2. Read : showBooks() (과제에서는 render이지만 showBooks라는 이름이 더 직관적이라 생각하여 바꾸었습니다.)함수를 이용하여 Array의 도서 정보를 화면에 출력했습니다.
3. Update : 수정 버튼을 클릭하면 UpdateIndex에 수정할 배열의 위치를 저장하고, 입력장에 기존 정보를 불러온 후 수정했습니다.
4. Delete : 삭제 버튼을 클릭하면 confirm으로 삭제 여부를 확인하고 splice를 이용하여 Array에서 데이터를 삭제했습니다.

## JavaScript

# 이번 과제에서 사용한 주요 JavaScript 기능을 설명합니다.
1. querySelector : HTML 요소를 선택하기 위해 사용, 입력창이나 버튼을 자바스크립트에서 가져올 때 사용함
2. addEventListener : 저장, 수정, 삭제 버튼의 click 이벤트를 처리하기 위해 사용함
3. createElement : 도서 목록을 출력할 때 li과 button 요소를 생성하기 위해 사용함
4. appenChild : 생성한 도서 목록과 버튼을 HTML에 추가하기 위해 사용함
5. Array : 도서 정보를 저장하기위해 사용함
6. push : 새로운 도서를 Array에 추가하기 위해 사용함
7. splice : 삭제할 도서를 Array에서 제거하기 위해 사용함
8. showBooks : Array에 저장된 도서 정보를 HTML 화면에 출력하는 함수로 사용함
9. updateIndex : Array에서 현재 수정하는 도서가 몇번째 위치에 있는지 저장하여 create와 update를 구분하는데 사용함

## 사용한 AI 또는 검색 도구
chat_GPT, Google 검색

# 어떤 문제를 해결하기 위해 사용했는지
1. splice의 사용 방법에 대해서 AI를 활용했습니다. 처음에는 removeChild를 사용했지만 이는 HTML 화면에서만 삭제되기 때문에 delete의 조건을 충족하지 못했습니다.  검색을 해서 splice를 알게 된 후 사용법과 예제들을 AI에게 물어보았습니다.

2. 새로운 도서를 추가하거나 기존의 도서를 수정할 때 Array를 망가뜨리지 않기 위해 구분하는 문제에서 활용했습니다. AI에게 어떻게 해결하면 좋은지 물어본 후 새로운 도서를 추가할 때는 updateIndex = -1로 설정하는 방법을 알게 되었고 이를 구현했습니다.

3. Array의 데이터를 변경했는데도 화면에 출력되는 내용이 뜻대로 흘러가지 않았습니다. AI에게 물어본 결과 showBooks가 추가, 수정, 삭제가 실행된 후 다시 호출되어야 현재 Array의 화면이 출력되는 것을 알게 되었습니다.
# 실제 코드에 어떻게 적용했는지
1. 이전 코드
deleteBtn.addEventListener("click", function () {
    bookList.removeChild(li);
});
변경 후 
deleteBtn.addEventListener("click", function () {
    if (confirm("삭제하시겠습니까?")) {
        books.splice(i, 1);
        showBooks();
    }
});

2. let updateIndex = -1;을 추가하고 updateIndex가 -1인지 아닌지를 통해 추가나 수정을 구분하였습니다.

3. showBooks() 추가

# 새롭게 이해한 내용
addEventListener(), querySelector(), createElement(), appendChild() 등을 사용하면서 자바스크립트를 이용해 HTML 요소를 동적으로 생성하고 변경하는 방법을 익혔습니다. 

## Reflection, 이번 과제를 통해 새롭게 알게 된 점 또는 궁금한 점
삭제 기능을 구현할 때 화면에서 항목만 삭제하는 것이 아니라 배열에서도 데이터를 삭제해야 된다는 것을 알게 되었습니다. 자바스크립트와 DOM을 활용하여 직접 웹 서비스를 구현하는 과정을 경험할 수 있었습니다.
이번 과제를 통해 자바스크립트 배열을 사용하여 별도의 서버없이 데이터 저장소로 사용하는 것을 알게 되었다. 또한 CRUD 기능을 직접 구현하며 추가, 수정, 삭제 같은 기능적인 부분을 자바스크립트를 사용하면서 실제 코드가 어떻게 사용되고 흘러가는지 이해하는 시간이었다. 또한 이번 과제 방법과 다르게 서버와 데이터베이스를 사용하는 CRUD 구현 방법도 알아보고싶다.