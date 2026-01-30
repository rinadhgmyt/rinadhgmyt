<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>People Search</title>

<style>
  body {
    background-color: black;
    color: red;
    font-family: Arial, sans-serif;
    text-align: center;
    padding: 40px;
  }

  h1 {
    font-size: 40px;
    text-shadow: 0 0 6px red;
  }

  input[type="text"] {
    margin-top: 20px;
    padding: 12px;
    width: 320px;
    font-size: 16px;
    color: red;
    background: rgba(255, 0, 0, 0.15); /* transparent red */
    border: 2px solid red;
    border-radius: 8px;
    outline: none;
  }

  input::placeholder {
    color: #ff9999;
  }

  .person {
    margin-top: 30px;
    display: inline-block;
    border: 1px solid red;
    border-radius: 12px;
    padding: 15px;
    width: 220px;
    box-shadow: 0 0 10px red;
  }

  .person img {
    width: 150px;
    border-radius: 10px;
    margin-bottom: 10px;
  }

  .person h2 {
    margin: 10px 0 5px;
  }

  .person p {
    color: #ff7777;
    font-size: 14px;
  }
</style>
</head>

<body>

<h1>Search People</h1>

<input
  type="text"
  id="search"
  placeholder="Type a name..."
  onkeyup="searchPerson()"
>

<div id="result"></div>

<script>
const people = [
  { name: "Person1", img: "person1.jpg", details: "Details about Person1" },
  { name: "Person2", img: "person2.jpg", details: "Details about Person2" },
  { name: "Person3", img: "person3.jpg", details: "Details about Person3" },
  // keep adding like this
  { name: "Person51", img: "person51.jpg", details: "Details about Person51" }
];

function searchPerson() {
  const input = document.getElementById("search").value.toLowerCase();
  const resultDiv = document.getElementById("result");
  resultDiv.innerHTML = "";

  const filtered = people.filter(p =>
    p.name.toLowerCase().includes(input)
  );

  filtered.forEach(p => {
    const div = document.createElement("div");
    div.className = "person";
    div.innerHTML = `
      <img src="${p.img}" alt="${p.name}">
      <h2>${p.name}</h2>
      <p>${p.details}</p>
    `;
    resultDiv.appendChild(div);
  });

  if (input && filtered.length === 0) {
    resultDiv.innerHTML = "<p>No results found</p>";
  }
}
</script>

</body>
</html>
 
