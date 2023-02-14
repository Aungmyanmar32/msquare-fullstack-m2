## MSquare Programing Fullstack Course

### Episode-_19_  Summary for (group 2)

ဒီနေ့သင်တန်းမှာတော့  

### NodeJS CURD 

အကြောင်းပဲ ဆက်လေ့လာသွားပါမယ်။
##
### ပြီးခဲ့တဲ့ သင်ခန်းစာမှာ Register button ကို နှိပ်လိုက်တဲ့အချိန် ဆာဗာကို POST request လှမ်းပို့လိုက်ပြီး ဆာဗာက လက်ခံကာ users Array ထဲ ပေါင်းထည့်လိုက်ကာ users Array ကို response ပြန်လုပ်တဲ့ အထိ လေ့လာခဲ့ပြီးပါပြီး
##
### ဒီ နေ့ သင်ခန်းစာမှာတော့ DELETE method ကို ဆက်ပြီး လေ့လာကြရအောင်။
- ကျနော်တို့ delete button ကို click လုပ်လိုက်တဲ့အခါ deleteUser function ကို ခေါ်ပြီး console.log ထုတ်ခဲ့ကြပါတယ်။
- အခု အဲ့ဒီ function မှာ DELETE method နဲ့ severဆီကို requset လှမ်းပို့ကြရအောင်
```js
//in script.js > deleteUser function

const deleteUser = async (event) => {
  console.log(event.target.id);
 
 //Send delete method request to server
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "DELETE",
    body: JSON.stringify(),
  });
 
};
```
- server.js မှာ  DELETE method နဲ့ severဆီ ၀င်လာတဲ့ requsetကို လက်ခံတဲ့နေရာမှာ code တစ်ချို့ ထပ်ထည့်ပေးပါမယ်
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
      const emailToDelete = "tuntun3@gmail.com";
     const newUsers = users.filter((element) =>  element.email !== emailToDelete)
     response.writeHead(200,{"Content-Type":"application/json"});
     response.write(JSON.stringify(newUsers));
    }
    response.end();
  }
```
> ရှင်းလင်းချက်

- `const emailToDelete = "tuntun3@gmail.com";`
- - users array ထဲရှိ email တစ်ခုကို နမူနာအနေတဲ့ လှမ်းယူလိုက်ပြီး  emailToDelete ဆိုတဲ့ variableမှာ သိမ်းလိုက်ပါတယ်
- `const newUsers = users.filter((element) =>  element.email !== emailToDelete)`
- - နဂိုရှိပြီးသား users array မှာ နမူနာထည့်ထားတဲ့ eamil မပါတဲ့ items တွေကို စစ်ထုတ်လိုက်ပြီး newUsers array မှာ သိမ်းလိုက်ပါတယ်။
- ရလာတဲ့ newUsers array ကို json string အနေနဲ့ front-end ဆီ response ပြန်လိုက်တာဖြစ်ပါတယ်။
- server  ကို start လုပ်ပြီး delete button တစ်ခုကို နှိပ်ကြည့်ကာ browser/network ထဲ မှာ previewသွားကြည့်ပါက နမူနာ email (tuntun3@gmail.com) ပါတဲ့ item ကို ဖျက်ပြီးသား array ကို မြင်ရမှာဖြစ်ပါတယ်။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep30-2-1.png)

##
### Source code for Summary 
- **index.html**
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
    <div class="form">
      <div class="mb-3">
        <label for="age" class="form-label">Name</label>
        <input type="text" class="form-control" id="newUserName" />
      </div>
      <div class="mb-3">
        <label for="age" class="form-label">Email</label>
        <input type="email" class="form-control" id="newUserEmail" />
      </div>
      <div class="mb-3">
        <label for="age" class="form-label">Age</label>
        <input type="number" class="form-control" id="newUserAge" />
      </div>

      <button class="btn btn-success" onclick=" registerNewUser()">
        Register
      </button>
    </div>

    <div id="app"></div>

    <!-- bootstrap js script -->
    <!-- <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-w76AqPfDkMBDXo30jS1Sgez6pr3x5MlQ1ZAGC+nuZB+EYdgRZgiwxhTBTkF7CXvN"
      crossorigin="anonymous"
    ></script> -->

    <script src="script.js"></script>
  </body>
</html>

```
- --
- script.js
```js
const app = document.getElementById("app");

const registerNewUser = async () => {
  const newUserName = document.getElementById("newUserName").value;
  const newUserEmail = document.getElementById("newUserEmail").value;
  const newUserAge = document.getElementById("newUserAge").value;

  const newUser = { name: newUserName, email: newUserEmail, age: newUserAge };
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "POST",
    body: JSON.stringify(newUser),
  });
};

const updateUser = async (event) => {
  const newUser = { name: "Aye Aye", email: "ayeaye4@gmail.com", age: 17 };
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "PUT",
    body: JSON.stringify(newUser),
  });
  const updateUserEmail = event.target.id;
  console.log(updateUserEmail);
};

const deleteUser = async (event) => {
  console.log(event.target.id);

  //Send delete method request to server
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "DELETE",
    body: JSON.stringify(),
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
---
- server.js
```js
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
      let dataFromScript = "";

      request.on("data", (chunk) => {
        dataFromScript += chunk;
      });

      request.on("end", () => {
        const userToAdd = JSON.parse(dataFromScript);
        users.push(userToAdd);
      });
      response.writeHead(200, { "Content-Type": "application/json" });
      response.write(JSON.stringify(users));
    } else if (request.method === "PUT") {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write("<h1>User Updated</h1>");
    } else if (request.method === "DELETE") {
      const emailToDelete = "tuntun3@gmail.com";
      const newUsers = users.filter(
        (element) => element.email !== emailToDelete
      );
      response.writeHead(200, { "Content-Type": "application/json" });
      response.write(JSON.stringify(newUsers));
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
---
- style.css
```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.form {
  max-width: 300px;
  margin: 0 auto;
}
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.usersDiv {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  padding: 0.5rem;
}

.userTag {
  border: 1px soloid brown;
}

```
---
-
