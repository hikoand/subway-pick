# subway-pick
Pick your favorite subway topping!

## ๐์ฃผ์๋ก์ง

1. `fetch()`๋ฅผ ํตํด item์ ๋ฐ์์ ๋ฐ์์จ ๋ฐ์ดํฐ๊ฐ ์ฑ๊ณต์ ์ด๋ฉด json์ผ๋ก ๋ณํ์ํค๊ณ  json ์์์๋ items๋ฅผ ๋ฆฌํดํ๋ค.

```javascript
function loadItems() {
  return (
    fetch('data/data.json')
      //json() API๋ฅผ ์ด์ฉํด resopnse body๋ฅผ json() ๊ฐ์ฒด๋ก ๋ณํ
      .then((response) => response.json())
      //json์ item๋ง ์ ๋ฌ
      .then((json) => json.items)
  );
}
```


2. promise๊ฐ return๋๋ฉด (๊ฐ์ ์ฑ๊ณต์ ์ผ๋ก ์ ๋ฌ๋์์ ์) ์ ๋ฌ๋ฐ์ ์์ดํ์ ์ด์ฉํด HTML์ ๋ณด์ฌ์ค๋ค.
- ํ๊ฐ์ง ๋ฐฐ์ด ํํ์์ ๋ค๋ฅธ ํํ ๋ฐฐ์ด๋ก ๋ณํํ๊ธฐ ์ํด `map()`์ ์ด์ฉํ๋ค.
- ๋ฌธ์์ด์ด ๋ค์ด์๋ ๋ฐฐ์ด์ ํ๊ฐ์ง ๋ฌธ์์ด๋ก ๋ณํฉํ๊ธฐ ์ํด `join()`์ฌ์ฉํ๋ค.

```javascript
function displayItems(items) {
  const container = document.querySelector('.items');
  container.innerHTML = items.map((item) => createHTMLString(item)).join('');
}
```

3. ๊ฐ๊ฐ ๋ฐ์์ ์์ดํ์ liํ๊ทธ๋ก ๋ง๋ค์ด html์ ์ถ๋ ฅํ๋ค.
- template Literals ์ด์ฉํ์ฌ ๋ณ์์ ๋ฌธ์์ด์ ๊ฐ๋จํ๊ฒ ์์ฑํ  ์ ์๋ค.

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
