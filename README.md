# subway-pick
Pick your favorite subway topping!

## 🔎주요로직

1. `fetch()`를 통해 item을 받아와 받아온 데이터가 성공적이면 json으로 변환시키고 json 안에있는 items를 리턴한다.

```javascript
function loadItems() {
  return (
    fetch('data/data.json')
      //json() API를 이용해 resopnse body를 json() 객체로 변환
      .then((response) => response.json())
      //json의 item만 전달
      .then((json) => json.items)
  );
}
```


2. promise가 return되면 (값을 성공적으로 전달되었을 시) 전달받은 아이템을 이용해 HTML에 보여준다.
- 한가지 배열 형태에서 다른 형태 배열로 변환하기 위해 `map()`을 이용한다.
- 문자열이 들어있는 배열을 한가지 문자열로 병합하기 위해 `join()`사용한다.

```javascript
function displayItems(items) {
  const container = document.querySelector('.items');
  container.innerHTML = items.map((item) => createHTMLString(item)).join('');
}
```

3. 각각 받아와 아이템을 li태그로 만들어 html에 출력한다.
- template Literals 이용하여 변수와 문자열을 간단하게 작성할 수 있다.

```javascript
function createHTMLString(item) {
  return `
    <li class="item">
        <img src="${item.image}" alt="${item.type}" class="item__thumbnail">
        <span class="item__description">${item.topping1}, ${item.topping2}</span>
    </li>
    `;
}
```
