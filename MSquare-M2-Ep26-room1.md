## MSquare Programing Fullstack Course
### Episode-*26* 
### Summary For `Room(1)` intermediate Class
##

- အရင်ဆုံး node-express-tuto ဆိုတဲ့ github repo ကို readme  နဲ့ လုပ်ပြီး clone ထားပါ
- clone ထား folder ထဲ npm init လုပ်ပြီး nodemon ကို dev dependency ၊  express ကို dependency အနေနဲ့ install လုပ်ပေးထားပါ။
- package.json ထဲ `"dev": "nodemon index.js"` script တစ်ခု ထည့်ပေးထားပါ
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
### Syntex 
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
```js
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
-  `npm run dev` ကို အသုံးပြုပြီး server ကို start လုပ်လိုက်တဲ့အခါ Hello World! ကို localhost:3000 မှာ ပြပေးနေမှာပါ။
- အထက်ပါအတိုင်းပဲ post , put , delete middleware တွေကို စမ်းသပ်ရေးသားကြည့်ပါ။

## 
### use( ) middleware
-အသုံးပြုလိုတဲ့ middleware ကို ခေါ်သုံးချင်တဲ့အခါ အသုံးပြုပါတယ်
##
```js
app.use((req, res, next) => {
  console.log("Request received");
  next();
});
```
- request  တစ်ခု၀င်လာတိုင်း "Request received" ကို log ထုတ်ခိုင်းလိုက်တာဖြစ်ပါတယ်
- browser  ကနေ request တစ်ခုလုပ်တိုင်း terminal မှာ "Request received"  ဆိုပြီး log ထုတ်ပေးနေတာ မြင်ရမှာဖြစ်ပါတယ်။
##
### read file and send data 
- node http server မှာလို route တွေ check/ ဖိုင် တွေ ဖတ် /  ရလာတဲ့ data တွေ response ပြန်လုပ် စတာတွေ မလိုတော့ပဲ express မှာ static  middleware ကို အသုံးပြူနိုင်ပါတယ်။
### syntax
### `app.use(express.static("folder-name"))`
- အရင် ဆုံး project folder ထဲမှာ public ဆိုတဲ့ folder တစ်ခု ဆောက်ပါ
- public  folder  ထဲမှာ index.html ဖိုင်တစ်ခုလုပ်ပြီး head tag တစ်ခု ရေးပေးထားပါ။
- index.js ရှိ express server မှာ static middleware ကို အသုံးပြုပါမယ်
```js
app.use(express.static("public"))
```
- localhost:3000 ကို ၀င်လိုက်တာနဲ့ index.html ကို ဖတ်ပြီး ရေးထားတဲ့ head tag ကို ပြပေးနေမှာဖြစ်ပါတယ်။
##
### Router- level middleware
- အရင်ဆုံး route တစ်ခု သတ်မှတ်ပါမယ်
- routes  ဆိုတဲ့ folder တစ်ခု လုပ်ပါ။
- ထို folderထဲမှာ route တစ်ခု အသစ်လုပ်မှာမလို့ birdRouter.js ဖိုင်တစ်ခု လုပ်ပါမယ်။
```js
//birdRouter.js
const  express = require("express");
const  birdRouter = express.Router();

birdRouter.get("/", (req, res) => {
  res.send("Birds home page");
});
 
module.exports = birdRouter;
```
- express.Router middleware ကို userRouter အဖြစ်သတ်မှတ်ပြီး အထဲမှာ get middlewareကို အသုံးပြုထားပါတယ်။
- birdRouter ကို index.js မှာ ခေါ်ယူ အသုံးပြုနိုင်ရန် export လုပ်ထားပါတယ်။
- index.js မှာ birdRouter ကို အသုံးပြုနိုင်ရန် အရင် ထည့်ပေးရပါမယ်
```js
const birdRouter = require("./routes/birdRouter")
```
- ဒါဆိုရင် use middlewareနဲ့ ခုလို အသုံးပြုလို့ ရပါပြီး
```js
app.use("/birds", birdRouter);
```
- `/birds` နဲ့ request ၀င်လာရင် birdRouter.js ထဲက get method ကို ခေါ်ပေးမှာဖြစ်ပါတယ်။
- Postman ကနေ `localhost:3000/birds` နဲ့ request send ကြည့်တဲ့အခါ `Birds home page` ကို response လုပ်ပေးတာ မြင်ရမှာပါ။
- birdRouter မှာ about route တစ်ခု ကို ထပ်ထည့်ပါမယ်။
```js
//birdRouter.js
const  express = require("express");
const  birdRouter = express.Router();

birdRouter.get("/", (req, res) => {
  res.send("Birds home page");
});

birdRouter.get("/about", (req, res) => {
  res.send("This is Birds About page");
});
 
module.exports = birdRouter;
```
- Postman မှာ `localhost:3000/birds/about` ဆိုပြီး request send လိုက်တဲ့အခါ **This is Birds About page** ဆိုပြီး ပြပေးမှာဖြစ်ပါတယ်
##
### send an array as json 
- ခု /birds route နဲ့ ၀င်လာတဲ့ request က GET ဖြစ်ခဲ့ရင် Array တစ်ခုကို  response လုပ်ကြည့်ပါမယ်.
```js
//birdRouter.js
const express = require("express");
const birdRouter = express.Router();

const birds = [
  {name: "bird1", color: "red"},
  {name: "bird2", color: "blue"},
]

birdRouter.get("/", (req, res) => {
  res.send(birds);
});

birdRouter.get("/about", (req, res) => {
  res.send("This is Birds About page");
});
module.exports = birdRouter;
```
- birds ဆိုတဲ့  array တစ်ခု လုပ်ထားပြီး GET နဲ့ request ၀င်လာရင် ထို array ကို response လိုက်တာပါ။
- Postman ကနေ `localhost:3000/birds` နဲ့ request send ကြည့်တဲ့အခါ birds ဆိုတဲ့  array ကို response လုပ်ပေးတာ မြင်ရမှာပါ။
##
### All JS code in this Summary
```js
// index.js

const { application } = require("express");
const express = require("express");
const birdRouter = require("./routes/BirdRouter");

const app = express();
const port = 3000;

app.use((req, res, next) => {
  console.log("Request recived");
  next();
});
app.use(express.static("public"));

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.use("/birds", birdRouter);

app.listen(port, () => {
  console.log(`Example app listening on port ${port}!`);
});

```
```js
//birdRouter.js
const express = require("express");
const birdRouter = express.Router();

const birds = [
  {name: "bird1", color: "red"},
  {name: "bird2", color: "blue"},
]

birdRouter.get("/", (req, res) => {
  res.send(birds);
});

birdRouter.get("/about", (req, res) => {
  res.send("This is Birds About page");
});
module.exports = birdRouter;
```

