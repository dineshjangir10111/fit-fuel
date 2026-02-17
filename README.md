<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FIT FUEL</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">

<style>

body{
    margin:0;
    font-family:'Poppins',sans-serif;
    background:linear-gradient(135deg,#e8fff5,#fff6e5);
    padding-bottom:100px;
}

/* HEADER */
header{
    backdrop-filter:blur(15px);
    background:rgba(255,255,255,0.6);
    padding:20px;
    text-align:center;
    position:sticky;
    top:0;
    z-index:1000;
    box-shadow:0 4px 20px rgba(0,0,0,0.1);
}

.logo{
    font-size:26px;
    font-weight:700;
    color:#27ae60;
}

.logo span{
    color:#ff7b00;
}

.tagline{
    font-size:13px;
    color:#555;
}

/* PRODUCT GRID */
.container{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(160px,1fr));
    gap:20px;
    padding:20px;
}

.card{
    background:white;
    border-radius:25px;
    padding:15px;
    text-align:center;
    box-shadow:0 15px 25px rgba(0,0,0,0.08);
    transition:0.3s;
}

.card:hover{
    transform:translateY(-6px);
}

.card img{
    width:100%;
    height:130px;
    object-fit:cover;
    border-radius:20px;
}

.card h3{
    font-size:15px;
    margin:10px 0 5px;
}

.card button{
    background:linear-gradient(90deg,#27ae60,#2ecc71);
    color:white;
    border:none;
    padding:7px 14px;
    border-radius:30px;
    font-size:13px;
    font-weight:600;
    cursor:pointer;
}

/* FLOATING CART BUTTON */
.floatingCart{
    position:fixed;
    bottom:20px;
    right:20px;
    background:linear-gradient(90deg,#ff7b00,#ff512f);
    color:white;
    padding:15px;
    border-radius:50%;
    font-size:20px;
    cursor:pointer;
    box-shadow:0 8px 20px rgba(0,0,0,0.3);
}

.cartCount{
    position:absolute;
    top:-5px;
    right:-5px;
    background:#27ae60;
    color:white;
    font-size:12px;
    padding:3px 7px;
    border-radius:50%;
}

/* SIDEBAR CART */
.cart{
    position:fixed;
    right:-350px;
    top:0;
    width:300px;
    height:100%;
    background:white;
    box-shadow:-5px 0 20px rgba(0,0,0,0.2);
    padding:20px;
    transition:0.4s;
    overflow:auto;
}

.cart.active{
    right:0;
}

.cart h2{
    text-align:center;
    color:#27ae60;
}

.cart img{
    width:100%;
    border-radius:15px;
}

.total{
    font-weight:700;
    margin-top:10px;
    font-size:18px;
}

.closeBtn{
    background:#ff512f;
    color:white;
    border:none;
    padding:8px 15px;
    border-radius:20px;
    cursor:pointer;
    margin-top:10px;
    width:100%;
}

</style>
</head>

<body>

<header>
<div class="logo">🍉 FIT <span>FUEL</span></div>
<div class="tagline">Healthy • Fresh • Energy Boost</div>
</header>

<div class="container" id="fruitContainer"></div>

<!-- Floating Cart -->
<div class="floatingCart" onclick="toggleCart()">
🛒
<div class="cartCount" id="cartBadge">0</div>
</div>

<!-- Sidebar Cart -->
<div class="cart" id="cart">
<h2>Your Order</h2>
<div id="cartItems"></div>
<div class="total" id="total">Total: ₹0</div>
<button class="closeBtn" onclick="toggleCart()">Close</button>
</div>

<script>

const fruits = [
{name:"Banana", img:"https://images.pexels.com/photos/461208/pexels-photo-461208.jpeg"},
{name:"Mango", img:"https://images.pexels.com/photos/2294471/pexels-photo-2294471.jpeg"},
{name:"Apple", img:"https://images.pexels.com/photos/102104/pexels-photo-102104.jpeg"},
{name:"Watermelon", img:"https://images.pexels.com/photos/1313267/pexels-photo-1313267.jpeg"},
{name:"Papaya", img:"https://images.pexels.com/photos/5945891/pexels-photo-5945891.jpeg"},
{name:"Pineapple", img:"https://images.pexels.com/photos/615705/pexels-photo-615705.jpeg"},
{name:"Grapes", img:"https://images.pexels.com/photos/708777/pexels-photo-708777.jpeg"}
];

let total=0;
let count=0;

const container=document.getElementById("fruitContainer");

fruits.forEach(fruit=>{
container.innerHTML+=`
<div class="card">
<img src="${fruit.img}">
<h3>${fruit.name}</h3>
<button onclick="addToCart('${fruit.name}','${fruit.img}')">
Add ₹30
</button>
</div>
`;
});

function addToCart(name,img){
total+=30;
count++;

document.getElementById("cartItems").innerHTML+=`
<img src="${img}">
<p>${name} Cut Box - ₹30</p>
<hr>
`;

document.getElementById("total").innerText="Total: ₹"+total;
document.getElementById("cartBadge").innerText=count;
}

function toggleCart(){
document.getElementById("cart").classList.toggle("active");
}

</script>

</body>
</html>
