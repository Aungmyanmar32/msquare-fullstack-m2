## MSquare Programing Fullstack Course

### Episode-22

### Summary For  `Room(1)`  intermediate Class

##
### fs.writeFile / fs.writeFilesync
- file တစ်ခုထဲကို text or code တွေ ရေးထည့်ချင်တဲ့အခါ သုံးပါတယ်။
#### Syntax
```js
fs.writeFile("file-name", "text-to-write", callback-function)
```
> Example
- ပုံတစ်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/pe22-1-1.png)
- `server.js` `text.txt` ဖိုင်နှစ်ခု လုပ်ထားပါတယ်
- `server.js` မှာ text.txt ထဲကို hello world ဆိုတဲ့ စာတစ်ကြောင်းရေးထည့်ရန် အောက်က ကုဒ်တွေရေးထည့်ပေးလိုက်ပါတယ်
```js
const fs = require("fs");
fs.writeFile("text.txt", "hello world", () => {
  console.log("file wrote");
});
```
- ဆာဗာကို run လိုက်တဲ့ အခါမှာတော့ text.txt ထဲမှာ server ကနေ ရေးထည့်လိုက်တဲ့ hello world ကို မြင်ရမှာဖြစ်ပါတယ်။
- ပုံနှစ်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep22-1-2.png)
### ဒါက ရှိပြီးသား ဖိုင်ထဲ ကို ရေးထည့်လိုက်တာဖြစ်ပါတယ်။
##
### မရှိသေးတဲ့ဖိုင်ထဲ ရေးထည့်ကြည့်ရအောင်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep22-1-3.png)
- fs.writeFile ကိုသုံးပြီး မရှိတဲ့ file (hello.txt)တစ်ခုကို welcome to myanmar စာတစ်ကြောင်း ရေးထည့်ထားတာပါ
- server ကို  run လိုက်တဲ့အခါမှာတော့ hello.txt ဆိုတဲ့ ဖိုင်ကိုပါ တစ်ခါတည်း လုပ်ပေးပြီး ရေးထည့်ထားတဲ့ welcome to myanmar စာကြောင်းပါ တစ်ပါတည်း ထည့်ပေးလိုက်တာကို တွေ့ရမှာဖြစ်ပါတယ်။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep22-1-4.png)

##
### File upload 

### Html
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <input type="file" accept="img/*" id="fileToUpload" />

    <button onclick="uploadHandler()">Upload</button>

    <script src="script.js"></script>
  </body>
</html>
```
> ရှင်းလင်းချက်
```html
<input type="file" accept="img/*" id="fileToUpload" />
<button onclick="uploadHandler()">Upload</button>
```
- `input type="file"` file input tag တစ်ခု လုပ်ထားတာပါ။
- `accept="img/*"` ပုံဖိုင် အမျိုးအစား ကိုပဲ လက်ခံမယ် လို့ သတ်မှတ်လိုက်တာပါ ။ နောက်က * ကတော့ img အမျိုးအစားထဲက file type( .jpg / .png/ .gif/ etc...) အားလုံးလို့  ဆိုလိုတာပါ။
- file input အောက်မှာ upload ဆိုတဲ့ `button tag` တစ်ခု လုပ်ထားပြီး click event ဖမ်းထားပါတယ်။
### script.js
```js
const fileInputTag = document.querySelector("#fileToUpload");

const uploadHandler = () => {
  fetch("http://localhost:3000/upload", {
    method: "POST",
    body: fileInputTag.files[0],
  });
};
```
> ရှင်းလင်းချက်
```js
const fileInputTag = document.querySelector("#fileToUpload");
```
- file input tag ကို လှမ်းယူထားတာပါ။

```js
const uploadHandler = () => {
  fetch("http://localhost:3000/upload", {
    method: "POST",
    body: fileInputTag.files[0],
  });
};
```
- click event အတွက်  function ဖြစ်ပါတယ်။
- file input က ရလာတဲ့ files array မှ ပထမ items ကို `/upload` route အသုံးပြုပြီး ဆာဗာဆီ POST methodနဲ့ လှမ်းပို့လိုက်တာဖြစ်ပါတယ်။
### server.js
```js
const fs = require("fs");
const http = require("http");

//Create http server
const server = http.createServer((req, res) => {

//for root url
  if (req.url === "/") {
    fs.readFile("index.html", (err, data) => {
      res.writeHead(200, { "Content-Type": "text/html" });
      res.write(data);
      return res.end();
    });
  } else if (req.url === "/script.js") {
  //for /script.js route
    fs.readFile("script.js", (err, data) => {
      res.writeHead(200, { "Content-Type": "text/javascript" });
      res.write(data);
      return res.end();
    });
  }else if (req.url === "/upload") {
    //define file name and type
    const fileExt = req.headers["content-type"];// image/png
    const fileName = fileExt.split("/")[0]; //image
    const fileType = fileExt.split("/")[1]; //png
    const fileNametoWrite =`${fileName}${i}.${fileType}`//image1.png

    //create data to write stream and pipe stream data
    const writeStream = fs.createWriteStream(fileNametoWrite);
    req.pipe(writeStream);
    
    res.writeHead(200, "Content-Type", "application/json");
    res.write(JSON.stringify({ message: "file uploaded" }));
    i = i + 1;
    return res.end();
  } else {
  
  //when invalid Route
    res.writeHead(404, { "Content-Type": "text/plain" });
    res.write("404 | Page Not Found!");
    return res.end();
  }
});

// listen server on port 3000
server.listen(3000, () => {
  console.log("Server started: Listening on port 3000");
});


```
> ရှင်းလင်းချက်
```js
else if (req.url === "/upload") {
    //define file name and type
    const fileExt = req.headers["content-type"];// image/png
    const fileName = fileExt.split("/")[0]; //image
    const fileType = fileExt.split("/")[1]; //png
    const fileNametoWrite =`${fileName}${i}.${fileType}`//image1.png

    //create data to write stream and pipe stream data
    const writeStream = fs.createWriteStream(fileNametoWrite);
    req.pipe(writeStream);
    
    res.writeHead(200, "Content-Type", "application/json");
    res.write(JSON.stringify({ message: "file uploaded" }));
    i = i + 1;
    return res.end();
  }
```
```js
if (req.url === "/upload"){...}
```
- request url က http://localhost:3000/upload ဖြစ်ခဲ့ရင် သူ့ အထဲက ကုဒ်တွေ run ခိုင်းတာပါ။

 ```js
const fileExt = req.headers["content-type"];
 ```
- request ပို့လိုက်တဲ့ data  ထဲက  headers object ကို လှမ်းခေါ်ပြီး  headers objectထဲ content-type ရဲ့ value ကို bracket notation နဲ့ ယူလိုက်တာပါ။
- content-type ရဲ့ တန်ဖိုး က file-type /file-extension လို့ ရလာပါမယ်။
- ဥပမာ ကျနော်တို့က png ဖိုင်တစ်ခု upload လုပ်လိုက်တယ် ဆိုပါစို့။
- ဒါဆိုရင် အပေါ်က fileExt ရဲ့ တန်ဖိုးက "image/png" ဖြစ်ပါမယ်
---
- upload လုပ်လိုက်တဲ့ ဖိုင်ကို ဆာဗာမှာ သိမ်းဖို့အတွက် file-name.file-type လိုအပ်ပါတယ်(eg: dog.jpg)
- ဒါမှပဲ uploaded ဖိုင်တွေကို ဆာဗာမှာ သိမ်းတဲ့အခါ file-name တူနေပြီး overwrite ဖြစ်သွားတာမျိုးတို့
error တက်သွားတာမျိုးတို့ ကနေ ကာကွယ်နိုင်မှာ ဖြစ်ပါတယ်
```js
    const fileName = fileExt.split("/")[0]; //image
    const fileType = fileExt.split("/")[1]; //png
    const fileNametoWrite =`${fileName}${i}.${fileType}`//image1.png
```

- ပို့လိုက်တဲ့ file type နဲ့ random file name တစ်ခု လုပ်ချင်တာမလို့  
-  headers objectထဲ content-type ရဲ့ value ကို "/" နဲ့ string နှစ်ခုခွဲလိုက်တာဖြစ်ပါတယ်။
- ပြီးတော့ fileNametoWrite variable မှာ ပြန်ပေါင်းလိုက်ပြီး သိမ်းလိုက်တာဖြစ်ပါတယ်
- **ဒီနေရာမှာ သတိပြုစေချင်တာက ကျနော်တို့ ဖန်တီးထားတဲ့ fileName ဟာ upload တင်လိုက်တဲ့ file ရဲ့ original name ကို ယူလိုက်တာ မဟုတ်ပါဘူး။ ဆာဗာမှာ ဖိုင်တွေ သိမ်းတဲ့အခါ နာမည်တူဖိုင်ရှိနေရင် error တစ်ခုခုဖြစ်မှာစိုးလို့ အလွယ်ပဲ ဖိုင်အမျိုးအစား ကို ကျပန်း ဖိုင် နာမည် အနေနဲ့ ယူသိမ်းလိုက်တာ ဖြစ်ပါတယ်**
- ခုဆိုရင် random filename နဲ့ file extension တစ်ခုရပြီးမလို့ server မှာ ပို့လိုက်တဲ့ data ကို သိမ်းလို့ရပါပြီး။
```js
    const writeStream = fs.createWriteStream(fileNametoWrite);
    req.pipe(writeStream);
```
- အရင် သင်ခန်းစာတွေတုန်းက request ပို့လိုက်တဲ့ data တွေကို variable တစ်ခု အသစ်ဆောက်/ res.on တွေ chunk တွေ လုပ်ပြီး ယူခဲ့ကြတာ မှတ်မိမယ် ထင်ပါတယ်။
- အပေါ်က ကုဒ်တွေကလဲ ထိုနည်းတူစွာပါပဲ။
- writeStream ဆိုတဲ့ variable ထဲမှာ request က ပို့လိုက်တဲ့ data တွေကို file တစ်ခု write လုပ်ပြီး သိမ်းလိုက်တာဖြစ်ပါတယ်
- ထို writeStream ဆိုတဲ့ variable ကို req.pipe() သုံးပြီး ဆာဗာမှာ သိမ်းလိုက်တာပါ။
```js
    res.writeHead(200, "Content-Type", "application/json");
    res.write(JSON.stringify({ message: "file uploaded" }));
    i = i + 1;
    return res.end();
```

- upload ဖိုင်ကို လက်ခံရရှိတဲ့အကြောင်း frontend ကို response ပြန်လိုက်တာပါ။
-  i ရဲ့ တန်ဖိုးကို တစ်တိုးလိုက်တာက နောက်တစ်ကြီမ် file upload တဲ့အခါ ဆာဗာမှာသိမ်းမယ့်ဖိုင် အမည် မတူစေချင်လို့ ဖြစ်ပါတယ်(ဥပမာ- (ပထမ အကြီမ် - image1.png ) (ဒုတိယအကြိမ်- imang2.png) )
### ခုဆိုရင် image uplaod အတွက် ပြင်ဆင်လို့ ပြီးပါပြီး
- node server ကို run ပြီး image file တစ်ခု upload တင်စမ်းကြည့်ပါက ကျနော်တို့ရဲ့ project folder ထဲမှာ image ဖိုင်တစ်ခု write လုပ်ပေးသွားတာကို မြင်တွေ့ရမှာ ဖြစ်ပါတယ်
##
### Try it
- image file တင်မကပဲ video file တွေ text file ပါ upload လုပ်စမ်းကြည့်ပါ
