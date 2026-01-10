# myshop-server.js-products.json-public-index.html-style.css-script.js
A few types of products are available here
const express = require("express");
const app = express();
const fs = require("fs");

app.use(express.json());
app.use(express.static("public"));

app.get("/products", (req, res) => {
    const data = fs.readFileSync("products.json");
    res.json(JSON.parse(data));
});

app.post("/order", (req, res) => {
    console.log("Order received:", req.body);
    res.send({ message: "Order placed successfully!" });
});

app.listen(3000, () => {
    console.log("Server running on http://localhost:3000");
});
[
  {
    "id": 1,
    "name": "Wireless Earbuds",
    "price": 999,
    "image": "https://via.placeholder.com/150"
  },
  {
    "id": 2,
    "name": "Smart Watch",
    "price": 1499,
    "image": "https://via.placeholder.com/150"
  }
]
<!DOCTYPE html>
<html>
<head>
    <title>My Shop</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="style.css">
</head>
<body>

<header>🛒 My Mobile Shop</header>

<div id="products"></div>

<div class="cart">
    <h3>Cart Total: ₹<span id="total">0</span></h3>
    <button onclick="placeOrder()">Place Order</button>
</div>

<script src="script.js"></script>
</body>
</html>
body {
    margin: 0;
    font-family: Arial;
    background: #f1f1f1;
}

header {
    background: #2874f0;
    color: white;
    padding: 15px;
    text-align: center;
    font-size: 20px;
}

#products {
    padding: 10px;
}

.product {
    background: white;
    margin-bottom: 10px;
    padding: 10px;
    border-radius: 5px;
}

.product img {
    width: 100%;
}

button {
    background: #ff9f00;
    border: none;
    padding: 10px;
    width: 100%;
    font-weight: bold;
}

.cart {
    position: fixed;
    bottom: 0;
    background: white;
    width: 100%;
    padding: 10px;
    box-shadow: 0 -2px 5px gray;
}
let total = 0;

fetch("/products")
.then(res => res.json())
.then(data => {
    let productsDiv = document.getElementById("products");
    data.forEach(p => {
        productsDiv.innerHTML += `
        <div class="product">
            <img src="${p.image}">
            <h3>${p.name}</h3>
            <p>₹${p.price}</p>
            <button onclick="addToCart(${p.price})">Add to Cart</button>
        </div>`;
    });
});

function addToCart(price) {
    total += price;
    document.getElementById("total").innerText = total;
}

function placeOrder() {
    fetch("/order", {
        method: "POST",
        headers: {"Content-Type": "application/json"},
        body: JSON.stringify({ total })
    })
    .then(res => res.json())
    .then(data => alert(data.message));
}
