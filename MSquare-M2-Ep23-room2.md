## MSquare Programing Fullstack Course
#### Episode-11 Summary
ဒီနေ့သင်တန်းမှာတော့

**Git** အကြောင်းကို ပြန်လည် လေ့လာသွားမှာပါ။

## 

- git ကို အသုံးပြုချင်ရင် မိမိရဲ့ project folder ထဲမှာ git ကို init လုပ်ပေးရပါမယ်။
```properties
git init
```
##
- Git မှာ အခြေအနေ သုံးခု ရှိပါတယ်
-  `git status` ဖြင့် လက်ရှိ မည်သည့်အခြေအနေ ရောက်နေကြောင်း ကြည့်နိုင်သည်။
 1. wotking tree
 - ရေးထားသောကုဒ်တွေကို git ဖြင့် မှတ်တမ်းမတင်ရသေးပဲ အလုပ်လုပ်နေဆဲ အခြေအနေ
```js
Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (master)
$ git status
  On branch master

  No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        index.html
nothing added to commit but untracked files present (use "git add" to track)
```
##
2. Staging Area
- မှတ်တမ်းတင်ရန် အဆင်သင့်ဖြစ်နေသော အခြေအနေ
- working tree မှ Staging Areaသို့ သိမ်းမယ့် မှတ်တမ်းများကို ပို့ရန် `git add filename` ကို အသုံးပြုပါ။
```console
Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (master)
$ git add index.html

Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   index.html

```
##
3.  commited 
- ( မှတ်တမ်းတင် သိမ်းလိုက်ပြီးသော အခြေအနေ)
- Staging Area မှ commited သို့ သိမ်းမယ့် မှတ်တမ်းများကို သိမ်းရန် `git commit -m "Your message"` ကို အသုံးပြုပါ။
```properties
Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (master)
$ git commit -m "started project"
[master (root-commit) e442c7b] started project
 1 file changed, 31 insertions(+)
 create mode 100644 index.html

Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (master)
$ git log --oneline
e442c7b (HEAD -> master) started project
```
- မှတ်တမ်းတင်ထားသည်များ (commit history )ကို `git log` **or** `git log --oneline` ဖြင့် စစ်ဆေးကြည့်ရှုနိုင်သည်။
## 
### Git barach / Git merge 
git branch တစ်ခု ကနေ နောက်တစ်ခြား branch တစ်ခုကို သွားချင်ရင် `git switch branch-name` ကို သုံးပါတယ်။<br>
ခု ကျနော်တို့မှာက branch တစ်ခုပဲရှိတဲ့ အတွက် နောက်ထပ် branch တစ်ခု ပြုလုပ်ပြီးမှ လက်ရှိ branch ကနေ သွားလို့ရမှာပါ။<br>
ဒါကြောင့်မလို့ ကျနော်တို့က `git switch -c new-branch-name` ကို သုံးရပါမယ်။ဒီ command က **ပေးလိုက်တဲ့ နာမည်နဲ့ branch အသစ်တစ်ခု လုပ်**ပေးပြီး ၊ ထို **အသစ်လုပ်တဲ့ branch ထဲ တစ်ခါထဲ ၀င်ရောက်ပေးသွားမှာ** ဖြစ်ပါတယ်။<br>
ဒါ့အပြင် **လက်ရှိ branch က commit history တွေကို အကုန်ကူးယူပြီး အသစ်လုပ်တဲ့ branch ထဲ သွားထည့်ပေး**သွားမှာပါ။
```properties
Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (master)
$ git switch -c feat/sidebar
Switched to a new branch 'feat/sidebar'

Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (feat/sidebar)
$ git log --oneline
e442c7b (HEAD -> feat/sidebar, master) started project
```
##
### git branch 
- မိမိ ဘယ် အကိုင်းထဲ ရောက်နေသလဲ သိချင်ရင် git branch ကို သုံးပါတယ်။
- အကိုင်း တစ်ခု ကနေ တစ်ခု သို့ သွားချင်ရင် git switch branch-name ကို သုံးရပါမယ်
```properties
Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (feat/sidebar)
$ git branch
* feat/sidebar
  master

Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (feat/sidebar)
$ git switch master
Switched to branch 'master'

Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (master)
$ 
```

  ### git merge
  branch တွေကို ပေါင်းဖို့အတွက် သုံးပါတယ်။
  #### `git merge branch-name` လို့ ရေးပေးရပါတယ်။
  ```properties
  Admin@MSquare MINGW64 ~/Desktop/exercises/googleMeet (master)
$ git merge feat/sidebar 
Updating e442c7b..417e492
Fast-forward
 index.html | 1 +
 1 file changed, 1 insertion(+)
```
  ##
  ### merge conflict

 အောက်က exampleကို လေ့လာကြည့်ရအောင်
>Example

![enter image description here](https://github.com/Aungtat/MSquareFullstackCourseSummary/blob/main/git2-7.jpg?raw=true)
<br>
ပုံပါ အတိုင်း branch နှစ်ခုမှာ မတူညီတဲ့ commit တစ်ခုစီ မှတ်တမ်းတင်ထားပါတယ်။
git merge လုပ်လိုက်တဲ့ အခါမှာတော့ အောက်ကပုံအတိုင်း conflict ပြဿနာ  ဖြစ်လာပါပြီး။<br>
![enter image description here](https://github.com/Aungtat/MSquareFullstackCourseSummary/blob/main/git2-9.jpg?raw=true)
<br>
merge conflict ဖြစ်လာပြီးဆိုရင်တော့ မြားပြထားတဲ့နေရာမှာ
လိုချင်တဲ့အတိုင်း ရွေးချယ်ကာ  မလိုအပ်တဲ့ ကုဒ်တွေကို ဖျက်ပြီး git commit ပြန်လုပ်ကာ branch တွေကို merge  လုပ်ပေးရမှာ ဖြစ်ပါတယ်။
##
##
### GitHub repository 
- github တွင် readme file မပါပဲ repo တစ်ခု create လုပ်ပါက empty repo ဖြစ်ပြီး
- readme ဖိုင် တစ်ခါတည်း ထည့် ပြီး create လုပ်ပါက git commit တစ်ခု ရှိပြီးဖြစ်သော repo ဖြစ်ပါတယ်။
##
### clone github repo
- မိမိတို့ရဲ့ github repo SSH link ကို copy လုပ်ပါ။
- project folder မှာ terminal ထဲ `git clone SSH-link` လို့ ရေးပြီး github repo တစ်ခုကို မိမိစက်ထဲ ပုံတူပွား ချိတ်ဆက်နိုင်သည်။
##
### Push back to github repo
- clone လုပ်ထားတဲ့ folder ထဲမှာ  ထည့်ချင်တဲ့ file/ပြောင်းလဲမှု/ပြင်ဆင်မှု ကို စိတ်ကြိုက်ပြုလုပ်ပြီး 
github ပေါ်ပြန်တင်လိုပါက မိမိစက်ထဲမှာ  commit တစ်ခု အရင်မှတ်တမ်းတင်ပါ.
- အဆင်သင့် ဖြစ်ပြီး ဆိုပါက `git push` ဖြင့် နောက်ဆုံးလုပ်ဆောင်ချက်များကို github repo ဆီသို့ တင်နိုင်ပါသည်။
