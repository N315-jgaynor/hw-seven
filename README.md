# N320 Homework Seven

This assignment utilized more advanced JSON nesting with objects and retrieving information within them. Additionally, it added the functionality of users being able to add/remove options from a list as well as changing the styling when an item was checked off.

# Web4 Link

https://in-info-web4.informatics.iupui.edu/~jgaynor/hw-seven/index.html

# Project Highlights

## JSON Loops with Styling

We were able to loop through objects while retaining container styling using a new combination of variables and looping with JSON. We defined a variable and used += (similar to .append) to insert a JSON loop within a container.

```js
function loadLists() {
  let listString = `<div class="events-container">`;
  $.each(LISTS, function (idx, list) {
    listString += `<li id="${idx}" onclick="loadListItems(${idx})"><p>${list.name}</p><span class="right"> Competitors: ${list.listItems.length}</span></li>`;
  });
  listString += "</div>";
  $(".home-content").html(listString);
}
```

## Adding/Removing Objects

By using .push and .splice, we were able to add/remove objects within the page memory. Any changes made were removed and set to default if the page was reloaded. This will change in later assignments with the use of external databases.

```js
function addItem(listIndex) {
  let newItemName = $("#addItem").val();
  let newItemObj = {
    name: newItemName,
    checked: false,
    category: "",
  };

  LISTS[listIndex].listItems.push(newItemObj);
  loadListItems(listIndex);
}
```

```js
function deleteItem(listIndex, idx) {
  LISTS[listIndex].listItems.splice(idx, 1);
  loadListItems(listIndex);
}
```

## Problems Encountered

For some reason, setting the script that imports app/app.js cannot be set to type="module" for onclick="" to work on html files. I was unable to get the buttons working for a while but removing the type solved the problem and I am unsure as to why that is.

```html
<script type="module" src="app/app.js"></script>
```
