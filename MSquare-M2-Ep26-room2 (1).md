## MSquare Programing Fullstack Course
### Episode-*19* Summary for (group 2) 

ဒီနေ့သင်တန်းမှာတော့ <br>
### server က data တွေကို UI မှာ ပြသခြင်း
### POST method ဖြင့် request လုပ်ခြင်း
### POST method ကို responseလုပ်ခြင်း
အကြောင်း တွေ လေ့လာသွားပါမယ်။
##
### server က data တွေကို UI မှာ ပြသခြင်း
- ပြီးခဲ့တဲ့ သင်ခန်းစာမှာ ဆာဗာက  dataတွေကို ရယူပြီး console log ထုတ်ခဲ့ ကြပါတယ်။
- ဒီနေ့ သင်တန်းမှာတော့ ရလာတဲ့ data တွေကို browser မှာ ပြပေးကြရအောင်
```html
// index.html

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="style.css" />
    <title>Node Route</title>
  </head>
  <body>
    <div id="app"></div>

    <script src="script.js"></script>
  </body>
</html>
```
- index.html မှာ  app လို့ ID ပေးထားတဲ့ div တစ်ခု ထပ်ထည့်ထားပါတယ်
```js
// script.js

const app = document.getElementById("app");

// UI function
const createUserElement = (users) => {
  for (let i = 0; i < users.length; i++) {
    const userTag = document.createElement("div");
    userTag.style.margin = "10px";
    userTag.innerHTML = `
    <input type="text" value="${users[i].name}" />
    <input type="text" value="${users[i].age}" />
    <input type="text" value="${users[i].email}"  disabled/>
    <button onclick = "updateUser()">Update</button>
    `;
    app.append(userTag);
  }
//make empty user input for new user
  const createUser = document.createElement("div");
  createUser.style.margin = "10px";
  createUser.innerHTML = `
  <input type="text" value="" />
  <input type="text" value="" />
  <input type="text" value="" />
  <button onclick = "createNewUser()">Create</button>
  `;
  app.append(createUser);
};

//fetch data from server
const fetchData = async () => {
  // get data from server
  const url = "http://localhost:3000/users";
  const response = await fetch(url);
  const data = await response.json();

//call UI function
  createUserElement(data);
};

fetchData();


```
> ရှင်းလင်းချက်
> 

    const app = document.getElementById("app");
- index.html ထဲက app div ကို လှမ်းယူလိုက်တာပါ
```js
const createUserElement = (users) => {
  for (let i = 0; i < users.length; i++) {
    const userTag = document.createElement("div");
    userTag.style.margin = "10px";
    userTag.innerHTML = `
    <input type="text" value="${users[i].name}" />
    <input type="text" value="${users[i].age}" />
    <input type="text" value="${users[i].email}"  disabled/>
    <button onclick = "updateUser()">Update</button>
    `;
    app.append(userTag);
  }
```
- createUserElement function တစ်ခု သတ်မှတ်လိုက်ပြီး
- userTag div တစ်ခု create လုပ်ပါတယ်
- margin 10px ထပ်ပေးပါမယ်
-  userTag.innerHTML မှာ input tag သုံးခုနဲ့ button  တစ်ခု ထပ်လုပ်ထားပါတယ်
- ပထမ inputရဲ့ value ကို server မှ ရလာမယ့် users array ထဲက name ရဲ့ value အဖြစ်သတ်မှတ်လိုက်ပါတယ်
- ဒုတိယ inputရဲ့ value ကို server မှ ရလာမယ့် users array ထဲ age ရဲ့ value အဖြစ်သတ်မှတ်လိုက်ပါတယ်
- တတိယ inputရဲ့ value ကို server မှ ရလာမယ့် users array ထဲက email ရဲ့ value အဖြစ်သတ်မှတ်လိုက်ပါတယ်
- button မှာ click event ဖမ်းထားပြီး click တဲ့အခါ updateUser() ကို လှမ်းခေါ်ရန် သတ်မှတ်ထားပါတယ်
- userTag ကို html က လှမ်းယူထားတဲ့ appTag ထဲမှာ append လုပ်ထားပါတယ်
```js
const createUser = document.createElement("div");
  createUser.style.margin = "10px";
  createUser.innerHTML = `
  <input type="text" value="" />
  <input type="text" value="" />
  <input type="text" value="" />
  <button onclick = "createNewUser()">Create</button>
  `;
  app.append(createUser);
  
```
- for loop အပြင်မှာ  နောက်ထပ် createUser div တစ်ခု create လုပ်ထားပါတယ်
- createUser .innerHTML မှာ input tag သုံးခုနဲ့ button  တစ်ခု ထပ်လုပ်ထားပါတယ်
- input သုံးခုစလုံးရဲ့ value ကို empty string ပဲ ထည့်ပေးထားပါတယ်
-  button မှာ click event ဖမ်းထားပြီး click တဲ့အခါ createNewUser()ကို လှမ်းခေါ်ရန် သတ်မှတ်ထားပါတယ်
- node server ကို run လိုက်တဲ့အခါမှာတော့ အခုလိုမြင်ရမှာ ဖြစ်ပါတယ်။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/nr23.png)
##
### POST method ဖြင့် request လုပ်ခြင်း
```js
// script.js
const app = document.getElementById("app");

const createNewUser = async () => {
  const newUser = { name: "Aye Aye", email: "ayeaye4@gmail.com", age: 17 };
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "POST",
    body: JSON.stringify(newUser),
  });
};

const createUserElement = (users) => {
  for (let i = 0; i < users.length; i++) {
    const userTag = document.createElement("div");
    userTag.style.margin = "10px";
    userTag.innerHTML = `
    <input type="text" value="${users[i].name}" />
    <input type="text" value="${users[i].age}" />
    <input type="text" value="${users[i].email}"  disabled/>
    <button onclick = "updateUser()">Update</button>
    `;
    app.append(userTag);
  }

  const createUser = document.createElement("div");
  createUser.style.margin = "10px";
  createUser.innerHTML = `
  <input type="text" value="" />
  <input type="text" value="" />
  <input type="text" value="" />
  <button onclick = "createNewUser()">Create</button>
  `;
  app.append(createUser);
};
const fetchData = async () => {
  // get data from server
  const url = "http://localhost:3000/users";
  const response = await fetch(url);
  const data = await response.json();
  createUserElement(data);
};

fetchData();

```
>ရှင်းလင်းချက်
```js
const createNewUser = async () => {
  const newUser = { name: "Aye Aye", email: "ayeaye4@gmail.com", age: 17 };
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "POST",
    body: JSON.stringify(newUser),
  });
};
```
- create button ကို နှိပ်လိုက်တဲ့အခါ ခေါ်သုံးမယ့် createNewUser function ကို သတ်မှတ်လိုက်တာဖြစ်ပါတယ်
- newUser ဆိုတဲ့ object နမူနာတစ်ခု လုပ်ထားပါတယ်
- request လုပ်မယ့် route ကို url အဖြစ် သိမ်းလိုက်တာပါ
- fetch နဲ့ ထို url ကို သုံးပြီး request လုပ်ပါမယ်
- ဒီတစ်တော့ POST method နဲ့ request လုပ်မှာမလို့ fetch မှာ url ထည့်အပြီး object တစ်ခုထပ်ထည့်ပါတယ်
- ထို object မှာ request method က POST ဖြစ်တဲ့အကြောင်း server ကို အသိပေးလိုက်ပြီ
- newUser ဆိုတဲ့ object နမူနာကို json string ပြောင်းပြီ ဆာဗာဆီ  တစ်ခါတည်း ထည့်ပေးလိုက်တာပါ။
### serverဆီ POST methodနဲ့ request လုပ်ဖို့ ပြင်ဆင်ထားပြီးပါပြီး
##
### server.js မှာ POST method  နဲ့ /users route ကနေ request လုပ်လာတဲ့အခါ reponse ပြန်လုပ်ပေးဖို့ ပြင်ဆင်ကြရအောင်
```js
//server.js
const http = require("http");
const fs = require("fs");

const users = [
  { name: "Aung Aung", email: "aungaung1@gmail.com", age: 23 },
  { name: "Kyaw Kyaw", email: "kyawkyaw2@gmail.com", age: 18 },
  { name: "Tun Tun", email: "tuntun3@gmail.com", age: 25 },
];

const server = http.createServer((request, response) => {
  const method = request.method;
  const route = request.url;
  if (route === "/") {
    fs.readFile("./index.html", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write(data);
      response.end();
    });
  } else if (route === "/script.js") {
    fs.readFile("./script.js", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/javascript" });
      response.write(data);
      response.end();
    });
  } else if (route === "/style.css") {
    fs.readFile("./style.css", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/css" });
      response.write(data);
      response.end();
    });
  } else if (route === "/users") {
    if (request.method === "GET") {
      response.writeHead(200, { "Content-Type": "application/json" });
      response.write(JSON.stringify(users));
    } else if (request.method === "POST") {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write("<h1>User created</h1>");
    }
    response.end();
  } else {
    response.writeHead(200, { "Content-Type": "text/plain" });
    response.write(`404 | Page not found!`);
    response.end();
  }
});

server.listen(3000, () => {
  console.log("Server Runnig on Port 3000");
});
```
- အပေါ်က ကုဒ်တွေက အရင်သင်ခန်းစာမှာ ရှင်းပြထားပြီးမလို့ အသစ်ထည့်လိုက်တဲ့ /users route ကိုပဲ ထပ်ရှင်းသွားပေးမှာ ဖြစ်ပါတယ်။ နားမလည်ဘူးဆိုပါက episode 25 summary မှာ ပြန်လည်ဖတ်ရှုနိုင်ပါတယ်
```js
 else if (route === "/users") {
    if (request.method === "GET") {
      response.writeHead(200, { "Content-Type": "application/json" });
      response.write(JSON.stringify(users));
    } else if (request.method === "POST") {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write("<h1>User created</h1>");
    }
    response.end();
  }
```
- /users route နဲ့ request ၀င်လာတဲ့အခါ method ကို ထပ်စစ်ပါမယ်
- GET method နဲ့ဆို  server ရှိ users array  ကို response လုပ်ပေးမှာဖြစ်ပြီး
- POST method ဆိုရင်တော့ လက်ခံရရှိကြောင်း  response ပြန်ထားတာပါ
- server  ကို start လိုက်ပြီး browser မှာ localhost:3000 ဆီသွားပါ
- inspect / Network ကိုဖွင့်ထားပြီး create button ကို နှိပ်ပေးကြည့်ပါ။
- Network မှာ request ပြပေးမှာ ဖြစ်ပြီး အောက်ဆုံးမှာ ပေါ်လာတဲ့ users ကို နှိပ်ကြည့်ပါ
- Network header မှာ method ကို စစ်ဆေးနိုင်ပြီး previeမှာ response ကို ကြည့်နိုင်ပါတယ်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/nr21.png)
