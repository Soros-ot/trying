<!DOCTYPE html>
<html>

<head>
</head>

<body>
<button id="editBtn" type="button">Edit Document</button>

<div id="editor">
    <h1 id="title">A Nice Heading.</h1>
    <p>Last Edited By - <span id="author">me</span></p>
    <p id="content">Some content that needs correction.</p>
    <p id="content2">Найс кодировка слетела</p>
</div>

<script>

var editBtn = document.getElementById('editBtn');
var editables = document.querySelectorAll('#title, #author, #content, #content2')

editBtn.addEventListener('click', function(e) {
  if (!editables[0].isContentEditable) {
    editables[0].contentEditable = 'true';
    editables[1].contentEditable = 'true';
    editables[2].contentEditable = 'true';
    editables[3].contentEditable = 'true';
    editBtn.innerHTML = 'Save Changes';
    editBtn.style.backgroundColor = '#6F9';
  } else {
    // выключаем режим редактирования
    editables[0].contentEditable = 'false';
    editables[1].contentEditable = 'false';
    editables[2].contentEditable = 'false';
    editables[3].contentEditable = 'false';
    // изменяем текст и цвет кнопки
    editBtn.innerHTML = 'Enable Editing';
    editBtn.style.backgroundColor = '#F96';
    // сохраняем данные в localStorage
    for (var i = 0; i < editables.length; i++) {
      localStorage.setItem(editables[i].getAttribute('id'), editables[i].innerHTML);
    }
  }
});
</script>

<script>
if (typeof(Storage) !== "undefined") {

  if (localStorage.getItem('title') !== null) {
    editables[0].innerHTML = localStorage.getItem('title');
  }

  if (localStorage.getItem('author') !== null) {
    editables[1].innerHTML = localStorage.getItem('author');
  }

  if (localStorage.getItem('content') !== null) {
    editables[2].innerHTML = localStorage.getItem('content');
  }

  if (localStorage.getItem('content2') !== null) {
    editables[3].innerHTML = localStorage.getItem('content2');
  }
}
</script>

</body>

</html>
