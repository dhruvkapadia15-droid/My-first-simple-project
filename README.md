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
  font-family: arial , sans-serif;
  text-align: center;
  background: linear-gradient(to right, #667eea ,#764ba2);
  color:white;
}
  
  h1
  {
    margin-top: 20px
  }

input
{
  padding: 10px;
  border-radius: 8px;
  border:none;
  outline:none;
  width: 200px
  
}

button
{
  padding:10px 15px;
  background-color: #ff7b00;
  color:white;
  cursor:pointer;
  border-radius: 8px;
  border: none;
  transition:0.3s;
}
  
  button:hover {
    background-color: #ff5500;
    transform : scale(1.05);
  }
  
  ul
  {
    list-style: none;
    padding:0;
  }
  
  li
  {
    background : white;
    color:black;
    margin: 10px auto;
    padding:10px;
    width: 300px;
    border-radius: 10px;
    display:flex;
    justify-content: space-between;
    align-items: center;
  }
  </style>
  
<script>
let books =[];
  document.getElementById("bookname").addEventListener("keypress",function(e)
  {
    if(e.key === "Enter"){
      addbook();
    }
  })
  
  
function addbook()
{
  let bookname = document.getElementById("bookname").value;
  
  if (bookname === "")
  {
    alert("enter book name");
    return;
  }
   books.push({ name: bookname , read: false});
  saveBooks();
  displaybooks();
}
  
  
function displaybooks()
{
  let list = document.getElementById("booklist");
  list.innerHTML = "";
  
  if(books.length === 0){
    list.innerHTML = "<p> no books are added!!</p>";
    return;
  }
  
  books.forEach(( book , index) => {
    let li = document.createElement("li");
    li.innerHTML = `
    <span style = "text-decoration:${book.read ? 'line-through' : 'none' }">${book.name}</span>
    <div>
      <button onclick="toggleRead(${index})">✔</button>
      <button onclick="deleteBook(${index})">❌</button>
    </div>`;
    list.appendChild(li);
  });
}
  
function toggleRead(index){
  books[index].read = !books[index].read;
  displaybooks();
}
  
  function deleteBook(index){
    books.splice(index , 1);
    saveBooks();
    displaybooks();
  }
  
  
  function saveBooks() {
  localStorage.setItem("books", JSON.stringify(books));
}

function loadBooks() {
  let data = localStorage.getItem("books");
  if (data) {
    books = JSON.parse(data);
  }
}

loadBooks();
displaybooks();

</script>
  
  </body>
</html>
