## MSquare Programing Fullstack Course
### Episode-*28* 
### Summary For `Room(1)` intermediate Class
##
### Express with Typescript

- အရင်ဆုံး project folder တစ်ခုလုပ် github နဲ့ ချိတ်ပြီး npm init လုပ်ပေးပါ
- အောက်ပါ module များကို install လုပ်ပေးထားပါ
1. express
2. typescript
3. ts-node-dev ( use -D )
4. @types/express ( use -D)
5. dotenv
- package.json မှာ လဲ dev script (**"ts-node-dev index.ts"**)တစ်ခု ထည့်ပေးထားပါ။

```properties
//package.json
{
  "name": "express-vercel-ts",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "dev": "ts-node-dev index.ts"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/Aungmyanmar32/express-vercel-ts.git"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/Aungmyanmar32/express-vercel-ts/issues"
  },
  "homepage": "https://github.com/Aungmyanmar32/express-vercel-ts#readme",
  "dependencies": {
    "dotenv": "^16.0.3",
    "express": "^4.18.2",
    "typescript": "^4.9.5"
  },
  "devDependencies": {
    "@types/express": "^4.17.17",
    "ts-node-dev": "^2.0.0"
  }
}

```
##
## Solve Url problem on versel
### file structure and basic code
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/evt2.png)

- public folder တစ်ခု လုပ်ထားပြီး index.html, script.js ဖိူင်နှစ်ခုထည့်ထားပါတယ်
- .env ဖိုင်တစ်ခု လုပ်ထားပြီး localhost:3000 ကို API_URL အဖြစ် သိမ်းထားပါတယ်
- index.ts ဖိုင်တစ်ခု လုပ်ထားပြီး express , { Request, Response } ကို expressမှ import လုပ်ထားပါတယ်
- dotenv ကို လဲ import လုပ်ထားပြီး dotenv.config() method ကို ခေါ်ထားပါတယ်
- express static  middlewareနဲ့ public folderကို ထည့်ပေးထားပါတယ်
- get middleware နဲ့ `/users` end-point မှာ ဖမ်းထားပြီး object တစ်ခု response လုပ်ထားပါတယ်
- ts ကို သုံးထားတာမလို့ req parameter က express က Requset data-type ဖြစ်ကြောင်း ရေးပေးထားရပါမယ်
- res parameter ကိုလဲ express က Response data-type ဖြစ်ကြောင်း ရေးပေးထားရပါမယ်
- **script.js** မှာတော့ /users route ကို GET နဲ့ request လုပ်ထားပြီး ရလာတဲ့ data ကို log ထုတ်ထားပါတယ်
- index.html မှာ **script.js** ကို ချိတ်ထားပါတယ်
- npm run dev နဲ့ server ကို စလိုက်တဲ့အချိန်မှာတော့ localhost:3000 မှာ index.html ကပြပေးတဲ့ head tag ကို မြင်ရမှာဖြစ်ပါတယ်။
##
### Send Api url to local storage
- env  ဖိုင်ထဲ ထည့်ထားတဲ့ API_URL ကို process မှ တစ်ဆင့်လှမ်းယူပြီး apiUrl ဆိုတဲ့ variable ထဲ ထည့်သိမ်းထာပါတယ်။
- ထို apiUrl ဆိုတဲ့ variable ကို  local storage တစ်ခုအနေနဲ့ သိမ်းလိုက်ပြီး html ဆိုတဲ့ variable မှာ ထပ်သိမ်းလိုက်ပါတယ်
- /api route နဲ့ request ၀င်လာရင် အထက်က html ကို  response ပြန်လုပ်ပေးလိုက်တာပါ။
```js
//index.ts
const apiUrl = process.env.API_URL;

const html = `<html>
 <body>
 <script>
  localStorage.setItem("apiUrl" ,${apiUrl} )
 </script>
 </body>
</html>
`;

app.get("/api", (req: Request, res: Response) => {
  res.send(html);
});
```

##
### GET local storage Item and set url
- script.js မှာ local storage က Item ကိုလှမ်းယူလိုက်ပြီး apiurl ရတာနဲ့ ဆာဗာက data ကို လှမ်းယူထားလိုက်တာပါ
- local storage က Item မရသေးရင်တော့ /api ကနေ request  သွားလုပ်ခိုင်းလိုက်တာပါ
- ဒါဆိုရင် server က process ကနေ api url လှမ်းပို့လို့ ရပါပြီး
```js
const fetchData = async () => {
  const urlFromLs = localStorage.getItem("apiUrl");
  console.log(urlFromLs);
  if (urlFromLs) {
    const response = await fetch(`${urlFromLs}/users`);
    const data = await response.json();
    console.log(data);
  } else {
    window.location.href = "/api";
  }
};
fetchData();
```
- server ကို run လိုက်ပြီး localhost:3000 ၀င်ကြည့်လိုက်ပါက log ထုတ်ထားတဲ့  data ကို တွေ့ရမှာပါ

##
###   Final set up

- vercel မှာ တင်ဖို့ အတွက် နောက်ဆုံးအဆင့် ပြင်ဆင်ပါမယ်
- vercel.json ဖိုင်တစ်ခု လုပ်ပြီး အောက်က ကုဒ်ကို ရေးထည့်ပေးပါ
```properties
{
"rewrites": [{ "source": "/api/(.*)", "destination": "/api" }]
}
```
- index.ts မှာ /users route ကို /api/users  လို့ပြောင်းပေးပါ
```js
import express, { Request, Response } from "express";
import dotenv from "dotenv";
const app = express();
const PORT = 3000;
dotenv.config();

app.use(express.static("./public"));

const apiUrl = process.env.API_URL;
const html = `<html>
<body>
<script>
localStorage.setItem("apiUrl" ,"${apiUrl}" )
</script>
</body>
</html>
`;

app.get("/api", (req: Request, res: Response) => {
  res.send(html);
});

//change here
app.get("/api/users", (req: Request, res: Response) => {
  res.send({ name: "user1", email: "user1@gmail.com", age: 30 });
});

app.listen(PORT, () => {
  console.log("server at port:", PORT);
});

```
- api folder အသစ်လုပ်ပြီး index.ts ဖိုင်ကို ရွေ့ထည့်ပေးပါ
- .gitignore ဖိုင်ကို လုပ်ပြီး node module folder ကို ignoreလုပ်ပေးပါ
- ပြီးရင် github မှာ push လုပ်ပြီး vercel မှာ new project deploy လုပ်ပေးလိုက်ပါ။
-Deploy လုပ်ပီးရလာတဲ့ project domin link ကို copy လုပ်ထားပါ
- project ထ ၀င် ပြီး setting > Environment Variables > ထဲသွားပြီး 
- key မှာ API_URL ထည့်ပေးပါ
- value မှာ မိမိ-project-domin-link/api ဆိုပြီးထည့်ပါ
- ​Production​/Preview/​Development သုံးခုစလုံး အမှန်ခြစ်ပြီး saveပါ

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/evts1.png)

- ခုဆိုရင် localhostပြဿနာကို ဖြေရှင်းလို့ပြီးပြီမို့ vercel မှာ တင်ထားတဲ့ ကိုယ့်ရဲ့ project  linkကို၀င်ကြည့်တဲ့အခါ ကျနော်တို့  log ထုတ်ထားတဲ့ object(data)  ကို console မှာ မြင်ရမှာ ဖြစ်ပါတယ်
##
### curd ဖြစ်အောင် ဆက်လုပ်သွားကြပါ။



