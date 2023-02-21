## MSquare Programing Fullstack Course
### Episode-*26* Summary for (group 2) 

ဒီနေ့သင်တန်းမှာတော့ <br>
### route
### Use GET method with pure JavaScript
အကြောင်း လေ့လာသွားပါမယ်။
##
### Route
- Route ဆိုတာ ဆာဗာထဲမှာ ရှိနေတဲ့ အခန်းခွဲ တစ်ခုလို့ သတ်မှတ်နိုင်ပါတယ်
- http://localhost:3000/route လို့ သုံးလေ့ရှိပါတယ်။
- route တွေအထဲမှာ ထူးခြားတဲ့ route က  `"/"` ပါ။ **root** လို့လဲ ခေါ်ပါတယ်။
##
### Root  (သို့မဟုတ် ) `"/"`
- url တစ်ခုကို ၀င်လိုက်တာနဲ့ root route ကို browser ကနေ auto ထည့်ပေးလေ့ရှိပြီး
 address bar မှာ ဖျောက်ထားလေ့ရှိပါတယ်
 - http://localhost:3000 ကို ၀င်လိုက်တာနဲ့ browser က  **root (  `"/"` )** ကို တန်း၀င်လိုက်တာဖြစ်ပါတယ် ။ ဒါပေမယ့် address bar  မှာတော့ http://localhost:3000/ ဆိုပြီး ပြပေးမှာ မဟုတ်ပဲ `"/"` ကို ဖျောက်ပြီး http://localhost:3000 လို့ပဲ ပြပေးမှာ ဖြစ်ပါတယ်။
 ##
 ### အခုဆိုရင် request လုပ်တာတဲ့ route နဲ့ method ကို သုံးပြီး server မှာ response လုပ်ကြည့်ရအောင်

```js
// server.js
const http = require("http");
const fs = require("fs");

const users = [
  { name: "Aung Aung", email: "aungaung1@gmail.com", password: 123456 },
  { name: "Kyaw Kyaw", email: "kyawkyaw2@gmail.com", password: 123456 },
  { name: "Tun Tun", email: "tuntun3@gmail.com", password: 123456 },
];

const server = http.createServer((request, response) => {
  const method = request.method;
  const route = request.url;
  if (route === "/") {
    fs.readFile("./index.html", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write(data);
      response.end();
    });
  }  else if (route === "/users") {
      if (request.method === "GET") {
        response.writeHead(200, { "Content-Type": "application/json" });
        response.write(JSON.stringify(users));
        response.end();
    }
  } 
});

server.listen(3000, () => {
  console.log("Server Runnig on Port 3000");
});
```
- server.js မှာ users Array တစ်ခု လုပ်ထားပါတယ်။
- http.createServer လုပ်ထားပြီး port 3000 မှာ listen  လုပ်ထားပါတယ်။
- server ထဲမှာ request ၀င်လာတဲ့ method ကို request.method နဲ့ ဖမ်း ပြီး `method` မှာ သိမ်းထားပြီး ၊ ၀င်လာတဲ့ route ကို request.url နဲ့ ဖမ်းကာ `route` မှာသိမ်းထားပါတယ်
```js
  if (route === "/") {
    fs.readFile("./index.html", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write(data);
      response.end();
    });
  } 
```
- request လုပ်လာတဲ့ route က root ဖြစ်ခဲ့ရင် index.html ကို ဖတ်ပြီး ရလာတဲ့ data ကို response ပြန်လိုက်တာဖြစ်ပါတယ်။
```js
else if (route === "/users") {
      if (request.method === "GET") {
        response.writeHead(200, { "Content-Type": "application/json" });
        response.write(JSON.stringify(users));
        response.end();
    }
  } 
});
```
- `else if (route === "/users")`တကယ်လို့ request လုပ်လာတဲ့ route က "/users" ဖြစ်ခဲ့ရင်တော့ သူ့အထဲ က ကုဒ်တွေ run ခိုင်းလိုက်တာပါ။
- `if (request.method === "GET")` /users route နဲ့ လာတဲ့ request ကို ဘာ method နဲ့ request လုပ်တာလဲ ဆိုပြီး ထပ်စစ်လိုက်တာပါ။ "GET" ဆိုရင်တော့ သူ့အထဲက ကုဒ်တွေ ဆက် run ခိုင်းတာပါ။
-  `response.writeHead(200, { "Content-Type": "application/json" });`
        `response.write(JSON.stringify(users));`
        server  ကနေ users Array ကို JSON string ပုံစံ ပြောင်းပြီး response Head မှာ application/json ဖိုင် အမျိုးအစားကို response လုပ်ပေးလိုက်တာ ဖြစ်ကြောင်း တစ်ခါတည်း ထည့်ပေးလိုက်တာပါ။
##

### postman နဲ့ `/user` route ကို request send ကြည့်ပါမယ်
- url adress နေရာမှာ localhost:3000/users ကို ထည့်ပေးပြီး GET နဲ့ request send လိုက်တဲ့အခါ 
- server ကနေ users Array ကို json string ပုံစံနဲ့ response လုပ်ပေးတာကို output မှာ မြင်ရမှာဖြစ်ပါတယ်။
##
### Get data from server using *JavaScript ( front-end)*
- အရင်ဆုံး script.js ဖိုင်တစ်ခုလုပ်ပြီး index.html မှာ ချိတ်လိုက်ပါမယ်။
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Node Route</title>
  </head>
  <body>
    <h1>Node CURD </h1>

    <script src="script.js"></script> //here
  </body>
</html>
```
- script.js ထဲ မှာ fetch ကို သုံးပြီး sever က data ကို လှမ်းယူပါမယ်
```js
const fetchData = async () => {
  // get data from server
  const url = "http://localhost:3000/users";
  const response = await fetch(url);
  const data = await response.json();
  console.log(data)
}

fetchData()
```
- `const url = "http://localhost:3000/users";` request လုပ်မယ့် route ကို url လို့ သတ်မှတ်လိုက်တာပါ။
- `const response = await fetch(url);` ဆာဗာက data ကို async/await သုံးပြီး လှမ်းယူကာ response ဆိုတဲ့ variable ထဲ သိမ်းလိုက်တာပါ။
- `const data = await response.json();`ထို response ထဲက json ကို လှမ်းယူပြီး data အနေနဲ့ သိမ်းလိုက်တာပါ
- `console.log(data)` ရလာတဲ့ data ကို log ထုတ်ကြည့်လိုက်တာပါ။
##
### route for script.js
- http://localhost:3000 ကို browser  ကနေ ၀င်ကြည့်တဲ့အခါ  root route ကို ရောက်သွားပါတယ်။
- server မှာ root နဲ့ request ၀င်လာရင် ကျနော်တို့က index.html ကို readFile လုပ်ပြီး response လုပ်ပေးထားတာမလို့ browser က index.html ကို လက်ခံကာ အထဲက ကုဒ်တွေကို စ run ပါတော့တယ်။
- script.js ကို ချိတ်ထားတဲ့နေရာ ရောက်တဲ့အခါ browser က server ဆီကို `/script.js` ဆိုတဲ့ route နဲ့ GET method ကို သုံးပြီး request ထပ်လုပ်ပါတယ်။
- ဒါကြောင့်မလို့ `/script.js` route အတွက် server  မှာ ပြင်ဆင်ပေးထားရပါမယ်။
```js
const http = require("http");
const fs = require("fs");

const users = [
  { name: "Aung Aung", email: "aungaung1@gmail.com", password: 123456 },
  { name: "Kyaw Kyaw", email: "kyawkyaw2@gmail.com", password: 123456 },
  { name: "Tun Tun", email: "tuntun3@gmail.com", password: 123456 },
];

const server = http.createServer((request, response) => {
  const method = request.method;
  const route = request.url;
  if (route === "/") {
    fs.readFile("./index.html", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/html" });
      response.write(data);
      response.end();
    });
  } else if (route === "/script.js") {
    fs.readFile("./script.js", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/javascript" });
      response.write(data);
      response.end();
    });
  } else if (route === "/users") {
    if (request.method === "GET") {
      response.writeHead(200, { "Content-Type": "application/json" });
      response.write(JSON.stringify(users));
      response.end();
    }
  } 
});

server.listen(3000, () => {
  console.log("Server Runnig on Port 3000");
});
```
> ရှင်းလင်းချက်
```js
else if (route === "/script.js") {
    fs.readFile("./script.js", (err, data) => {
      response.writeHead(200, { "Content-Type": "text/javascript" });
      response.write(data);
      response.end();
    });
  }
```
- `/script.js` route နဲ့  request ၀င်လာတဲ့ အခါ script.js ဖိုင်ကို ဖတ်ပေးပြီး ရလာတဲ့ data ကို response ပြန်လိုက်တာဖြစ်ပါတယ်။
- ခုဆိုရင် browser က server က response လုပ်လိုက်တဲ့ data  ကို အသုံးပြုပြီး script.js  ထဲက ကုဒ်တွေ run ပေးပါပြီး
- script.js  ထဲမှာ  ဆာဗာကို /users route နဲ့ fetch လုပ်ပြီး ရလာတဲ့ data ကို log ထားတာမလို့ 
browser console ထဲမှာ ဆာဗာက response ပြန်ပို့ထားတဲ့ json ( users Array) ကို မြင်ရမှာဖြစ်ပါတယ်
