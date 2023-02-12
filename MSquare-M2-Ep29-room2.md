## MSquare Programing Fullstack Course

### Episode-_19_  Summary for (group 2)

ဒီနေ့သင်တန်းမှာတော့  

### NodeJS CURD 

အကြောင်းပဲ ဆက်လေ့လာသွားပါမယ်။
##
### ပြီးခဲ့တဲ့ သင်ခန်းစာမှာ button တွေ နှိပ်လိုက်တဲ့အချိန် ဆာဗာကို request လှမ်းပို့လိုက်ပြီး ဆာဗာက လက်ခံကာ response ပြန်လုပ်တဲ့ အထိ လေ့လာခဲ့ပြီးပါပြီး
- ဆက်ပြီးတော့ button တွေ နှိပ်လိုက်တဲ့အချိန်  button နဲ့သက်ဆိုင်တဲ့ user eamil  တွေ ပြနိုင်အောင် လေ့လာကြပါမယ်
- ကျနော်တို့ **script.js** မှာ button တွေရဲ့ id ကို ပေးထားတာမှတ်မိကြမယ်ထင်ပါတယ်
- click event မှာ function ခေါ်တဲ့အခါ parameter တစ်ခု ထည့်ပေးထားတာကိုလဲ သတိထားမိကြမယ်ထင်ပါတယ်။
- ပြီးခဲ့တဲ့ သင်ခန်းစာက script.js ကို အောက်မှာ ပြန်ကြည့်နိုင်ပါတယ်
```js
const app = document.getElementById("app");

const registerNewUser = async () => {
  const newUser = { name: "Aye Aye", email: "ayeaye4@gmail.com", age: 17 };
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "POST",
    body: JSON.stringify(newUser),
  });

  const newUserName = document.getElementById("newUserName").value;
  const newUserEmail = document.getElementById("newUserEmail").value;
  const newUserAge = document.getElementById("newUserAge").value;
  console.log(newUserName, newUserEmail, newUserAge);
};

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
##
### Update နဲ့ Delete Button ကို နှိပ်လိုက်တဲ့အခါ နှိပ်လိုက်တဲ့Buttonရဲ့ id မှာ  users[].emailကို ပေးထားတာမလို့ ထို id ကို လှမ်းခေါ်လိုက်တာနဲ့ သက်ဆိုင်တဲ့ email ကို ရမှာဖြစ်ပါတယ်
- script.js အထဲက updateUser နဲ့ deleteUser function မှာ ထပ်ထည့်ပေးရမှာ ဖြစ်ပါတယ်။
```js
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
  const newUser = { name: "Aye Aye", email: "ayeaye4@gmail.com", age: 17 };
  const url = "http://localhost:3000/users";
  const response = await fetch(url, {
    method: "DELETE",
    body: JSON.stringify(newUser),
  });
  const updateUserEmail = event.target.id;
  console.log(updateUserEmail);
};
```
> ရှင်းလင်းချက်
```js
 const updateUserEmail = event.target.id;
  console.log(updateUserEmail);
```
- နှိပ်လိုက်တဲ့ ခလုတ်ရဲ့ ID ကို လှမ်းယူလိုက်ပြီး  log ထုတ်လိုက်တာဖြစ်ပါတယ်
- Update (or) Delete button တွေကို နှိပ်ကြည့်လိုက်ပါက သက်ဆိုင်ရာ email တွေကို console မှာ ပြပေးမှာ ဖြစ်ပါတယ်။
 ##
 ### Send new user object to server( POST method)
 - script.js မှာ ရှိတဲ့ registerNewUser function မှာ  သွားပြင်ရေးပါမယ်
 ```js
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
}
```
- input tag တွေမှာ ထည့်လိုက်တဲ့ value တွေကို newUserName,newUserEmail,newUserAge ဆိုပြီး သိမ်းထားပါတယ်။
- newUser ဆိုတဲ့ object မှာ အထက်က variable တွေ သက်ဆိုင်ရာ key တွေနဲ့ သိမ်းလိုက်တာပါ။
- ထို newUser object ကို /users end-point(route) မှာ  POST method နဲ့ request လုပ်ပြီး ဆာဗာဆီ လှမ်းပို့လိုက်တာပါ။
##
### request(POST method) နဲ့ ၀င်လာတဲ့ newUser dataကို ဆာဗာမှာ လက်ခံရယူပြီး users array ထဲမှာ new user အနေနဲ့ ပေါင်းထည့်ပါမယ်
- /users route ထဲက POST method နေရာမှာ ကုဒ်ရေးပေးရမှာ ဖြစ်ပါတယ်။
```js
else if (route === "/users") {
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
      response.end()
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
>ရှင်းလင်းချက်
```js
else if (request.method === "POST") {
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
      response.end()
    }
```
- POST method နဲ့ request တစ်ခု ၀င်လာရင်
 `let dataFromScript = "";`
- dataFromScript  ဆိုတဲ့ variable တစ်ခု ကို  သတ်မှတ်လိုက်ပါတယ်။

     **request.on("data", (chunk) => {
            dataFromScript += chunk;
          });**

- request.on method မှာ data တွေ ၀င်လာနေတဲ့အချိန် ရလာတဲ့ chunk တွေကို dataFromScript  ဆိုတဲ့ variable မှာ သွားပေါင်းထည့်ပြီး သိမ်းလိုက်တာပါ

  **request.on("end", () => {
        const userToAdd = JSON.parse(dataFromScript);
        users.push(userToAdd);
      });**
     
  - request.on method မှာ end ဖြစ်တဲ့အခါ   dataFromScript  ဆိုတဲ့ variable မှာ ၀င်လာတဲ့ data တွေ  အကုန် သိမ်းလို့ပြီးသွားပါပြီး။
  - ကျနော်တို့က Json string အနေနဲ့ ပို့လိုက်တာမလို့ ရလာတဲ့ data ကို JS object ပြန်ပြောင်းပြီး userToAdd လို့ သိမ်းလိုက်တာပါ။
  - နောက်ဆုံး ရထားတဲ့ userToAdd ကို server မှာ ရှိနေတဲ့ users array ထဲ ထပ်ပေါင်းထည့်လိုက်တာဖြစ်ပါတယ်

     **response.writeHead(200, { "Content-Type": "application/json" });
      response.write(JSON.stringify(users));
      response.end()**
- user အသစ်ပေါင်းထည့်ပြီးသား array ကို Json string ပြောင်းပြီး response ပြန်လိုက်တာဖြစ်ပါတယ်
- ဆာဗာ ကို start လုပ်ပြီး UI ကနေ user အသစ် register လုပ်ကြည့်ပါက response ပြန်လာတဲ့အထဲမှာ အသစ်ထပ်ထည့်လိုက်တဲ့ user ပါ ,ပါလာတာကို မြင်ရမှာပါ။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep291.png)
