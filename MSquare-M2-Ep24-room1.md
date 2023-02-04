## MSquare Programing Fullstack Course
### Episode-*24* 
### Summary For `Room(1)` intermediate Class
##
### Upload Simple NodeJS CURD to Render web server
- အရင်ဆုံ ပြီးခဲ့တဲ့ သင်ခန်းစာမှာ လေ့ကျင့်ထားခဲ့တဲ့ node curd project ကို  github မှာ repo တစ်ခုလုပ်ပြီး တင်ထားပေးပါ။
- https://dashboard.render.com/ ကို သွားပါ။
- singin မှာ  github  ကိုရွေးပေးပါ
- Authorize Render ကို ကလစ်ပါ။
- လိုအပ်သည်များကို ဖြည့်ပေးပါ
- Almost there ကို ရောက်ရင် မိမိရဲ့ emial ထဲမှာ render ကပို့လိုက်တဲ့ Activate link ကို ကလစ်ပေးလိုက်ပါ။
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/render1.png)

- `New +` >> Web Server ကို ရွေးပါ။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/render2.png)

- github မှာ တင်ထားတဲ့ repo များ ပေါ်လာပါလိမ့်မည်
- မပေါ်လာပါက + connect account မှာ နှိပ်ပြီး install လုပ်ပေးပါ။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/render3.png)

- github repo များ ပေါ်လာပါက မိမိ အစောပိုင်းက တင်ထားတဲ့ repo ကို ရှာပြီး connect လုပ်လိုက်ပါ

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/render4.png)

- Name မှာ ကြိုက်တာထည့်ပါ
- Environment မှာ node
- start command မှာ  node server-file name ရေးပေးပါ(eg: `node server.js` )
- cerate web service ကို နှိပ်လိုက်ပါ။

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/render5.png)

- server deploy လုပ်နေကြောင်း ပြပေးလိမ့်မည်။
- အင်တာနက်လိုင်းပေါ် မူတည်ပြီး အချိန် ကြာတက်ပါတယ်
- ပြီးသည်အထိ စောင့်ပေးလိုက်ပါ။
- အောက်ကပုံလို live လေး ပေါ်လာပါက အဆင်ပြေပါပြီး

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/render6.png)

- server လုပ်ပြီးသွားပြီးဆိုပါ project အောက်မှာ link တစ်ခု ပြနေပါလိမ့်မယ်
- ထို link ကနေတစ်ဆင့် မိမိရဲ့ simple node curd ကို website အနေနဲ့ သွား၀င်ကြည့်လို့ ရပါပြီး

![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/render7.png)

- ၀င်ကြည့်လို့ ရနေပေမယ့်လဲ ကျနော်တို့ရဲ့ CURD တွေက အလုပ်မလုပ်ဖြစ်နေတာကို ကြုံရမှာပါ။
- ထို  error ကို ဖြေရှင်းဖို့ အတွက် script.js မှာ fetch နဲ့ request လုပ်တဲ့အခါ သုံးတဲ့ url ကို သွားပြင်ပေးရမှာ ဖြစ်ပါတယ်
- fetch ( http://localhost:3000/users ) ကို မိမိရဲ့ render website url နဲ့ အစားထိုးပေးရမှာဖြစ်ပါတယ်။
- ဒါကြောင့် srcipt.js မှာ လက်ရှိ ကျနော့ရဲ့ render url ဖြစ်တဲ့ https://amrcurd233.onrender.com/  ကို http://localhost:3000 နေရာမှာ အစားထိုးပြီး  github repo မှာ သွားပြင်လိုက်ပါတယ်
- ( **eg:** fetch (  https://amrcurd233.onrender.com/users ) )
- github မှာ ပြင်လိုက်တာနဲ့ တစ်ပြိုင်နက်ထဲ render က auto deploy လုပ်ပေးပါလိမ့်မယ်
- ပထမပုံမှာ deploy in progress ဆိုပြီး အလုပ်နေတာ ပြနေရင်  စောင့်ပေးလိုက်ပါ
- ဒုတိယပုံလို succussed လို့ပြပြီ ဆိုရင် ကိုယ့်ရဲ့ render link ကို ပြန်၀င်ကြည့်ပါက CURD ဟာ ရေးထားတဲ့ အတိုင်း အလုပ်လုပ်နေပါပြီး 
- အဆင်မပြေသေးပါက refresh နှစ်ခေါက် သုံးခေါက် လုပ်ပေးကြည့်ပါ။
![enter image description here](https://raw.githubusercontent.com/Aungmyanmar32/msquare-fullstack-m2/main/render8.png)

- ကျနော့ရဲ့ render url ဖြစ်တဲ့ https://amrcurd233.onrender.com/  ကို ၀င်ကြည့်ကြည့်ပါက
- GET POST PUT DELETE ( CURD ) လုပ်လို့ရသွားပါပြီ

> သတိပြုရန် 
> **render မှာ web server deploy လုပ်တဲ့ အချိန် တစ်ခါတရံ အရမ်းကြာတက်ပါတယ်။error မပြမချင်း စိတ်ရှည်ရှည်နဲ့ စောင့်ပေးပါ**
> 
