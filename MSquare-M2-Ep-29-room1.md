## MSquare Programing Fullstack Course
### Episode-*28* 
### Summary For `Room(1)` intermediate Class
##
### file upload with Express
##
- index.html မှာ file input နဲ့ button တစ်ခု လုပ်ပါမယ်။

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Express TS Vercel</title>
  </head>
  <body>
    <h1>Express Tutorial</h1>
    <h1>File upload</h1>
    <input type="file" name="" id="fileUpload" />
    <button onclick="uploadFile()">Upload</button>

    <script src="script.js"></script>
  </body>
</html>
```
- button မှာ click event တစ်ခု ဖမ်းထားပါတယ်။
- script.js ထဲမှာ ဖမ်းထားတဲ့ uploadFile function ကို သတ်မှတ်ပါမယ်
```js
//script.js
const urlFromLs = localStorage.getItem("apiUrl");

const fetchData = async () => {
  
  console.log(urlFromLs);
  if (urlFromLs) {
    const response = await fetch(`${urlFromLs}/users`);
    const data = await response.json();
    console.log(data);
  } else {
    window.location.href = "/api";
  }
};

//defind upload file function 
const uploadFile = async () => {
  const inputTag = document.getElementById("fileUpload");
  const response = await fetch(`${urlFromLs}/upload`, {
    method: "POST",
    body: inputTag.files[0],
  });
};

fetchData();
```
- express sever  မှာ လက်ခံဖို့ပြင်ဆင်ပါမယ်
- body parser ဆိုတဲ့ node module တစ်ခု install လုပ်ပေးပါ။
- `npm i body-parser`
- body parser က request body ကို ဖတ်ရန်အတွက်ပါ။
- uuid ဆိုတဲ့ node module တစ်ခု install လုပ်ပေးပါ။
- `npm i uuid`
- uuid က Unix ဖြစ်တဲ့ ID တစ်ခုကို generate  လုပ်ပေးတဲ့ module ပါ။ 
- uuid အတွက် data type ဖိုင် module ကို ထပ်ထည့်ပေးရပါမယ်
- `npm i --save-dev @types/uuid`
- index.ts မှာ body-parser နဲ့ uuid ကို လှမ်းထည့်ပေးရပါမယ်
```js
import { v4 as uuidv4 } from "uuid";
import bodyParser, { BodyParser } from "body-parser";
```
- /api route နဲ့ ၀င်လာတဲ့ ဖိုင်ကို serverမှာ random name နဲ့ သိမ်းပါမယ်
 ```js
 app.post("/api/upload", (req: Request, res: Response) => {
  const fileName = v4();
  const fileType = req.headers["content-type"]?.split("/")[1];
  const fileStream = fs.createWriteStream(`${fileName}.${fileType}`);
  req.pipe(fileStream);
  res.end();
});
```
- ခု server ကို npm run dev နဲ့ start ပြီး ပုံတစ်ခုခု uploadတင်ကြည့်လိုက်ပါက uuid က Unix ဖြစ်တဲ့ ID တစ်ခုကို generate  လုပ်ပေးပြီး အဆိုပြ  ID နဲ့ upload လုပ်လိုက်တဲ့ ပုံ ကို သိမ်းပေးလိုက်တာကို တွေ့ရမှာပါ။

##
### multiple file upload with *`formidable`* ( intro)
- formidable နဲ့ ts data types module ကို install လုပ်ပေးပါ။
- `npm i formidable`
- `npm i --save-dev @types/formidable`
- formidable က multiple file upload တဲ့အခါ အသုံးပြုပါတယ်
- formidableကို index.ts မှာ import လုပ်ပေးထားပါ
- `import  formidable  from  "formidable";`
## 
### setup in front-end
- input tag မှာ multiple upload  ရအောင် အရင်ပြင်ရေးရပါမယ်
```html

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Express TS Vercel</title>
  </head>
  <body>
    <h1>Express Tutorial</h1>
    <h1>File upload</h1>
    <input type="file" name="" id="fileUpload" multiple />
    <button onclick="uploadFile()">Upload</button>

    <script src="script.js"></script>
  </body>
</html>
```
- script.js မှာလဲ အနည်းငယ် ပြင်ရေးပေးပါမယ်
```js
const uploadFile = async () => {
  const inputTag = document.getElementById("fileUpload");
  const formData = new FormData();
  const filesArray = [...inputTag.files];
  filesArray.forEach((file) => formData.append("files", file));
  console.log(filesArray);
  const response = await fetch(`${urlFromLs}/upload`, {
    method: "POST",
    body: formData,
  });
};
```
- form data တစ်ခုလုပ်ပြီး input tag က ရှိသမျှ ဖိုင်တွေကို array အဖြစ်ပြောင်းပြီး loop ပတ်ကာ သိမ်းလိုက်ပါတယ်
- ထို form data ကို POST methodနဲ့ server ဆီ request လှမ်းလုပ်ပြီး ပို့လိုက်ပါတယ်။
##
### setup in server (back-end)
- /upload endpoint မှာ POST method ဖမ်းထားတဲ့ code တွေ အနည်းငယ် ပြင်ရေးရပါမယ်
- formidable နဲ့ file တွေလက်ခံပြီး response လုပ်ပါမယ်။
- formidableကို index.js မှာ import လုပ်ပါ
- `import  formidable  from  "formidable";`
- /uplode route မှာ code  အသစ်ပြင်ရေးပါမယ်။
```js
//index.ts - /uplode route 



app.post("/api/upload", (req: Request, res: Response) => {
 
  const form = formidable({ multiples: true });

  form.parse(req, (err, fields, files) => {
    if (err) {
      res.writeHead(err.httpCode || 400, { "Content-Type": "text/plain" });
      return res.end(String(err));
    }
    res.writeHead(200, { "Content-Type": "application/json" });
    res.end(JSON.stringify({ fields, files }, null, 2));
  });
});

```
- const form = formidable({ multiples: true })
- - formidable ကို ခေါ်လိုက်ပြီး multiples option ကို true ပေးကာ form variable ထဲ သိမ်းလိုက်တာပါ
- form.parse(req, (err, fields, files) => {...}
- - form variable ကို parse method ခေါ်လိုက်ပြီး req နဲ့ callback function  တစ်ခု ထည့်ပေးလိုက်ပါတယ်
- - callback ထဲမှာ parameter သုံးခုလက်ခံထားပါတယ်
- error ဖြစ်ခဲ့ရင် error ကို log ထုတ်ခိုင်းထားပြီး
- error မဖြစ်ခဲ့ရင်တော့ fields နဲ့  files ကို  json string  အနေနဲ့  response ပြန်လိုက်တာပါ။
- server ကို start ပြီး ဖိုင်နှစ်ခုတင်ကြည့်တဲ့အခါမှာတော့ network  က response မှာ  fields နဲ့  files ကို  json string  အနေနဲ့  ပြပေးမှာ ဖြစ်ပါတယ်
- ![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep292.png)

## Source code for this lesson [HERE](https://github.com/Aungmyanmar32/express-vercel-ts)
