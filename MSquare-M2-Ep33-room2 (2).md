## MSquare Programing Fullstack Course
### Episode-*19* Summary for (group 2) 

ဒီနေ့သင်တန်းမှာတော့ <br>
### Express middleware
### nodemon module
အကြောင်း လေ့လာသွားပါမယ်။
##

### Express 
- Express ဆိုတာ nodeကို ပိုမိုလွယ်ကူစွာ အသုံးပြုနိုင်အောင် ပြုလုပ်ပေးတဲ့ အရာတစ်ခုဖြစ်ပါတယ်။
- express မှာ **middleware** တွေ အသုံးပြုပြီး request တွေ response တွေကို စီမံခန့်ခွဲလို့ရပါတယ်။

##
### express middleware
- middleware ဆိုတာ function တစ်မျိုး ဖြစ်ပါတယ်။
- express မှာ middleware ( ၅ ) မျိုး ရှိပါတယ်။
-   [Application-level middleware](https://expressjs.com/en/guide/using-middleware.html#middleware.application)
-   [Router-level middleware](https://expressjs.com/en/guide/using-middleware.html#middleware.router)
-   [Error-handling middleware](https://expressjs.com/en/guide/using-middleware.html#middleware.error-handling)
-   [Built-in middleware](https://expressjs.com/en/guide/using-middleware.html#middleware.built-in)
-   [Third-party middleware](https://expressjs.com/en/guide/using-middleware.html#middleware.third-party)
### Syntex of application level middleware
```js
express().middleware( route , callback)

//example
const  express = require("express");
const  app = express();

app.get("/", (req, res) => {
 res.send("Hello World!");
});
```
##
### Create Express server
- server.js ဖိုင်တစ်ခု လုပ်ပါ။
```js
//server.js
const express = require("express");
const app = express();
const port = 3000;

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}!`);
});
```
- express ကို လှမ်းယူထားပြီး app ကို express() အဖြစ် သတ်မှတ်ကာ server create လုပ်ပြီး port 3000 မှာ listen ထားပါတယ်။
- အထဲမှာ get middleware ကို အသုံးပြုပြီး root route နဲ့ request လုပ်လာရင် Hello World! ကို response လုပ်ထားတာဖြစ်ပါတယ်။
- express server ကို start  လုပ်ဖို့ package.json  ထဲက script object ထဲ မှာ command တစ်ခု ပြင်ထည့်ပေးရပါမယ်
```
//package.json
{
  "name": "npm-express-project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "node server.js"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.18.2"
  }
}

```
- start ဆိုတဲ့ command ကို node server.js  ဆိုပြီး ထည့်ပေးထားတာဖြစ်ပါတယ်
-  `npm start` ကို အသုံးပြုပြီး server ကို start လုပ်လိုက်တဲ့အခါ  Hello World! ကို localhost:3000 မှာ ပြပေးနေမှာပါ။


## 
### use( ) middleware
- အသုံးပြုလိုတဲ့ middleware ကို ခေါ်သုံးချင်တဲ့အခါ အသုံးပြုပါတယ်
##





### read file and send data 
- node http server မှာလို route တွေ check/ ဖိုင် တွေ ဖတ် /  ရလာတဲ့ data တွေ response ပြန်လုပ် စတာတွေ မလိုတော့ပဲ express မှာ static  middleware ကို အသုံးပြူနိုင်ပါတယ်။
### syntax
### `app.use(express.static("folder-name"))`
- အရင် ဆုံး project folder ထဲမှာ **public ဆိုတဲ့ folder တစ်ခု ဆောက်**ပါ
- **public  folder  ထဲမှာ index.html ဖိုင်တစ်ခုလုပ်**ပြီး head tag တစ်ခု ရေးပေးထားပါ။
- server.js ရှိ express မှာ static middleware ကို အသုံးပြုပါမယ်
```js
const express = require("express");
const app = express();
const port = 3000;

app.use(express.static("public"))

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}!`);
});

```
`app.use(express.static("public"))`
-  static middleware မှာ public folderကို  ထည့်ပေးလိုက်တာဖြစ်ပါတယ်
- browser မှာ localhost:3000 ကို ၀င်လိုက်တာနဲ့ index.html ကို ဖတ်ပြီး ရေးထားတဲ့ head tag ကို ပြပေးနေမှာဖြစ်ပါတယ်။
- Node http  server လို request ၀င်လာတဲ့ route ကို စစ် / ဖိုင်တွေဖတ် / ရလာတဲ့ data ကို response ပြန် စတာတွေ လုပ်ပေးစရာမလိုပဲ static middleware ကို အသုံးပြုလိုက်ရုံနဲ့ express က လုပ်ပေးသွားမှာ ဖြစ်ပါတယ်။
##
### Nodemon
- nodemon ဆိုတာ node module(package) တစ်ခုဖြစ်ပြီး
- - js ဖိုင်တွေမှာ အပြောင်းအလဲ တစ်ခု လုပ်လိုက်တာနဲ့ server ကို auto restart လုပ်ပေးတဲ့ module ဖြစ်ပါတယ်။
- nodemon ကို အသုံးပြုခြင်းအားဖြင့် serverကို ပိတ်/ဖွင့် လုပ်စရာမလိုတော့ပဲ တစ်ခုခုပြောင်းလိုက်တိုင်း browserမှာ တစ်ခါည်း test လုပ်လို့ရသွားမှာပါ။
### install nodemon
 - nodemon ကို developer dependency  အနေနဲ့ install လုပ်ပါမယ်။
 ```properties
 npm i -D nodemon
```
- **i** ဆိုတာ insatll ရဲ့ အတိုကောက်ဖြစ်ပြီး **-D** ဆိုတာက  developer dependency  အနေနဲ့ install လုပ်လိုက်တာဖြစ်ပါတယ်။
- install ပြီးတဲ့အခါ package.json မှာ devDependencies ဆိုတဲ့ object တစ်ခု တိုးလာပြီး nodemon ကို ပြပေးမှာဖြစ်ပါတယ်။
- nodemon ကို အသုံးပြုရန်  package.json  ထဲက script object ထဲ မှာ start command ကို ပြင်ထည့်ပေးရပါမယ်
```json
{
  "name": "npm-express-project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "nodemon server.js"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "nodemon": "^2.0.20"
  }
}

```
- npm start  နဲ့ server ကို start ကြည့်ပြီး server.js မှာ တစ်ခုခု ပြောင်းကြည့်ပြီး save လိုက်တာနဲ့  nodemon က server ကို auto restart လုပ်ပေးမှာ ဖြစ်ပါတယ်။
##
### front-end က ပို့လိုက်တဲ့ data တွေကို Express server မှာ ဖမ်းယူခြင်း
- Node JS http server မှာ လေ့လာခဲ့သလိုပဲ POST method နဲ့ request ၀င်လာတဲ့အခါ အတူပါလာတဲ့ data တွေကို express မှာ ဖမ်းယူနည်းကို လေ့လာကြရအောင်။
- အရင်ဆုံး public folder ထဲမှာ script .js ဖိုင်တစ်ခုလုပ်ပြီး object တစ်ခုကို POST method ရဲ့ body အထဲမှာ ထည့်ပေးလိုက်ပါမယ်
```js
const fetchData = async () => {
  const testUserObj = {
    name: "Aung Myanmar",
    email: "aungmm@gmail.com",
    age: 29,
  };

  const response = await fetch("http://localhost:3000/usres", {
    method: "POST",
    headers: { "content-type": "application/json" },
    body: JSON.stringify(testUserObj),
  });
};
fetchData();
```
- `testUserObj` ဆိုတဲ့ object တစ်ခု သတ်မှတ်လိုက်ပါတယ်။
- fetch ကို အသုံးပြုပြီး  server ဆီ request လုပ်လိုက်ပါတယ်
-  method အဖြစ် POST ကို သတ်မှတ်လိုက်ပြီး 
- body မှာ `testUserObj` ဆိုတဲ့ object ကို json string အနေနဲ့ ထည့်ပေးလိုက်မှာမို့လို့
- headers မှာ "content-type": "application/json" ဖြစ်ပါတယ်လို့ server ကို အသိပေးထားတာဖြစ်ပါတယ်။
- script.js ဖိုင်ကို index.html မှာ ချိတ်ပေးလိုက်ပါ။
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Express Server</title>
  </head>
  <body>
    <h1>Hello from static</h1>

    <script src="script.js"></script>
  </body>
</html>

```
##
### serverဆီ request ပို့တာကို ပြင်ဆင်ထားပြီးမလို့ server မှာ အဆိုပါrequest ကို ဖမ်းပါမယ်။
```js
//server.js
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



app.post("/users", (req, res) => {
  console.log(req.body);
  const dataFromScript = req.body;
  users.push(dataFromScript);
  res.send(users);
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}!`);
});

```
> ရှင်းလင်းချက်
> 

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

- users ဆိုတဲ့ array တစ်ခု လုပ်ထားပါတယ်
```js
    app.use(express.static("public"));
    app.use(express.json());
```
-  static middleware နဲ့  json middleware ကို use middleware နဲ့ ခေါ်သုံးထားပါတယ်။
- static middleware က public folder ထဲက ဖိုင်တွေ ဖတ်ဖို့အသုံးပြုပြီး
-  json middleware က request body ထဲမှာ ပါလာတဲ့ data ကို ဖမ်းယူဖို့ အသုံးပြုပါတယ်
```js
app.post("/users", (req, res) => {
  const dataFromScript = req.body;
  users.push(dataFromScript);
  res.send(users);
});
```
- /users route ကနေ ၀င်လာတဲ့ request ကို express post middlewareနဲ့ ဖမ်းထားပါတယ်
- req.body ဆိုပြီး request ကနေ ပါလာတဲ့ data ကို ယူပြီး dataFromScript ဆိုတဲ့ variable ထဲ သိမ်းလိုက်တာပါ။
- - script.js ကနေ json string အနေနဲ့ ပို့ပေးလိုက်တာကို express ရဲ့ json middlewareကို လှမ်းယူပြီး တစ်ခါတည်း js object အဖြစ် ပြောင်းပေးလိုက်တာမလို့ JSON.parse ထပ်လုပ်စရာမလိုပဲ တန်းသုံးလို့ရသွားပါပြီး။
- - node http server မှာလို req.on တွေ chunk တွေ စုစရာမလိုတော့ပဲ express က  json middleware ကို အသုံးပြုလိုက်ရုံနဲ့ အဆင်ပြေသွားပါတယ်။
- users array ထဲမှာ ရလာတဲ့ object ကို push လုပ်လိုက်ပြီး response ပြန်လိုက်တာပါ။
- res.send(users) ကို ခေါ်လိုက်တာနဲ့ express က တစ်ခါတည်း json string ပြောင်းပြီး response ပြန်ေပးတာကို သတိပြုပါ။
##
### server က response ပြန်လာတဲ့ data ကို script.js မှာ လက်ခံပြီး log ထုတ်ကြည့်ပါမယ်။
```js
//script.js
const fetchData = async () => {
  const testUserObj = {
    name: "Aung Myanmar",
    email: "aungmm@gmail.com",
    age: 29,
  };

  const response = await fetch("http://localhost:3000/usres", {
    method: "POST",
    headers: { "content-type": "application/json" },
    body: JSON.stringify(testUserObj),
  });
  const  data = await  response.json();
  console.log(data);
};
fetchData();
```
- npm start နဲ့ server ကို run လိုက်ပြီး browser မှာ refresh လုပ်လိုက်ပါက အသစ်ပို့လိုက်တဲ့ user3 ပါ ပါ၀င်တဲ့ array ကို log ထုတ်ပေးတာ မြင်ရမှာ ဖြစ်ပါတယ်။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep33r22.png)
