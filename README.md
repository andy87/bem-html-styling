
## Пример моей вёрстки.  

* [hyper-guard](html.andy87.ru/hyper-guard/index.html)
* [city-dynamic](html.andy87.ru/intermobility/city-dynamic/index.html)
* [evacharge](html.andy87.ru/intermobility/evacharge/index.html)
* [is-telecom](html.andy87.ru/intermobility/is-telecom/index.html)
* [pampers-docdeti](html.andy87.ru/pampers-docdeti.pgbonus/index.html)
* [energoprof-group](https://energoprof-group.ru)

## Как я верстаю?  

Я соблюдаю принцып: "Блок, Элемент, Модификатор".  

Вёрстка, разумеется, делится на логические блоки, с именами классов: `block__####`. Внутри (`block__####`) элементы 
именуются согласно предназнаяению и назначения элемента, по шаблону `b_####--????`. Элементы могут иметь модификаторы (
дополнительный клас изменяющий или/и дополняющий CSS свойства элемента), коотрые начинается с символов `__` 
 и имеют вид `__****`.

**Legend:**  
`####` - имя блока (одно-два слова)  
`????` - имя элемента (одно-два слова)  
`****` - имя модификатора (одно-два слова)

#### Пример блока `header` c BEM именованием:  
```HTML
<div class="block__header">
    
    <div class="b_header--wrapper">
        
        <a class="b_header--link __logo" href="/">
            <img class="b_header--img" src="/img/block/header/logo.png" alt="" />
        </a>
        
        <div class="b_header--layout">
            <a class="b_header--link" href="/">
                <i class="ico __mail"></i>
                Написать письмо
             </a>
        </div>
        
    </div>
    
</div>
```

В примере блок `header`. его элемент ссылка(`b_header--link`) имеет модификатор `__logo`.  
Так же в блоке используется компонент `ico` с модификатором `__mail`.

Имён может быть множжество, но все они обязаны соответсвовать структуре документа или назначению блока/элемента.
Хотя иногда допустимо именовать элемент не согласно структуре, а по его назначению:  
`b_header--img` --> `b_header--logo`

**Каждый блок:**
- подобен микросервису, показывает свои данные (живёт не зная о других блоках)
- имеет собственный файл стилей(less)  

-----  

**Преимущества:**
- **Конкретика.** У блоков и элементов персональные имена, не спутать с другими блоками.
- **нет перегружености** имён классов (когда у 1 элемента более 3 классов)
- **Переиспользование.** *Легко переиспользовать как весь блок так и отдельные его элементы*
- HTML код даёт **полное представление** *по коду без проблем понятно на какой элемент смотришь*
- **Удобство разработки адаптива.** *перезатираются свойства единственного класса, 
автодополнение: в IDE показывает только нуобходимые классы, поиск в IDE: можно легко найти нужный блок, 
при изменении имени можно использовать быстрое удаление через Ctrl +  Backspace оно удалит всё до знака "--", 
так же с другой стороны Ctrl + Del .*
- **Удобство рефакторинга.** *Не задевается ни какой другой блок, редактиркется только 1 блок / элемент*
- **Удобство взаимодействия** *Общаясь с другим разработчиком понятно о каком блоке идёт речь*
- **Минификация кода** с повторяющимися именами будет выполнена успешней
- Используя имена блоков и элементов в коммитах **Описание коммитов** становится надлядней и понятней
- "**Простота восприятия проекта целиком**".

-----  

**Недостатки:**
- иногда не хватает имён блокам и модификаторам.  
- для получения преимуществ требуется строгое соответствие рекомендациям.  
- каждому блоку надо выбрать подходящее и уникальное имя (хотя это общяя проблема).

-----  

**Пример имён элементов для блока `.block__name`:**  

.b_name--box  
.b_name--layer  
.b_name--layout  
.b_name--overlay  
.b_name--window  
.b_name--ico  
.b_name--img  
.b_name--pic  
.b_name--text ( .__small, .__large, .__total )  
.b_name--header  
.b_name--title  
.b_name--body  
.b_name--footer  
.b_name--title  
.b_name--form  
.b_name--label  
.b_name--button  
.b_name--input   
.b_name--preview  
.b_name--reward  
.b_name--preview
.b_name--......  и др.

-----  
### Возможная структура ресуосов  

### By Type  
**Удобство:** Ресурсы расположены по одинаковому "маршруту"  
Все ресурсы сгруппированы по типу (все скрипты в одном месте, все файлы стилей одном месте и т.д.) 
Ресурсы каждого блока расположены по одному path. В скриптах и стилях отсутствуют постороннии элементы.  
#### *пример:*  
```
┠📁 source 
┃ ┠📁 views 
┃ ┃ ┠📄 banner.tpl
┃ ┃ ┗📄 menu.tpl
┃ ┠📁 style 
┃ ┃ ┠📄 banner.less
┃ ┃ ┗📄 menu.less
┃ ┗📁 script 
┃   ┠📄 banner.js
┃   ┗📄 menu.js
┗📁 web 
  ┠📁 img 
  ┃ ┠📁 banner 
  ┃ ┃ ┠📄 background.png
  ┃ ┃ ┗📄 icon.svg
  ┃ ┗📁 menu 
  ┃   ┠📄 background.png
  ┃   ┗📄 icon.svg
  ┗📁 css 
    ┠📄 banner.css
    ┗📄 menu.css
... и так далее  
```
### By Block  
**Удобство:** Абсолютное понимание где лежат ресурсы блока.  
#### *пример:*  
```
┗📁 source 
  ┗📁 block 
     ┠📁 banner 
     ┃ ┠📄 banner__view.tpl
     ┃ ┠📄 banner__script.js
     ┃ ┠📄 banner__style.less
     ┃ ┠📄 banner__style.css
     ┃ ┗📁 img 
     ┃   ┠📄 background.png
     ┃   ┗📄 icon.svg
     ┗📁 menu 
       ┠📄 menu__view.tpl
       ┠📄 menu__script.js
       ┠📄 menu__style.less
       ┠📄 menu__style.css
       ┗📁 img 
         ┠📄 background.png
         ┗📄 icon.svg
 ... и так далее
```

-----  
