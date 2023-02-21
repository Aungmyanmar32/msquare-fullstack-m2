## MSquare Programing Fullstack Course
### Episode-*34* Summary for (group 2) 

ဒီနေ့သင်တန်းမှာတော့ <br>
### Express 

အကြောင်း ဆက်လေ့လာသွားပါမယ်။
##
### ပြီးခဲ့တဲ့ သင်ခန်းစာမှာ post middleware  ကို သုံးပြီး user အသစ်တစ်ယောက် add ခဲ့ပြီပါပြီး
- ဒါပေမယ့် refresh တစ်ခါလုပ်လိုက်တိုင်း info အကုန် တူညီတဲ့ user တစ်ယောက်ကိုပဲ ထပ် ပေါင်းထည့်ပေးနေပါတယ်။
- တကယ့်လက်တွေ့မှာ email တူတဲ့ user နှစ်ယောက် မရှိတာကြောင့် refresh တစ်ခါ လုပ်တိုင်း ထပ်ထည့်ပေးနေတာက မဖြစ်သင့်တဲ့ error တစ်ခုလို ဖြစ်နေပါတယ်။
- အခုသင်ခန်းစာမှာတော့ sever က users array ထဲမှာ ရှိပြီးသား email နဲ့ user အသစ်ထပ်ပေါင်းထည့်လို့ မရအောင် လုပ်ကြည့်ကြရအောင်။
- server.js ထဲကို သွားပါ
```js
const express = require("express");
const app = express();
const port = 3000;

const users = [
  {
    name: "user1",
    email: "user1@gmail.com",
    age: 23,
  },
  {
    name: "user2",
    email: "user2@gmail.com",
    age: 19,
  },
];

app.use(express.static("public"));
app.use(express.json());

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.post("/users", (req, res) => {
  console.log(req.body);
  const dataFromScript = req.body;

// check and throw error
  const isEmailexit = users.find((user) => user.email === dataFromScript.email);
  if (isEmailexit) {
    
    throw new Error("Email already exit!");
  }
  users.push(dataFromScript);
  res.send(users);
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}!`);
});
```
>ရှင်းလင်းချက်
```js
app.post("/users", (req, res) => {
  console.log(req.body);
  const dataFromScript = req.body;

// check and throw error
  const isEmailexit = users.find((user) => user.email === dataFromScript.email);
  if (isEmailexit) {
    
    throw new Error("Email already exit!");
  }
  users.push(dataFromScript);
  res.send(users);
});
```
- post middleware ကို သုံးပြီး request နဲ့ အတူ ၀င်လာတဲ့ data ကို dataFromScript ထဲ အရင်သိမ်းလိုက်ပါတယ်။
- find method ကို သုံးပြီး ရှိပြီးသား users array ထဲ မှာ dataFromScriptထဲက email ရှိမရှိ ရှာလိုက်ပါတယ်။
- တကယ်လို့ ရှိခဲ့ရင် error တစ်ခု throw လိုက်ပါတယ်။
- မရှိခဲ့ရင်တော့ အောက်က ကုဒ်တွေ ဆက်run ခိုင်းလိုက်တာပါ။
- browser ကို refresh လုပ်ကြည့်တဲ့အခါ find method က true ဖြစ်( **၀င်လာတဲ့ user အသစ်ရဲ့ email က users array ထဲရှိ email နဲ့ တူ** )တဲ့အချိန်  terminal မှာ Email already exit! ဆိုပြီး error ပြပေးမှာဖြစ်ပြီး
- browser console မှာလဲ errorတစ်ခု ပြနေမှာ ဖြစ်ပါတယ်။
##
### params
- params ဆိုတာ request လုပ်တဲ့အခါ သုံးတဲ့ route နောက်က ထည့်ပေးလိုက်တဲ့ အရာကို ဆိုလိုပါတယ်
- နမူနာ
 ```html
  address:port/route/params
  http://localhost:3000/users/1
```
- express မှာ req.params ဆိုပြီး requset ၀င်လာတဲ့ params ကို ဖမ်းလို့ရပါတယ်။
- နမူနာ 
```js
app.delete("/users/:id", (req, res) => {
 console.log(req.params);
 res.end()
});
// output: { id: '1' }
```
-  delete middleware နဲ့ users route ကနေ ၀င်လာတဲ့ request ကို ဖမ်းထားပါတယ်
- users route နောက်မှာ : id ဆိုပြီး param ကိုဖမ်းထားပါတယ်
- အောက်မှာတော့ req.params ဆိုပြီး log ထုတ်ကြည့်ထားပါတယ်။
- postman ကနေ  http://localhost:3000/users/1  ကို သုံးပြီး delete method  ကို ရွေးပြီး request send ကြည့်ပါက
- request နဲ့ အတူပါလာတဲ့ `1` ဆိုတဲ့ params ကို express က route နောက်မှာ ဖမ်းထားတဲ့ id ရဲ့ တန်ဖိုးအဖြစ် သတ်မှတ်လိုက်ပြီး object တစ်ခု အဖြစ် req.params ထဲ ထည့်ပေးလိုက်တာဖြစ်ပါတယ်
- log  ထုတ်ထားတာကို terminal ထဲ ကြည့်တဲ့အခါ `{ id : '1'}` ဆိုပြီး ပြပေးနေမှာဖြစ်ပါတယ်။
- ဒီနေရာမှာ သတိပြုရမှာက params ကို number အနေနဲ့ request ပို့လိုက်ပေမယ့် express မှာ ဖမ်းတဲ့အခါ string ဖြစ်သွားပါတယ်။
- ဆိုလိုတာက  params ကို ဘယ်data type  နဲ့ request ပို့လိုက်လိုက် express က string အနေနဲ့ ပဲ ဖမ်းမှာဖြစ်ပါတယ်။

##
### Express *delete* middleware
- nodeJS သင်ခန်းစာတုန်းကလိုပဲ user တစ်ယောက်ကို express မှာ ဖျက်ထုတ်နည်းကို လေ့လာကြည့်ရအောင်။
### server.js
```js
const express = require("express");
const app = express();
const port = 3000;

const users = [
  {
    id: 1,
    name: "user1",
    email: "user1@gmail.com",
    age: 23,
  },
  {
    id: 2,
    name: "user2",
    email: "user2@gmail.com",
    age: 19,
  },
  {
    id: 3,
    name: "user3",
    email: "user3@gmail.com",
    age: 29,
  },
];

app.use(express.static("public"));
app.use(express.json());

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.post("/users", (req, res) => {
  const dataFromScript = req.body;

  const isEmailexit = users.find((user) => user.email === dataFromScript.email);
  if (isEmailexit) {
    throw new Error("Email already exit!");
  }

  users.push(dataFromScript);
  res.send(users);
});

app.delete("/users/:id", (req, res) => {
  const idToDelete = parseInt(req.params.id, 10);
  const remainUsers = users.filter((user) => user.id !== idToDelete);
  res.send(remainUsers);
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}!`);
});

```
- users array မှာ id key တစ်ခု ထပ်တိုးထားပြီး item (user) သုံးခု ထည့်ပေးထားပါတယ်
- delete middlewareကို အသုံးပြုပြီး users route နဲ့ params ကို ဖမ်းထားပါတယ်။
 `const idToDelete = parseInt(req.params.id, 10);` 
- req.paramsက object တစ်ခု ရလာတာမလို့  **req.paramsထဲက id ရဲ့ value ကို string ကနေ number အဖြစ်ပြောင်းပြီး idToDelete ထဲ သိမ်းလိုက်တာဖြစ်ပါတယ်**
```
 const remainUsers = users.filter((user) => user.id !== idToDelete);
  res.send(remainUsers);
```
- filter method ကို သုံးပြီး params အနေနဲ့ **၀င်လာတဲ့ id နဲ့ users array ထဲက id တူ မတူ စစ်ထုတ်**ပြီး မတူတဲ့ id ပါတဲ့ item တွေကို response လုပ်လိုက်တာဖြစ်ပါတယ်။
- postman ကနေ delete method နဲ့ http://localhost:3000/users/1 ကို request send ကြည့်တဲ့အခါ response body မှာ **request လုပ်လိုက်တဲ့ params နဲ့ တူတဲ့ id ရှိတဲ့ user မပါတဲ့ array တစ်ခု ကို ပြပေးနေတာတွေ့ရမှာဖြစ်ပါတယ်**

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/demid.png)
