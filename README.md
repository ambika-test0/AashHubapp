<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>AashHub</title>

<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Arial;}
body{
background:linear-gradient(135deg,#1e3a8a,#2563eb);
color:white;
min-height:100vh;
}
header{
padding:15px;
background:rgba(0,0,0,.3);
display:flex;
justify-content:space-between;
align-items:center;
}
.logo{
font-size:28px;
font-weight:bold;
}
nav button{
margin:5px;
padding:10px 15px;
border:none;
border-radius:20px;
cursor:pointer;
}
.page{
display:none;
padding:20px;
}
.active{
display:block;
}
.card{
background:rgba(255,255,255,.15);
padding:15px;
border-radius:15px;
margin-top:15px;
}
input,textarea{
width:100%;
padding:10px;
margin:10px 0;
border:none;
border-radius:10px;
}
.post{
background:white;
color:black;
padding:15px;
border-radius:15px;
margin-top:15px;
}
.like{
background:#2563eb;
color:white;
padding:8px 15px;
border:none;
border-radius:10px;
}
img{
max-width:100%;
border-radius:15px;
}
</style>
</head>

<body>

<header>
<div class="logo">AashHub</div>
<nav>
<button onclick="show('home')">Home</button>
<button onclick="show('login')">Login</button>
<button onclick="show('profile')">Profile</button>
<button onclick="show('upload')">Upload</button>
<button onclick="darkMode()">Dark</button>
</nav>
</header>

<div class="page active" id="home">
<h2>Home Feed</h2>

<input type="text" id="search" placeholder="Search..." onkeyup="searchPost()">

<div class="post">
<h3>AashHub Welcome Post</h3>
<p>Welcome to AashHub Social Platform.</p>
<button class="like" onclick="like(this)">❤️ Like 0</button>
</div>

<div class="post">
<h3>Nature</h3>
<p>Beautiful green world.</p>
<button class="like" onclick="like(this)">❤️ Like 0</button>
</div>
</div>

<div class="page" id="login">
<div class="card">
<h2>Login</h2>
<input type="text" placeholder="Username">
<input type="password" placeholder="Password">
<button onclick="alert('Login Successful')">Login</button>
</div>
</div>

<div class="page" id="profile">
<div class="card">
<h2>Profile</h2>
<p>Name: User</p>
<p>Followers: 100</p>
<p>Posts: 5</p>
</div>
</div>

<div class="page" id="upload">
<div class="card">
<h2>Upload Photo</h2>
<input type="file" id="file">
<img id="preview">
</div>
</div>

<script>

function show(id){
document.querySelectorAll('.page')
.forEach(p=>p.classList.remove('active'));
document.getElementById(id).classList.add('active');
}

function darkMode(){
document.body.style.background="#111";
}

function like(btn){
let n=parseInt(btn.dataset.like||0);
n++;
btn.dataset.like=n;
btn.innerHTML="❤️ Like "+n;
}

document.getElementById("file").addEventListener("change",function(e){
let reader=new FileReader();
reader.onload=function(){
document.getElementById("preview").src=reader.result;
}
reader.readAsDataURL(e.target.files[0]);
});

function searchPost(){
let value=document.getElementById("search").value.toLowerCase();
let posts=document.querySelectorAll(".post");

posts.forEach(post=>{
if(post.innerText.toLowerCase().includes(value)){
post.style.display="block";
}else{
post.style.display="none";
}
});
}

</script>

</body>
</html>
