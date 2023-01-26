
## MSquare Programing Fullstack Course
### Episode-*18* 
### Summary For `Room(1)` intermediate Class
##
### Create registration form UI with `bootstrap` 
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/room1-1.jpg)
> Example code
### Html
```html
<!DOCTYPE  html>

<html  lang="en">
<head>
 <meta  charset="UTF-8"  />
 <meta  http-equiv="X-UA-Compatible"  content="IE=edge"  />
 <meta  name="viewport"  content="width=device-width, initial- scale=1.0"  />

 <link
href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css"
rel="stylesheet"
integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD"
crossorigin="anonymous"
/>

 <link  rel="stylesheet"  href="style.css"  />
 <title>Document</title>
</head>

<body>

 <div  class="container d-flex justify-content-center">
  <div  class="registerForm p-2 d-flex flex-column w-50">
   <label  for="exampleInputEmail1">Name</label>
   <input
type="text"
class="form-control"
id="exampleInputEmail1"
placeholder="Your Name"
/>
   <label  for="exampleInputEmail1">Email</label>
   <input
type="text"
class="form-control"
id="exampleInputEmail1"
placeholder="Email"
/>
   <label  for="exampleInputEmail1">Password</label>
   <input
type="password"
class="form-control"
id="exampleInputEmail1"
placeholder="password"
/>
   <button  type="button"  class="btn btn-primary">Register</button>
  </div>
 </div>
 <script  src="script.js"></script>
 <script
src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"
integrity="sha384-w76AqPfDkMBDXo30jS1Sgez6pr3x5MlQ1ZAGC+nuZB+EYdgRZgiwxhTBTkF7CXvN"
crossorigin="anonymous"></script>
</body>

</html>
```
### CSS
```css
.container {
max-width: 1024px;
height: 80vh;
}
.registerForm  button,
.registerForm  input {
margin: 2px  auto;
font-size: 0.6rem;
}

  

.registerForm  label {
font-size: 0.6rem;
}
```
### Server.js
```javascript
const  fs = require("fs");
const  http = require("http");

const  server = http.createServer((req, res) => {
 if (req.url === "/") {
   fs.readFile("index.html", (err, data) => {
   res.writeHead(200, { "Content-Type":  "text/html" });
   res.write(data);
  return  res.end();
 });
 }else  if (req.url === "/script.js") {
   fs.readFile("script.js", (err, data) => {
   res.writeHead(200, { "Content-Type":  "text/javascript" });
   res.write(data);
  return  res.end();
 });
 }else  if (req.url === "/style.css") {
   fs.readFile("style.css", (err, data) => {
   res.writeHead(200, { "Content-Type":  "text/css" });
   res.write(data);
   return  res.end();
 });

 }else {
   res.writeHead(404, { "Content-Type":  "text/plain" });
   res.write("404 | Page Not Found!");
   return  res.end();
 }
});

  

server.listen(3000, () => {
console.log("Server started: Listening on port 3000");
});
```
##
### Get user name from Server and append on index.html 
- server.js မှာ allUsers ဆိုပြီး arry တစ်ခု လုပ်ပါမယ်။
```javascript
const  allUsers = [
{
id:  1,
name:  "Aung Aung",
email:  "aung1@web.de",
},
{
id:  2,
name:  "Ko Ko",
email:  "koko2@web.de",
},
{
id:  3,
name:  "Bo Bo",
email:  "bobo3@web.de",
},
];
```
- လုပ်ထားတဲ့ array ကို  server ကနေ route တစ်ခုနဲ့ response လုပ်ပါမယ်
#### server.js
```js
else  if (req.url === "/allUsers") {
res.writeHead(200, {"Content-Type":"application/json"});
res.write(JSON.stringify(allUsers));
return res.end();
}
```
- server ကနေ response လုပ်ထားတဲ့ data ကို script.js(frontend) ကနေ fetch နဲ့ လှမ်းယူပြီး index page မှာ ပြပေးပါမယ်။

```html
//Add to html
<div  class="usersInfo text-center"></div>

//CSS
.user {
 border: 1px  solid  black;
 width: 70%;
 margin: 0.3rem  auto;
}

.user  p {
 color: blueviolet;
}
```
### script.js
```javascript
const  usersInfoTag = document.querySelector(".usersInfo");
  
const  showOnUI = (name, email) => {
 const  userDiv = document.createElement("div");
 userDiv.classList.add("user");
 userDiv.innerHTML = `<h2>Welcome ${name}.</h2>
 <p>Your email is ${email} <p>`; 
 usersInfoTag.append(userDiv);
};

const  getUsersFromServer = async () => {
 const  url = "http://localhost:3000/allUsers";
 const  response = await  fetch(url);
 const  data = await  response.json();

 for (let  i = 0; i < data.length; i++) {
  let  userName = data[i].name;
  let  userEmail = data[i].email;
  showOnUI(userName, userEmail);
 }
};

getUsersFromServer();
```
### result
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/room1-2.jpg)
##
### Post data from front-end to server
- index.html ထဲမှာ လုပ်ထားတဲ့ register form ကနေ ထည့်လိုက်တဲ့ data(value)တွေကို လှမ်းယူဖို့ အတွက် html file ထဲမှာ class name ပေးပြီး  change Event ကို သုံးကာ script.js မှာ ရေးပါမယ်။
### Index.html
```html
<label  for="exampleInputEmail1">Name</label>
<input
type="text"
class="form-control newUserName"<-- aded new class -->
id="exampleInputEmail1"
placeholder="Your Name"
/>

  

<label  for="exampleInputEmail1">Email</label>
<input
type="text"
class="form-control newUserEmail"<-- aded new class -->
id="exampleInputEmail1"
placeholder="Email"
/>
```
### script.js
```javascript
//Get input tag
const inputedName = document.querySelector(".newUserName");
const inputedEmail = document.querySelector(".newUserEmail");

//define new user info
let newUserName;
let newUserEmail;
let newUserobject;

//get value from input
inputedName.addEventListener("change", (e) => {
newUserName = e.target.value.toString();
});

inputedEmail.addEventListener("change", (e) => {
newUserEmail = e.target.value.toString();
});
```
- ရလာတဲ့ value တွေကို  server ဆီ ပို့ရန် 
1. html က button မှာ onclick =function()   လုပ်ရပါမယ်
2. ထည့်ပေးလိုက်တဲ့ function ကို script.js မှာ define  လုပ်ပေးရမှာပါ။
3. ထို  function ထဲမှာ `fetch(url,{metoh: "POST"})` ကို အသုံးပြုရပါမယ်။
### html
```html
<button
type="button"
class="btn btn-primary"
onclick="registerNewUser()"> <-- added click handaler -->
Register
</button>
```
### script.js
```js
const  registerNewUser = async () => {
newUserobject = {
name:  newUserName,
email:  newUserEmail,
};
  
//check name and email is not empty
if (newUserName || newUserEmail) {
//Post data to server
const response = await fetch("http://localhost:3000/allUsers", {
method:  "POST",
body:  JSON.stringify(newUserobject),
});
```
##
### receive data from front-end 
- front-end က ပို့လာတဲ့ data တွေကို server က `/allusers` route မှာ လက်ခံရယူရန်
1. ၀င်လာတဲ့ request method က "GET" လား "POST"လား စစ်ဆေးရပါမယ်
2. "GET" method ဆိုရင်တော့ နဂိုရှိပြီးသား allUsers array ကိုပဲ response  လုပ်မှာဖြစ်ပြီး
3. "POST" method ဆိုရင်တော့ ရလာတဲ့ data ကို နဂိုရှိပြီးသား allUsers array မှာ ပေါင်းထည့်(push)ပြီး update  ဖြစ်လာတဲ့ allUsers array ကို response လုပ်ပေးမှာဖြစ်ပါတယ်။
### server.js
```js
else  if (req.url === "/allUsers") {
const  method = req.method;

if (method === "GET") {
//Get method
res.writeHead(200, { "Content-Type":  "application/json" });
res.write(JSON.stringify(allUsers));
return  res.end();
} else  if (method === "POST") {

//post method
//get data from front-end
let  newData = "";
req.on("data", (chunk) => {
newData += chunk;
}); 
req.on("end", () => {
//push new-data to allUsers array
allUsers.push(JSON.parse(newData));

//response updated allUsers array to front-end
res.writeHead(200, { "Content-Type":  "application/json" });
res.write(JSON.stringify(allUsers));
return  res.end();
});
}
}
```
##
### Get updated user array from server and show new user info 
- server ကနေ ပြန်ရလာတဲ့ update ဖြစ်တဲ့ array ကို လက်ခံပြီး အသစ်ထည့်ပေးလိုက်တဲ့ user info ကို
html ထဲ က div အထဲမှာ ထပ်ပြပေးနိုင်အောင်လုပ်ပါမယ်
1. register ခလုတ်ကို နှိပ်လိုက်တာနဲ့ တစ်ခါတည်း ပို့လိုက်တဲ့ new user ကို ပြချင်တာမလို့
`registerNewUser` function ထဲမှာပဲ ဆက်ရေးပါမယ်။
### script.js
```js
const  registerNewUser = async () => {
newUserobject = {
name:  newUserName,
email:  newUserEmail,
};

//check name and email is not empty
if (newUserName || newUserEmail) {
//Post data to server
const  response = await  fetch("http://localhost:3000/allUsers", {
method:  "POST",
body:  JSON.stringify(newUserobject),
});

//appen new user info to front end 
const  data = await  response.json();
let  userName = data[data.length - 1].name;
let  userEmail = data[data.length - 1].email;
await  showOnUI(userName, userEmail);
}
};
```
### result
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/room1-3.jpg)

##
### try this
အခုကျနော်တို့ ရေးထားသလောက် အဆင်ပြေနေတယ်လို့ ထင်ရပေမယ့် 
- register button နှိပ်လိုက်တာနဲ့ new user info ပြပေးနေသော်လည်း
button ကို ထပ်နှိပ်ကြည့်ပါက နောက်ဆုံး user info ကို ထပ်ပေါင်းထည့် ပြပေးနေတဲ့ error ရှိနေပါတယ်
- ထို error လေးကို ရှင်းကြည့်ကြပါ။
- ဒီ summary မှာ ရေးထားတဲ့ source ကုဒ်ကို [ဒီမှာနှိပ်ပြီး](https://github.com/Aungmyanmar32/episode19-source-code)ကြည့်ရှုနိုင်ပါတယ်။ အထက်ပါ errorကိုလဲ 
ကျနော့နည်း ကျနော့ဟန် နဲ့ ဖြေရှင်းထားပါတယ်
