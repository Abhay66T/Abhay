<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tech Store</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Poppins',sans-serif;
}

body{
background:#f7f7f7;
color:#222;
}

/* NAVBAR */

nav{
display:flex;
justify-content:space-between;
align-items:center;
padding:15px 30px;
background:#111;
color:white;
position:sticky;
top:0;
z-index:1000;
}

.logo{
font-size:22px;
font-weight:700;
}

.tag{
font-size:14px;
color:#aaa;
}

.cart-btn{
background:#00eaff;
color:black;
padding:8px 15px;
border-radius:20px;
cursor:pointer;
}

/* HERO */

.hero{
height:85vh;
background:url("https://i.ibb.co/bR8R0BvV/IMG-0895.jpg") center/cover no-repeat;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
text-align:center;
color:white;
}

.hero h1{
font-size:48px;
margin-bottom:10px;
}

.hero p{
font-size:18px;
margin-bottom:20px;
}

.hero button{
padding:12px 28px;
background:#00eaff;
border:none;
font-size:16px;
border-radius:30px;
cursor:pointer;
}

/* PRODUCTS */

.products{
padding:60px 20px;
}

.products h2{
text-align:center;
margin-bottom:30px;
}

.carousel{
display:flex;
gap:20px;
overflow-x:auto;
scroll-behavior:smooth;
}

.product{
min-width:260px;
background:white;
padding:20px;
border-radius:15px;
box-shadow:0 10px 25px rgba(0,0,0,0.08);
text-align:center;
transition:.3s;
}

.product:hover{
transform:translateY(-5px);
}

.product img{
width:100%;
border-radius:10px;
}

.product h3{
margin:10px 0;
}

.price{
font-weight:600;
margin-bottom:10px;
}

.product button{
background:#111;
color:white;
padding:10px 15px;
border:none;
border-radius:20px;
cursor:pointer;
}

/* CART PANEL */

.cart-panel{
position:fixed;
right:-350px;
top:0;
width:320px;
height:100%;
background:white;
box-shadow:-5px 0 20px rgba(0,0,0,0.1);
padding:20px;
transition:.4s;
overflow:auto;
z-index:2000;
}

.cart-panel.active{
right:0;
}

.cart-panel h2{
margin-bottom:10px;
}

.cart-item{
padding:8px 0;
border-bottom:1px solid #eee;
}

input{
width:100%;
padding:10px;
margin-top:10px;
border:1px solid #ddd;
border-radius:5px;
}

.order-btn{
margin-top:15px;
width:100%;
background:#00eaff;
border:none;
padding:12px;
cursor:pointer;
font-weight:600;
}

/* WHATSAPP */

.whatsapp{
position:fixed;
bottom:20px;
right:20px;
background:#25D366;
color:white;
font-size:22px;
padding:15px;
border-radius:50%;
text-decoration:none;
}

/* FOOTER */

footer{
text-align:center;
padding:20px;
margin-top:40px;
background:#111;
color:#aaa;
}

</style>
</head>

<body>

<nav>
<div>
<div class="logo">Tech Store</div>
<div class="tag">Fresh Finds, Best Prices</div>
</div>

<div class="cart-btn" onclick="toggleCart()">
Cart (<span id="cartCount">0</span>)
</div>
</nav>


<section class="hero">

<h1>Latest Tech Products</h1>
<p>Buds • Headphones • Phones</p>

<button onclick="document.getElementById('products').scrollIntoView({behavior:'smooth'})">
Shop Now
</button>

</section>


<section class="products" id="products">

<h2>Popular Products</h2>

<div class="carousel">

<div class="product">
<img src="https://i.ibb.co/8nJF6pHw/0-e1e4339f-0237-4909-8202-0176f1dbfffa.jpg">
<h3>Wireless Earbuds</h3>
<div class="price">₹999</div>
<button onclick="addCart('Wireless Earbuds',999)">Add to Cart</button>
</div>

<div class="product">
<img src="https://i.ibb.co/8nJF6pHw/0-e1e4339f-0237-4909-8202-0176f1dbfffa.jpg">
<h3>Bluetooth Headphones</h3>
<div class="price">₹1499</div>
<button onclick="addCart('Bluetooth Headphones',1499)">Add to Cart</button>
</div>

<div class="product">
<img src="https://i.ibb.co/8nJF6pHw/0-e1e4339f-0237-4909-8202-0176f1dbfffa.jpg">
<h3>Smartphone</h3>
<div class="price">₹12999</div>
<button onclick="addCart('Smartphone',12999)">Add to Cart</button>
</div>

</div>

</section>


<div class="cart-panel" id="cartPanel">

<h2>Your Cart</h2>

<div id="cartItems"></div>

<input id="customerName" placeholder="Your Name">
<input id="customerPhone" placeholder="Phone Number">

<button class="order-btn" onclick="sendOrder()">Place Order</button>

</div>


<a class="whatsapp" href="https://wa.me/" target="_blank">💬</a>


<footer>
© 2026 Tech Store
</footer>


<script>

let cart=[]

function addCart(name,price){

cart.push({name,price})

updateCart()

}

function updateCart(){

document.getElementById("cartCount").innerText=cart.length

let items=""

cart.forEach(i=>{
items+=`<div class="cart-item">${i.name} - ₹${i.price}</div>`
})

document.getElementById("cartItems").innerHTML=items

}

function toggleCart(){

document.getElementById("cartPanel").classList.toggle("active")

}

function sendOrder(){

let name=document.getElementById("customerName").value
let phone=document.getElementById("customerPhone").value

if(name==""||phone==""){
alert("Enter name and phone")
return
}

let items=cart.map(i=>`${i.name} ₹${i.price}`).join("%0D%0A")

let email=`mailto:abhaypandit673@gmail.com?subject=New Tech Store Order&body=
Customer Name: ${name}%0D%0A
Phone: ${phone}%0D%0A
Items:%0D%0A${items}`

window.location.href=email

}

</script>

</body>
</html>html>
