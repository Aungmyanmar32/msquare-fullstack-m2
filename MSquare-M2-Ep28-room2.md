## MSquare Programing Fullstack Course

### Episode-_28_  Summary for (group 2)

ဒီနေ့သင်တန်းမှာတော့  

### Bootstrap ကို အသုံးပြုပြီး UI တစ်ခု တည်ဆောက်ခြင်း
### User input မှ data ကို ဖမ်းယူခြင်း

အကြောင်း တွေ လေ့လာသွားပါမယ်။
##
### bootstrap CDN link ချိတ်ဆက်အသုံးပြုခြင်း
- bootstrap ကို အသုံးပြုနိုင်ရန် html ဖိုင်ထဲမှာ CDN link ချိတ်ဆက်ပေးရပါမယ်
- getbootstrap.com သွားပါ
- ### Include via CDN အောက်က link နှစ်ခုကို copy လုပ်ပြီး html ထဲမှာ ချိတ်ပေးလိုက်ပါ
- လိုအပ်တဲ့ link ချိတ်ပြီးပြီဆိုရင် form တစ်ခု လုပ်ပါမယ်
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    
    <!-- bootstrap CDN css -->
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-GLhlTQ8iRABdZLl6O3oVMWSktQOp6b7In1Zl3/Jr59b6EGGoI1aFkw7cmDA6j6gD"
      crossorigin="anonymous"
    />
    
    <link rel="stylesheet" href="style.css" />
    <title>Node Route</title>
  </head>
  <body>
    <form>
      <div class="mb-3">
        <label for="age" class="form-label">Name</label>
        <input type="text" class="form-control" id="newUserName"/>
      </div>
      <div class="mb-3">
        <label for="age" class="form-label">Email</label>
        <input type="email" class="form-control" id="newUserEmail"/>
      </div>
      <div class="mb-3">
        <label for="age" class="form-label">Age</label>
        <input type="number" class="form-control" id="newUserAge"/>
      </div>

      <button class="btn btn-success" onclick="registerNewUser()">
        Register
      </button>
    </form>

    <div id="app"></div>

    <script src="script.js"></script>
    
    <!-- bootstrap js script -->
    <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-w76AqPfDkMBDXo30jS1Sgez6pr3x5MlQ1ZAGC+nuZB+EYdgRZgiwxhTBTkF7CXvN"
      crossorigin="anonymous"
    ></script>
  </body>
</html>

```
- bootstrap ကို အသုံးပြုပြီး form တစ်ခု လုပ်ထားပါတယ်။
- form ထဲမှာ input div သုံးခုနဲ့ button တစ်ခု လုပ်ထားပါတယ်။
- input tag  တွေမှာ 
1. **Name** အတွက် input မှာ **id="newUserName"** ပေးထားပါတယ်
2. **Email** အတွက် input မှာ **id="newUserEmail"** ပေးထားပါတယ်
3. **Age** အတွက် input မှာ **id="newUseAge"** ပေးထားပါတယ်
- `Register` button မှာ click event တစ်ခု ဖမ်းထားပြီး **registerNewUser** function ကို ခေါ်ထားပါတယ်
- `Register` button ကို click လုပ်တဲ့အခါ အထက်က input တွေမှာ ရေးထည့်ပေးလိုက်တဲ့ value တွေကို log  ထုတ်ပြီး ပြပေးနိုင်အောင် **registerNewUser** function မှာ ရေးမှာပါ။
- အဲ့ဒီ **registerNewUser** function ကို script.js ထဲမှာ define လုပ်ကြရအောင် ။

##
```js
// script.js
const app = document.getElementById("app");

const registerNewUser = async () => {
  const newUserName = document.getElementById("newUserName").value;
  const newUserEmail = document.getElementById("newUserEmail").value;
  const newUserAge = document.getElementById("newUserAge").value;
  
  console.log(newUserName, newUserEmail, newUserAge);
};

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
> ရှင်းလင်းချက်
```js
const registerNewUser = async () => {
  const newUserName = document.getElementById("newUserName").value;
  const newUserEmail = document.getElementById("newUserEmail").value;
  const newUserAge = document.getElementById("newUserAge").value;
  
  console.log(newUserName, newUserEmail, newUserAge);
};
```
- input tag တွေထဲက value တွေကို လှမ်းယူလိုက်ပြီး console log ထုတ်လိုက်တာပါ။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep281.png)
##
### ခု server က ရလာတဲ့ data ကို ပြပေးတဲ့ UI ကို အနည်းငယ်ပြင်ပါမယ်
- input tag တွေနဲ့ ပြထားတာတွေကို span tag အနေနဲ့ ပြောင်းပြီး ပြပေးမှာဖြစ်သလို button နောက်တစ်ခုလဲ ထပ်ထည့်လိုက်မှာ ဖြစ်ပါတယ်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep282.png)
- createUserElement ဆိုတဲ့ function မှာ ပြင်ရမှာ ဖြစ်ပါတယ်
```js
// script.js
const app = document.getElementById("app");

const registerNewUser = async () => {
  const newUserName = document.getElementById("newUserName").value;
  const newUserEmail = document.getElementById("newUserEmail").value;
  const newUserAge = document.getElementById("newUserAge").value;
  
  console.log(newUserName, newUserEmail, newUserAge);
};

const createNewUser = async () => {
  const newUser = { name: "Aye Aye", email: "ayeaye4@gmail.com", age: 17 };
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "POST",
    body: JSON.stringify(newUser),
  });
};

const createUserElement = (users) => {
  const usersDiv = document.createElement("div");
  usersDiv.classList.add("usersDiv");
  for (let i = 0; i < users.length; i++) {
    const userTag = document.createElement("div");
    userTag.style.margin = "10px";
    userTag.innerHTML = `
    <span >${users[i].name} </span>
    <span >${users[i].age} </span>
    <span >${users[i].email}</span>
    <button id ="${users[i].email}" class="btn btn-primary" onclick = "updateUser(event)">Update</button>
    <button id ="${users[i].email}" class="btn btn-danger" onclick = "deleteUser(event)">Delete</button>
    `;
    usersDiv.append(userTag);
  }
  app.append(usersDiv);
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
> ရှင်းလင်းချက်
```js
const createUserElement = (users) => {
  const usersDiv = document.createElement("div");
  usersDiv.classList.add("usersDiv");
  for (let i = 0; i < users.length; i++) {
    const userTag = document.createElement("div");
    userTag.style.margin = "10px";
    userTag.innerHTML = `
    <span >${users[i].name} </span>
    <span >${users[i].age} </span>
    <span >${users[i].email}</span>
    <button id ="${users[i].email}" class="btn btn-primary" onclick = "updateUser(event)">Update</button>
    <button id ="${users[i].email}" class="btn btn-danger" onclick = "deleteUser(event)">Delete</button>
    `;
    usersDiv.append(userTag);
  }
  app.append(usersDiv);
};
```
- for loop ထဲမှာ server ကရလာတဲ့ data တွေကို span tag ထဲမှာ ထည့်ပြီး ပြပေးထားပါတယ်
- button နှစ်ခု လုပ်ထားပြီး တစ်ခုကို Update /  တစ်ခုကို Delete လို့ လုပ်ထားပါတယ်
- Update button ရဲ့ onclick မှာ updateUser function ကို ခေါ်ထားပါတယ်
- Delete button ရဲ့ onclick မှာ deleteUser function ကို ခေါ်ထားပါတယ်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep283.png)
##
### အခု update/delete button တွေကို click  တဲ့ အခါ ဆာဗာကို request ပို့ပြီး ဆာဗာဘက်ကနေ လက်ခံရရှိကြောင်း response ပြန်လာအောင် လုပ်ကြည့်ရအောင်
- အရင်ဆုံး button တွေအတွက် click event function ကို စလုပ်ပါမယ်
- script.js မှာ အောက်က function နှစ်ခု ထပ်လုပ်ထားပါတယ်
```js
const updateUser = async (event) => {
  const newUser = { name: "Aye Aye", email: "ayeaye4@gmail.com", age: 17 };
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "PUT",
    body: JSON.stringify(newUser),
  });
};

const deleteUser = async (event) => {
  const newUser = { name: "Aye Aye", email: "ayeaye4@gmail.com", age: 17 };
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "DELETE",
    body: JSON.stringify(newUser),
  });
};
```
- /users route နဲ့ ဆာဗာဆီ request လုပ်ထားတာဖြစ်ပါတယ်.
- updateUser function  မှာတော့  PUT method ကို သုံးထားပြီး
- deleteUser function မှာတော့ DELETE method ကို သုံးထားပါတယ်
##
### server.js မှာလဲ အဆိုပါ methodတွေနဲ့ requestကို လက်ခံဖို့ ပြင်ဆင်ရပါမယ်
```js
else if (route === "/users") {
    if (request.method === "GET") {
      response.writeHead(200, { "Content-Type": "application/json" });
      response.write(JSON.stringify(users));
    } else if (request.method === "POST") {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write("<h1>User created</h1>");
    } else if (request.method === "PUT") {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write("<h1>User Updated</h1>");
    } else if (request.method === "DELETE") {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write("<h1>User deleted</h1>");
    }
    response.end();
  }
```
- PUT method နဲ့ ၀င်လာရင် User Updated ဆိုတဲ့ head tag တစ်ခု response လုပ်ပေးလိုက်တာပါ
- DELETE method နဲ့ ၀င်လာရင် User Deleted ဆိုတဲ့ head tag တစ်ခု response လုပ်ပေးလိုက်တာပါ

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep284.png)
