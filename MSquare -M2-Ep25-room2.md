## MSquare Programing Fullstack Course
### Episode-*25* Summary for (group 2) 

ဒီနေ့သင်တန်းမှာတော့ <br>
### Postman ကို အသုံးပြုပြီး server ဆီ request send လုပ်ခြင်း
### Request method ပေါ် မူတည်ပြီး  server မှ response ပြန်ခြင်း
### Json အကြောင်း 
စတာတွေ လေ့လာသွားပါမယ်။
##
- အရင်ဆုံး Postman ကို https://www.postman.com/downloads/ ကနေ download လုပ်ပြီး install လုပ်ပေးပါ။
- create account လုပ်မလားမေးရင် ဘေးနားက skip ... ကို နှိပ်လိုက်ပါ
- overwrite ဘေးက  + ကို နှိပ်ပြီး postman ကို စသုံးလို့ရပါပြီး။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/ep20-1-1.jpg)

- method ဆိုတာက ကျနော်တို့  server ကို request လုပ်တဲ့ အခါ သုံးရမယ့် http method တွေကို ဆိုလိုတာပါ။
- url/route မှာတော့ မိမိတို့ရဲ့ node server adress နဲ့ port ကို ရေးပေးရမှာပါ။
- ( ဥပမာ **localhost:3000** )
- send ခလုတ်ကတော့ server ဆီ request လှမ်းပို့လိုက်တာပါ။
- output မှာတော့  server ကနေ response ပြန်တဲ့ဟာကို ပြပေးမှာ ဖြစ်ပါတယ်
##
### ခု ကျနော်တို့  Postman ကနေ  GET , POST, PUT, DELETE method တွေ server ဆီကို request လုပ်ပါမယ်
### ဆာဗာကလဲ ဘယ်method နဲ့ request လုပ်လိုက်တာကို ဖတ်ပြီး request လုပ်လာတဲ့ method name အတိုင်း response ပြန်ထုတ်ပေးလာအောင် လုပ်ကြည့်ပါမယ်

### server.js
```js
const http = require("http");

const server = http.createServer((request, response) => {
  const method = request.method;
  if (method === "GET") {
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
  } else if (method === "POST") {
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
  } else if (method === "PUT") {
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
  } else if (method === "DELETE") {
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
  }
});

server.listen(3000, () => {
  console.log("Server Runnig on Port 3000");
});

```
> ရှင်းလင်းချက်
```js
const http = require("http");
```
- http server လုပ်ရန် node မှာ ရှိပြီးသား http ကို လှမ်းယူလိုက်တာပါ
```js
const server = http.createServer((request, response) => { })
```
- http ရဲ့ createServer method ကို သုံးပြီး ဆာဗာ တစ်ခု create လုပ်လိုက်တာပါ
```js
const method = request.method;
```
- client က ဘာmethod နဲ့ request လုပ်လာတယ်ဆိုတာကို request.method နဲ့ ဖမ်းလိုက်ပြီး method ဆိုတဲ့ variable ထဲ သိမ်းလိုက်တာပါ
```js
if (method === "GET") {......}
```
- တကယ်လို့  client က GET method နဲ့ request လုပ်လာတယ်ဆိုရင် သူ့အထဲက ကုဒ်တွေ run ပေးပါလို့ သတ်မှတ်လိုက်တာပါ။
```js
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
```
- server က client ဘက်ကို response ပြန်လုပ်ပေးတာပါ။
```js
response.writeHead(200, "Content-Type", "text/html");
```
- status code 200 (ok) နဲ့ html တစ်ခု response လုပ်လိုက်ကြောင်း browser ကို အသိပေးလိုက်တာပါ

```js
response.write(`<h1>${method}</h1>`);
```
- request method ကို h1 tag ထဲ ထည့်ပြီး client ဆီကို response လုပ်လိုက်တာပါ
```js
response.end();
```
- ဆာဗာဆီက response လုပ်တာ ပြီးပြီးလို့ client  ကို အသိပေးလိုက်တာပါ
```js
 else if (method === "POST") {
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
  }
```
- တကယ်လို့  client က POST method နဲ့ request လုပ်လာတယ်ဆိုရင် 
- ၀င်လာတဲ့ request method အတိုင်း h1 tag နဲ့ response ပြန်လုပ်လိုက်တာပါ
```js
else if (method === "PUT") {
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
  }
```
- တကယ်လို့  client က PUT method နဲ့ request လုပ်လာတယ်ဆိုရင် 
- ၀င်လာတဲ့ request method အတိုင်း h1 tag နဲ့ response ပြန်လုပ်လိုက်တာပါ
```js
else if (method === " DELETE") {
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
  }
```
- တကယ်လို့  client က DELETE method နဲ့ request လုပ်လာတယ်ဆိုရင် 
- ၀င်လာတဲ့ request method အတိုင်း h1 tag နဲ့ response ပြန်လုပ်လိုက်တာပါ

```js
server.listen(3000, () => {
  console.log("Server Runnig on Port 3000");
});
```
- server  ကို port 3000 မှာ စောင့်ကြည့်နားထောင်ခိုင်းလိုက်တာပါ။
- ခု server ကို `node server.js` နဲ့ run ထားလိုက်ပါ။
##
### ဆာဗာပိုင်း အဆင်သင့်ဖြစ်ပြီမလို့ postman ကနေ request  send ကြည့်ပါမယ်
- Postman မှာ
1.  method ကို  GET ရွေးပေးပါ။
2. url မှာ localhost:3000 ကို ထည့်ပါ
3. request send ကြည့်ပါ
4. output က preview မှာ server က response လုပ်လိုက်တဲ့ GET  ကို ပြပေးမှာ ဖြစ်ပါတယ်

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/prtwo1.png)
- ကျန်တဲ့ POST , PUT , DELETE method တွေကိုလဲ စမ်ကြည့်ပါက အောက်ပါအတိုင်း မြင်ရမှာပါ။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/prtwo2.png)

### အပေါ်က server.js မှာ ရေးထားတဲ့ code တွေက ထပ်နေတာကို မြင်ရမှာပါ
- အတာ့ကို ရှင်းရှင်းလေးဖြစ်အောင် ခုလို ရေးလို့ရပါတယ်။
### server.js
```js
const http = require("http");

const server = http.createServer((request, response) => {
    const method = request.method;
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
    });

server.listen(3000, () => {
  console.log("Server Runnig on Port 3000");
});
```
##
### server ဆီ GET method နဲ့ request လုပ်လာတဲ့ အခါ html ဖိုင်တစ်ခုကို read လုပ်ပြီး ရလာတဲ့ data ကို response ပြန်လုပ်ကြည့်ရအောင်။ 
### တခြား method ဆိုရင်တော့ အပေါ်က သင်ခန်းစာလိုပဲ methodကိုပဲ response လုပ်ကြပါမယ်။
- index.html ဖိုင်တစ်ခုဆောက်ပါ။
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
    <h1>Welcome to Myanmar</h1>
  </body>
</html>
```
- Welcome to Myanmar ကို  h1 tag နဲ့ ရေးထားလိုက်ပါတယ်
### server.js
```js
const http = require("http");
const fs = require("fs");

const server = http.createServer((request, response) => {
  const method = request.method;
  if (method === "GET") {
    fs.readFile("./index.html", (err, data) => {
      response.writeHead(200, "Content-Type", "text/html");
      response.write(data);
      response.end();
    });
  } else {
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
  }
});

server.listen(3000, () => {
  console.log("Server Runnig on Port 3000");
});
```
> ရှင်းလင်းချက်
```js
 if (method === "GET") {
    fs.readFile("./index.html", (err, data) => {
      response.writeHead(200, "Content-Type", "text/html");
      response.write(data);
      response.end();
    });
  }
```
- တကယ်လို့ **request method က GET ဖြစ်ခဲ့ရင်** index.html ဖိုင်ကို ဖတ်ပြီး ရလာတဲ့  data ကို response လုပ်ပေးလိုက်တာပါ။

```js
else {
    response.writeHead(200, "Content-Type", "text/html");
    response.write(`<h1>${method}</h1>`);
    response.end();
  }
```
- တကယ်လို့ **request method က GET မဟုတ်ခဲ့ဘူးဆိုရင်**တော့ request method ကို h1 tag  ထဲ ထည့်ပြီး response လုပ်ပေးလိုက်တာပါ။
- --
- အထက်ပါ ကုဒ်ကို postman မှာ GET method နဲ့ request send လိုက်တဲ့အခါ  output preview မှာ
 Welcome to Myanmar ပြပေးမှာပါ

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/prtwo3.png)
 - ကျန် method  နဲ့  request send လိုက်တဲ့အခါ မှာတော့ send လိုက်တဲ့ method ပဲ ပြပေးမှာဖြစ်ပါတယ်။
##
##
### Json
javascript object တစ်မျိုးဖြစ်ပါတယ်။ Json က javascript object ဆိုပေမယ့် ပုံမှန် objcet တွေမှာလို undefined , function စတဲ့ property value တွေ ထည့်ရေးလို့မရပါဘူး။
property name တွေကိုလဲ string ထဲမှာ ရေးပေးရပါတယ်။ server (database) ကနေ ပြန်လာတဲ့ data တွေဟာ အများအားဖြင့် json ပုံစံနဲ့ ပြန်လာလေ့ရှိကြပါတယ်။
ကျနော်တို့ api တွေနဲ့ ဆက်သွယ်တဲ့အခါမှာလဲ json ပုံစံနဲ့ပဲ အများဆုံး အသုံးပြုလေ့ရှိပါတယ်။

    //this is valid json
     { 
     "test" : 234 
     }
    ----
    //this is not valid json
     { 
     test: 234
     }

>Json ဟုတ်မဟုတ် https://jsonlint.com/ မှာ ၀င်ရောက် စစ်ဆေးနိုင်ပါတယ်

### JSON.stringify()
object တစ်ခုကို json string ပုံစံ ပြောင်းဖို့အတွက် သုံးတာပါ။
```js
const data = { name : "aung"}
 const data2=JSON.stringify(data)
 console.log(data2)
  //output data2 :'{"name":"aung"}'
 ```
## 
### JSON.parse()
json string တစ်ခုကို object ပုံစံ ပြန်ပြောင်းဖို့အတွက် သုံးတာပါ။

 ```js
const data = { name : "aung"}
 const data2=JSON.stringify(data)
 const data3=JSON.parse(data2)
   console.log(data3)
    //output data3 : {name: 'aung'}
 
 ```
    

##
