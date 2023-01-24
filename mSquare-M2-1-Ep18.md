

## MSquare Programing Fullstack Course
### Episode-*18* Summary

ဒီနေ့သင်တန်းမှာတော့ <br>
#### async function
#### Json
#### get data from web server 
အကြောင်း လေ့လာသွားပါမယ်။
##
## async/await function

### async/await function ဆိုတာကတော့
### ဥပမာ လုပ်ဆောင်ချက်သုံးခုရှိတယ် ဆိုပါစို့
### - နံပါတ်တစ် လုပ်ဆောင်ချက်ပြီး အောင် စောင့်ပြီးမှ 
### -- နံပါတ်နှစ် လုပ်ဆောင်ချက် ကို ဆက်လုပ်....
### - -နံပါတ်နှစ် လုပ်ဆောင်ချက်ပြီးအောင် စောင့်ပြီးမှ 
### --- နံပါတ်သုံး လုပ်ဆောင်ချက် ကို ဆက်လုပ်....
ဆိုပြီး အရင်လုပ်ခိုင်းတဲ့ လုပ်ဆောင်ချက်တွေ ပြီးအောင်စောင့်ပြီးမှ ကျန်တာ ဆက်လုပ်ခိုင်းချင်တဲ့အခါ သုံးလေ့ရှိပါတယ်။
### အဓိကအားဖြင့် serverကနေ data တွေယူတဲ့အခါ data ယူပြီးတဲ့အထိ ပြီးအောင်စောင့်ခိုင်းပြီးမှ ရလာတဲ့data ကို မူတည်ပြီး ကျန်တဲ့လုပ်ဆောင်ချက်တွေကို ဆက်run ခိုင်းချင်တဲ့အချိန်မှာ အများဆုံး အသုံးပြုလေ့ရှိပါတယ်။

### Syntax
`async` ( ) => {<br>
  `await` step1-code<br>
  `await` step2-code<br>
  `await` step3-code<br>
}

### Using `async function` with `fetch` api

    const dataFromServer = async () => {
     const url = "https://fakestoreapi.com/products?limit=5";
     const responseData = await fetch(url); 
     const data = await responseData.json();
     console.log(data);
    };
    
    dataFromServer();

## 
### Json
javascript object တစ်မျိုးဖြစ်ပါတယ်။ javascript object ဆိုပေမယ့် ပုံမှန် objcet တွေမှာ undefined , function စတဲ့ property value တွေ ထည့်ရေးလို့မရပါဘူး။
property name တွေကိုလဲ string ထဲမှာ ရေးပေးရပါတယ်။ api (database) ကနေ ပြန်လာတဲ့ data တွေဟာ အများအားဖြင့် json ပုံစံနဲ့ ပြန်လာလေ့ရှိကြပါတယ်။
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
## 
### JSON.parse()
json string တစ်ခုကို object ပုံစံ ပြောင်းဖို့အတွက် သုံးတာပါ။

    const data = { name : "aung"}
    const data2=JSON.stringify(data)
    const data3=JSON.parse(data2)
    //output data2 :'{"name":"aung"}'
    //output data3 : {name: 'aung'}
##
### Get json  from web server (backend)

    browser ကနေ  /data ဆိုတဲ့ route နဲ့ request လုပ်လာတဲ့အခါ 
    json တစ်ခု ကို server ကနေ response ပြန်ကြည့်ရအောင်

```
const  fs = require("fs");
const  http = require("http");

const  server = http.createServer((req, res) => {
 if (req.url === "/data") {
   res.writeHead(200, { "Content-Type":  "application/json" });
   res.write(JSON.stringify({ name:  "aung" }));
   return  res.end();
   }
});
 
server.listen(3000, () => {
console.log("Server started: Listening on port 3000");

});
```
#### `"Content-Type" : "application/json"`
ကျနော်တို့ backend server ကနေ browser ဆီကို http route( url) မှ တစ်ဆင့် Json data လှမ်းပို့လိုတဲ့အခါ ပို့လိုက်တဲ့ data က json ဖြစ်ကြောင်းကို အရင်အသိပေးရပါတယ်။
#### JSON.stringify({ name:  "aung" })
ကျနော်တို့ server ကနေ ပြန်ပို့ချင်တဲ့ object ကို json string ပုံစံပြောင်းပြီး ပြခိုင်းလိုက်ပါ။

### browser မှာ `/data` route နဲ့ ၀င်ကြည့်လိုက်တဲ့အခါမှာတော့ အောက်ပါအတိုင်း မြင်ရမှာဖြစ်ပါတယ်။
![enter image description here](https://github.com/Aungmyanmar32/msquare-fullstack-m2/blob/main/data.jpg?raw=true)

##
### Try this 
server မှ ရလာတဲ့ data ကို index.html (root, "/") ပေါ်မှာ ပြနိုင်အောင် လုပ်ကြည့်ပါ။
#### hint
- set url with data route
- fetch url with async function
- use JSON.parse()  
- Show `My name is {(data from server ).name}` in Browser
