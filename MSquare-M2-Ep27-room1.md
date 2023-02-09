
## MSquare Programing Fullstack Course
### Episode-*27* 
### Summary For `Room(1)` intermediate Class
##
### Upload express project to vercel
- ပြီးခဲ့သင်ခန်းစာမှာ လေ့ကျင့်ခဲ့တဲ့ express project ကို vercel မှာ တင်ကြည့်ရအောင်
- မတင်ခင်မှာ public folder ထဲ script.js ဖိုင်တစ်ခု လုပ်ပြီး /birds route ကနေ data လှမ်းယူလိုက်ပါ.
- - index.html မှာလဲ ထို script.js ဖိုင်ကို ချိတ်ပေးထားပါ။
```js
//script.js
const fetchData = async () => {
  const response = await fetch("http://localhost:3000/birds");
  const data = await response.json();
  console.log(data);
};
fetchData();

// index.html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Express</title>
  </head>
  <body>
    <h1>Hello</h1>
    <script src="script.js"></script>
  </body>
</html>
```
- git add / commit လုပ်ပြီး github repo မှာ push လုပ်ပေးထားပါ။
- vercel မှာ github နဲ့ login ၀င်ပါ။ [vercel မှာ github နဲ့ login ၀င်နည်း ဒီမှာ ပြန်ကြည့်ပါ](https://github.com/Aungmyanmar32/msquare-fullstack-m2/blob/main/MSquare-M2-Ep23-room1.md#connect-github-with-vercel)
- Add new project နဲ့ express project repo ကို ရွေးပေးပြီး Deploy လုပ်လိုက်ပါ။ 
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/express1.png)

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/express2.png)

- Deploy လုပ်ပြီးပါက dashboard ထဲ သွားပြီး visit ကြည့်တဲ့အခါ script.js မှာ  fetch error တက်နေတာကို console မှာ ၀င်ကြည့်တဲ့အခါ မြင်ရမှာပါ။
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/express3.png)
- project  ကို localhost မှာ စမ်းတုန်းက အဆင်ပြေနေပေမယ့် web ပေါ်တင်တဲ့အခါ
localhost:3000 ဆိုတာ က မရှိတာမလို့  ဒီ error က ဖြစ်လာရတာပါ။
##
### အထက်ပါerror ကို ဖြေရှင်းရန်အတွက် environment ဖိုင်တစ်ခု နဲ့ ချိတ်ဆက်ပေးရပါမယ်
- `.env` ဖိုင်တစ်ခုကို project folder မှာ create လုပ်ပြီး `API_URL = "http://lacalhost:3000"` ကို env ဖိုင်မှာ ရေးထည့်ပေးထားပါ
- dotenv module ကို install လုပ်ပါ။ `npm i dotenv`
-  index.js မှာ dotenv ကို လှမ်းယူပြီး config() method ကို ခေါ်ပေးလိုက်ပါ
```js
const  dotenv = require("dotenv");
dotenv.config()
```
- အခုဆို environment အတွက် server  မှာ ပြင်ဆင်ထားလိုက်ပါပြီး
- ထည့်လိုက်တဲ့ env ထဲက API_URL ရှိမရှိကို `process.env` နဲ့ စစ်ကြည့်လို့ရပါတယ်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/express4.png)
