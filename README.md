# mainonlyRevert
mainonlyRevert 是一个专门设计用于网页浏览器的 JavaScript 书签小程序。它能够突出显示和操作网页中的 HTML 元素，提供直观的页面元素导航和互动功能。通过鼠标悬停、点击和滚轮操作，用户可以选择和突出显示页面上的任何元素，同时隐藏非目标元素。且在取消突出显示后，页面会自动回到之前的滚动位置，便于用户快速返回到原先的浏览状态。

# 功能：
   - 当用户将鼠标悬停在页面上的任何元素上时，该元素会被突出显示。
   - 点击任意元素会隐藏页面上的其他元素，仅显示选中的元素及其子元素。
   - 使用鼠标滚轮可以在选中的元素的父元素和第一个子元素之间切换。
   - 按下 `Escape` 键取消突出显示，恢复页面到正常状态，并将滚动位置回到之前的位置。

# 使用方法
1. 复制以下代码：
```
javascript:(function(){var e=document.body;var currentScrollPosition;const n=document.head.appendChild(document.createElement("style"));n.textContent=".mainonly { outline: 2px solid red; }";const t=CSS.supports("selector(:has(*))");function o(n){if(n instanceof HTMLElement){e.classList.remove("mainonly");currentScrollPosition=window.scrollY;(e=n).classList.add("mainonly")}}function s(e){o(e.target)}function a(o){if(o.preventDefault(),t){n.textContent=":not(:has(.mainonly), .mainonly, .mainonly *) { display: none; }"}else{n.textContent=":not(.mainonly *, .mainonly-ancestor) { display: none; }";var s=e;do{s.classList.add("mainonly-ancestor")}while(s=s.parentElement)}l()}function i(n){n.preventDefault();n.deltaY<0?o(e.parentElement):o(e.firstElementChild)}function l(){document.removeEventListener("mouseover",s),document.removeEventListener("click",a),document.removeEventListener("wheel",i)}document.addEventListener("mouseover",s),document.addEventListener("click",a),document.addEventListener("wheel",i,{passive:!1});document.addEventListener("keydown",(function o(s){if("Escape"===s.key){n.remove(),document.removeEventListener("keydown",o),l(),e.classList.remove("mainonly"),!t&&Array.from(document.getElementsByClassName("mainonly-ancestor")).forEach(e=>e.classList.remove("mainonly-ancestor")),window.scrollTo(0,currentScrollPosition)}}))}());
```
2. 右键点击您的浏览器书签栏，选择“添加书签”。

3. 在弹出的窗口中，为书签命名（例如：“mainonlyRevert”），并将复制的代码粘贴到 URL 或位置栏中。

4. 保存书签。

5. 在网页上，激活书签后，点击您想要关注的元素。该元素将被红色轮廓圈出。使用滚轮调整选择范围。

6. 选定元素后，点击鼠标左键，其他所有元素将被隐藏，只显示所选元素。

7. 按 ESC 键可显示隐藏的元素，并恢复网页至原始状态，并将滚动位置回到之前的位置。

# 鸣谢
mainonlyRevert源自jerrylususu的mainonly，经过ChatGPT-4修改而成。

若您在取消突出显示后，恢复页面到原始状态即可，不需要返回先前滚动位置的功能，请使用mainonly:
```
https://github.com/jerrylususu/mainonly#how-to-use
```
