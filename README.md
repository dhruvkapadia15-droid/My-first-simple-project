# My-first-simple-project
#This is the simple library management system app which store you book which you have readed or you want to read 


<!DOCTYPE html>

<html>
<head>
  <title>Library system</title>
  <link rel="stylesheet" href="css/style.css">
</head>
<body>
  <h1> Library Management System </h1>
  
  <input type="text" id = "bookname" placeholder = "enter your book name">
  <button onclick = "addbook()">Add book</button>
  
  <ul id = "booklist"></ul>
  <script src = "js/script.js"></script>



<style>

body
{
  font-family: arial;
  text-align: center;
  background-color: lightgray;
}

input
{
  padding: 10px;
  margin: 15px;
}

button
{
  padding:10px;
  background-color:blue;
  color:white;
}
  </style>
  
<script>
let books =[];
function addbook()
{
  let bookname = document.getElementById("bookname").value = "";
  
  if (bookname === "")
  {
    alert("enter book name");
    return;
  }
   books.push(bookname);
  displaybooks();
}
function displaybooks()
{
  let list = document.getElementById("booklist");
  list.innerHTML = "";
  
  books.forEach(( book , index) => {
    let li = document.createElement("li");
    li.innerHTML = book + " <button onclick = 'deleteBook(" + index + ")'>Delete</button>";
    list.appendChild(li);
  });
}

function deleteBook(index)
{
  books.splice(index , 1);
  displaybooks();
}
</script>
  
  </body>
</html>
