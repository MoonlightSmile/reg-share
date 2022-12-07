---
theme: seriph
background: /bg.jpeg
class: text-center
highlighter: shiki
lineNumbers: true
info: 正则分享
drawings:
  persist: false
css: unocss
title: 正则表达式
---


# 正则表达式



<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
     <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
</div>

---
layout: image-right
image: /apple.jpeg
---

## 找找苹果在哪里
<ol>
<li class="py-4" v-click>在记忆中寻找苹果的特征</li>
<li class="pb-4" v-click>在图片里面找符合这个特征的物体</li>
</ol>

---
layout: image-right
image: /600.jpeg
---

# 找找文字中的苹果在哪里

```ts {all|1|4|6|8|9|10}
苹果的种类繁多，有红富士、小水晶、灯笼等。
但最好吃的还是红富士。
而红富士比其他种类更香更甜，营养价值也更上一层，
人们有一句话：“一天一苹果，医生远离我。”
这句话可不是浪得虚名的，经专实研究。
表明苹果的氨基酸、血活分子以及20多种营养素，
可平衡维持人体的健康。
而且苹果的粗纤维，可以输通肠胃，使肠胃不会造成炎症。
苹果的吃法是五花八门，可以生吃‘榨汁、以及煮糖水等。
苹果不仅美味，而且价格便宜，
平均每千克6元，谈得上物美价廉了。
```

<!--

[测试](https://regex101.com/r/NKPh1E/1)

-->

---
layout: cover
---

# 正则

正则表达式是一组由字母和符号组成的特殊文本,
<br/>
它可以用来从文本中找出满足你想要的格式的句子。

---

# 元字符

|元字符|描述|例子|
|:----:|----|----|
|.|句号匹配任意单个字符除了换行符。|https://regex101.com/r/xc9GkU/1|
|[ ]|字符种类。匹配方括号内的任意字符。|https://regex101.com/r/2ITLQ4/1|
|[^ ]|否定的字符种类。匹配除了方括号里的任意字符|https://regex101.com/r/nNNlq3/1|
|*|匹配>=0个重复的在*号之前的字符。|https://regex101.com/r/7m8me5/1|
|+|匹配>=1个重复的+号前的字符。|https://regex101.com/r/Dzf9Aa/1|
|?|标记?之前的字符为可选.|https://regex101.com/r/kPpO2x/1|

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

|元字符|描述|例子|
|:----:|----|----|
|{n,m}|匹配num个大括号之前的字符<br/>或字符集 (n <= num <= m).|https://regex101.com/r/Gdy4w5/1|
|(xyz)|字符集，匹配与 xyz 完全相等的字符串.|https://regex101.com/r/tUxrBG/1|
|&#124;|或运算符，匹配符号前或后的字符.|https://regex101.com/r/fBXyX0/1|
|&#92;|转义字符,用于匹配一些保留的字符<br/> <code>[ ] ( ) { } . * + ? ^ $ \ &#124;</code>|https://regex101.com/r/DOc5Nu/1|
|^|从开始行开始匹配.|https://regex101.com/r/jXrKne/1|
|$|从末端开始匹配.|https://regex101.com/r/t0AkOd/1|

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# 简写字符集

|简写|描述|
|:----:|----|
|.|除换行符外的所有字符|
|\w|匹配所有字母数字，等同于 `[a-zA-Z0-9_]`|
|\W|匹配所有非字母数字，即符号，等同于： `[^\w]`|
|\d|匹配数字： `[0-9]`|
|\D|匹配非数字： `[^\d]`|
|\s|匹配所有空格字符，等同于： `[\t\n\f\r\p{Z}]`|
|\S|匹配所有非空格字符： `[^\s]`|

---

# 简写字符集

|简写|描述|
|:----:|----|
|\f|匹配一个换页符|
|\n|匹配一个换行符|
|\r|匹配一个回车符|
|\t|匹配一个制表符|
|\v|匹配一个垂直制表符|
|\p|匹配 CR/LF（等同于 `\r\n`），用来匹配 DOS 行终止符|

---

# 零宽度断言（前后预查）


|符号|描述|
|:----:|----|
|[?=](https://regex101.com/r/0PJcHu/1)|正先行断言-存在|
|?!|负先行断言-排除|
|[?<=](https://regex101.com/r/cEAbUE/1)|正后发断言-存在|
|?<!|负后发断言-排除|

实际应用：https://regex101.com/r/6kEk3L/1

---

# 标志

|标志|描述|
|:----:|----|
|i|忽略大小写。|
|g|全局搜索。|
|m|多行修饰符：锚点元字符 `^` `$` 工作范围在每行的起始。|

---

# Q&A