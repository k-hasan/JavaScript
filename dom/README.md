# 1. Todu List

```composer log
var inp = document.querySelector(".taskname");
var list = document.querySelector(".tasklist");
var taskList = [];
//["get up","brush teeth"]
function render(elements) {
  list.innerHTML = "";
  elements.forEach(e => {
    let newEl = document.createElement("li");
    newEl.innerHTML = e;
    list.appendChild(newEl);
  });
}

inp.addEventListener("keyup", e => {
  if (e.which === 13 && inp.value !== "") {
    taskList.push(inp.value);
    inp.value = "";
    render(taskList);
  }
});
```

```html
<html>
  <head>
    <title>Parcel Sandbox</title>
    <meta charset="UTF-8" />
  </head>

  <body>
    <input class="taskname" placeholder="type and press enter" />
    <ul class="tasklist"></ul>
    <script src="src/index.js"></script>
  </body>
</html>

```

