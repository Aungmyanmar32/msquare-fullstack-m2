## MSquare Programing Fullstack Course

### Episode-23

### Summary For  `Room(1)`  intermediate Class

##
### Setup NPM project
- မိမိရဲ့ project မှာ node package  တွေ သုံးနိုင်ဖို့ npm ကို အရင် initialize လုပ်ပေးရပါမယ်
```properties
npm init --y
```
- npm ကို init လုပ်ပြီးပါက package.json ဖိုင်တစ်ခု ပေါ်လာမှာဖြစ်ပါတယ်။
### package.json
```properties
{
  "name": "test-npm-project",
  "version": "1.0.0",
  "description": "",
  "main": "server.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

##
### install node package(module) to project
- node module တစ်ခု install လုပ်ချင်ရင် npm i module-nameကို အသုံးပြုလေ့ရှိပါတယ်
-  nodemon  module ကို install လုပ်ချင်ရင် `npm i nodemon` ကို ရေးပေးရပါမယ်
- nodemon ကို install  လုပ်ပြီးတဲ့အခါ package,json မှာ "dependencies" ဆိုပြီး nodemon ကို ထည့်ပေးထားတာကို မြင်ရမှာပါ
### package.json
```properties
{
  "name": "test-npm-project",
  "version": "1.0.0",
  "description": "",
  "main": "server.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
     "nodemon": "^2.0.20"
  }
}
```
- nodemon ကို အသုံးပြုနိုင်ရန် package.json ထဲ က script မှာ comand တစ်ခု  ပေါင်းထည့်ပေးရမှာဖြစ်ပါတယ်။
```properties
{
  "name": "test-npm-project",
  "version": "1.0.0",
  "description": "",
  "main": "server.js",
  "scripts": {
    "start" : "nodemon server.js",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "nodemon": "^2.0.20"
  }
}

```
- server ကို စတင်ရန်အတွက် ခါတိုင်း ရေးသလို `node server.js` / `nodemon server.js` ရေးစရာမလိုတော့ပဲ `npm start` ဆိုတာနဲ့ ဆာဗာကို nodemon နဲ့ run ပေးတာမြင်ရမှာပါ။
##
### connect GitHub with vercel 
- https://vercel.com/login ကို သွားပါ။
- containue with Github ကိုနှိပ်ပါ
- Authorize Vercel ကို ရွေးပေးပါ

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/vercel1.png)

- ပြီးရင် မိမိရဲ့ profile ကို နှိပ်ပါ
- create new project
- install vercelလို့ ပြလာရင် Install ကိုနှိပ်ပေးပါ။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/vercel2.png)

- ချိတ်ချင်တဲ့ repo ကို ရွေးပေးပါ
- ခု ကျနော်က အစမ်းရေးထားတဲ့ weather api test repo ကို ရွေးလိုက်ပါတယ်။
- ထပ်ပေါ်လာတဲ့ အထဲမှာ deploy လုပ်လိုက်ပါ

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/vercel4.png)

- ခေတ္တ စောင့်ပြီးလို့ အောက်ကပုံလို ပြလာရင် project တစ်ခု create  လို့ ပြီးပါပြီး
- Containue to Dashboard ကို နှိပ်လိုက်ပါ
- 
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/vercel5.png)
- domin နေရာက link မှတဆင့် လုပ်ထားတဲ့ project ကို webpage တစ်ခုအနေနဲ့ ကြည့်လို့ ရပါပြီး
- 
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/vercel6.png)
- အောက်ကပုံက  ကျနော်ရေးထားတဲ့ weather  api project ကို vercel link နဲ့ ၀င်ကြည့်တာထားတာ ဖြစ်ပါတယ်။
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/vercel7.png)

##
### Try it
-  node module တွေကို npm သုံးပြီး project ထဲ install လုပ်ကြည့်ပါ။
- vercel ကို  github နဲ့ ချိတ်ပြီး repo သုံး လေးခုလောက် deploy လုပ်ကြည့်ပါ။
