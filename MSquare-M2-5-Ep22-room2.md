## MSquare Programing Fullstack Course
### Episode-22 *Summary*

ဒီနေ့သင်တန်းမှာတော့ 

 - **async/await function**

 
 <br>အကြောင်း လေ့လာသွားမှာပါ။

## async/await function

### async/await function ဆိုတာကတော့
### ဥပမာ လုပ်ဆောင်ချက်သုံးခုရှိတယ် ဆိုပါစို့
### - နံပါတ်တစ် လုပ်ဆောင်ချက်ပြီး အောင် စောင့်ပြီးမှ 
### -- နံပါတ်နှစ် လုပ်ဆောင်ချက် ကို ဆက်လုပ်....
### - -နံပါတ်နှစ် လုပ်ဆောင်ချက်ပြီးအောင် စောင့်ပြီးမှ 
### --- နံပါတ်သုံး လုပ်ဆောင်ချက် ကို ဆက်လုပ်....
ဆိုပြီး အရင်လုပ်ခိုင်းတဲ့ လုပ်ဆောင်ချက်တွေ ပြီးအောင်စောင့်ပြီးမှ ကျန်တာ ဆက်လုပ်ခိုင်းချင်တဲ့အခါ သုံးလေ့ရှိပါတယ်။
###   promise ကို အသုံးပြုရ လွယ်ကူစေရန် async/ await function နဲ့အစားထိုး အသုံးပြုလေ့ရှိပါတယ်
### 


### Syntax
`async` ( ) => {
  `await` step1-code
  `await` step2-code
  `await` step3-code
}
##
### Get data from api server 
- api server ကနေ data များကို fetch ကို အသုံးပြုပြီး လှမ်းယူပုံကို အရင် သင်ခန်းစာမှာ လေ့လာခဲ့ပြီး ဖြစ်ပါတယ်။
- 
```js
const getData = () => {
  const url = "https://fakestoreapi.com/products";
  const fetchData = fetch(url);
  fetchData
    .then((response) => response.json())
    .then((data) => console.log(data));
};
getData()
```
- အထက်ပါကုဒ်ကို async / await function နဲ့ အခုလို သုံးလို့ရပါတယ်
```js
const getData = async() => {
 const url = "https://fakestoreapi.com/products";
 const response = await fetch(url);
 const data = await response.json();
 console.log(data);
};

getData();
```
> ရှင်းလင်းချက်
```js
const getData = async() =>
```
- getDataဆိုတဲ့ function ကို async function ဖြစ်ကြောင်း သတ်မှတ်လိုက်ပါတယ်
```js
const url = "https://fakestoreapi.com/products";
```
- အသုံးပြုမယ့်ဆာဗာရဲ့ လိပ်စာကို url variable နဲ့ သိမ်းလိုက်တာပါ
```js
const response = await fetch(url);
```
- fetch ကနေ return ပြန်လာတဲ့ promise ကို response variable ထဲ သိမ်းလိုက်တာပါ။
- ဒီနေရာမှာ `await`  က fetch အလုပ်လုပ်နေတာကို ပြီးအောင်စောင့်ပါလို့ အဓိပ္ပါယ် ရပါတယ်
 ```js
const data = await response.json();
```
- response က data တွေထဲ json dataကို လိုချင်တာမလို့ .json() နဲ့ လှမ်းယူလိုက်တာဖြစ်ပါတယ်။
##
### Catch error in async/ await Function
-async function မှာ error ဖြစ်လာခဲ့ရင် ဖမ်းယူဖို့အတွက် try{} catch{} နဲ့ အသုံးပြုရပါမယ်။
```js
const getData = async() => {
 try{
  const url = "https://fakestoreapi.com/productsffffff";
  const response = await fetch(url);
  const data = await response.json();
  console.log(data);
} catch (error) {
  console.error("error occuerd" ,error);
 }
};
getData();
```
- ရေးထားတဲ့ ကုဒ်တွေကို `try { }` ထဲ ထည့်ထားလိုက်ပြီး error မရှိခဲ့ code ရေးထားတဲ့အတိုင်း အလုပ်လုပ်ခိုင်းထားတာဖြစ်ပြီး
- error ရှိလာရင်ခဲ့တော့ ဖြစ်တဲ့ error ကို `catch { }` ထဲ မှာ console.log ထုတ်ခိုင်းထားဖြစ်ပါတယ်
- အထက်ပါ code မှာ တော့ error မရှိတဲ့အတွက် try { } ထဲက code တွေ ရေးထားတဲ့အတိုင်း အလုပ် လုပ်နေမှာ ဖြစ်ပါတယ်
##
### Try to catch error

```js
const getData = async() => {
 try{
  const url = "https://fakestoreapi.com/productsffffff";
  const response = await fetch(url);
  const data = await response.json();
  console.log(data);
} catch (error) {
  console.error("error occuerd :" ,error);
 }
};
getData();
```
- url ကို အမှားပေးထားပြီး error ကို catch လုပ်ကြည့်ထားတာဖြစ်ပါတယ် 
