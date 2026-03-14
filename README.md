<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tech Store</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial;
}

body{
background:#f5f5f5;
}

/* NAV */

nav{
background:#111;
color:white;
padding:15px;
display:flex;
justify-content:space-between;
align-items:center;
}

nav h1{
font-size:22px;
}

nav span{
color:#00eaff;
}

/* HERO */

.hero{
height:90vh;
background:url("https://i.ibb.co/bR8R0BvV/IMG-0895.jpg") center/cover no-repeat;
display:flex;
flex-direction:column;
align-items:center;
justify-content:center;
color:white;
text-align:center;
}

.hero h2{
font-size:45px;
margin-bottom:10px;
}

.hero p{
font-size:20px;
margin-bottom:20px;
}

.hero button{
padding:12px 30px;
border:none;
background:#00eaff;
color:black;
font-size:18px;
cursor:pointer;
border-radius:5px;
}

/* PRODUCTS */

.products{
padding:40px 20px;
}

.products h2{
text-align:center;
margin-bottom:20px;
}

.carousel{
display:flex;
overflow-x:auto;
gap:20px;
scroll-behavior:smooth;
}

.product{
min-width:230px;
background:white;
border-radius:10px;
padding:15px;
box-shadow:0 0 10px rgba(0,0,0,0.1);
text-align:center;
}

.product img{
width:100%;
border-radius:10px;
}

.product h3{
margin:10px 0;
}

.product button{
background:#111;
color:white;
border:none;
padding:10px;
cursor:pointer;
border-radius:5px;
}

/* CART */

.cart{
background:white;
padding:30px;
margin:20px;
border-radius:10px;
}

.cart h2{
margin-bottom:10px;
}

.cart input{
width:100%;
padding:10px;
margin:10px 0;
}

.cart button{
background:#00eaff;
border:none;
padding:12px;
width:100%;
font-size:16px;
cursor:pointer;
}

/* WHATSAPP */

.whatsapp{
position:fixed;
bottom:20px;
right:20px;
background:#25D366;
color:white;
padding:15px;
border-radius:50%;
font-size:24px;
text-decoration:none;
}

</style>
</head>

<body>

<nav>
<h1>Tech <span>Store</span></h1>
<p>Fresh Finds, Best Prices</p>
</nav>


<!-- HERO -->

<section class="hero">

<h2>Latest Technology Products</h2>
<p>Buds, Headphones, Phones & More</p>

<button onclick="document.getElementById('products').scrollIntoView({behavior:'smooth'})">
Shop Now
</button>

</section>


<!-- PRODUCTS -->

<section class="products" id="products">

<h2>Our Products</h2>

<div class="carousel">

<div class="product">
<img src="https://i.ibb.co/8nJF6pHw/0-e1e4339f-0237-4909-8202-0176f1dbfffa.jpg">
<h3>Wireless Earbuds</h3>
<p>₹999</p>
<button onclick="addToCart('Wireless Earbuds',999)">Add to Cart</button>
</div>

<div class="product">
<img src="https://i.ibb.co/8nJF6pHw/0-e1e4339f-0237-4909-8202-0176f1dbfffa.jpg">
<h3>Bluetooth Headphones</h3>
<p>₹1499</p>
<button onclick="addToCart('Bluetooth Headphones',1499)">Add to Cart</button>
</div>

<div class="product">
<img src="https://i.ibb.co/8nJF6pHw/0-e1e4339f-0237-4909-8202-0176f1dbfffa.jpg">
<h3>Smartphone</h3>
<p>₹12999</p>
<button onclick="addToCart('Smartphone',12999)">Add to Cart</button>
</div>

</div>

</section>


<!-- CART -->

<section class="cart">

<h2>Your Cart</h2>

<ul id="cartItems"></ul>

<input id="name" placeholder="Your Name">
<input id="phone" placeholder="Phone Number">

<button onclick="placeOrder()">Place Order</button>

</section>


<!-- WHATSAPP -->

<a class="whatsapp" href="https://wa.me/" target="_blank">
💬
</a>


<script>

let cart=[]

function addToCart(name,price){

cart.push({name,price})

renderCart()

}

function renderCart(){

let list=document.getElementById("cartItems")

list.innerHTML=""

cart.forEach(item=>{
let li=document.createElement("li")
li.innerText=item.name+" - ₹"+item.price
list.appendChild(li)
})

}

function placeOrder(){

let name=document.getElementById("name").value
let phone=document.getElementById("phone").value

if(name==""||phone==""){
alert("Please enter name and phone")
return
}

let items=cart.map(i=>i.name+" ₹"+i.price).join("%0D%0A")

let mail=
`mailto:abhaypandit673@gmail.com?subject=New Order&body=
Customer Name: ${name}%0D%0A
Phone: ${phone}%0D%0A
Items:%0D%0A
${items}`

window.location.href=mail

}

</script>

</body>
</html>
