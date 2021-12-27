
## Пример моей вёрстки.  

* [hyper-guard](http://html.andy87.ru/hyper-guard/index.html)
* [city-dynamic](http://html.andy87.ru/intermobility/city-dynamic/index.html)
* [evacharge](http://html.andy87.ru/intermobility/evacharge/index.html)
* [is-telecom](http://html.andy87.ru/intermobility/is-telecom/index.html)
* [pampers-docdeti](http://html.andy87.ru/pampers-docdeti.pgbonus/index.html)
* [energoprof-group](https://energoprof-group.ru)

## Как я верстаю?  

Я соблюдаю принцып: "Блок, Элемент, Модификатор".  

У каждого тега имеется аттрибут `class`, и в коде он первый из аттрибутов.  
Вёрстка делится на логические блоки, каждый основной блок логической части вёрстки получает 
имя класса вида: `block__####`.  
Внутри (`block__####`) элементы именуются согласно типу элемента или согласно его сути, 
по шаблону `b_####--????` ( имя класса содержет имя блока ).  
Элементы могут иметь модификаторы ( дополнительный клас изменяющий или/и дополняющий CSS 
свойства конкретного элемента), их имена имеют вид `__****`.  
Блоки, разумеется, могут быть вложены друг в друга.  

**Legend:**  
`####` - имя блока (одно-два слова)  
`????` - имя элемента (одно-два слова)  
`****` - имя модификатора (одно-два слова)

**компоненты.**  
Как модификаторы не привязанные к конкретному блоку и используется как обычный класс.  
Пример:
```css
.none { display: none; } 
.t-left { text-align: left; } 
.f-left { float: left; } 
```

#### Наглядный пример HTML кода с BEM именованием:
```HTML
<div class="block__content">
    <div class="b_content--wrapper">

      <header class="block__header">
        <div class="b_header--wrapper">
          
          <a class="b_header--link __logo" href="/">
            <img class="b_header--img" src="/img/blocks/header/logo.png" alt=""/>
          </a>
          
          <div class="b_header--layout">
            <a class="b_header--link" href="/">
              <i class="ico __mail"></i>
              Написать письмо
            </a>
          </div>
          
        </div>
      </header>

      <div class="block__welcome">
        <div class="b_welcome--wrapper">
          <div class="b_welcome--overlay">
            
            <div class="b_welcome--layer __left">
              <img class="b_welcome--img" src="/img/blocks/welcome/main.png" alt="">
            </div>
            
            <div class="b_welcome--layer __right">
              <h1 class="b_welcome--title">Title</h1>
            </div>
            
          </div>
        </div>
      </div>

      <div class="block__service">
        <ul class="b_service--wrapper">
          
          <li class="b_service--item none">
            <img class="b_service--ico" src="/img/blocks/service/ico_1.svg" alt="">
            <h3 class="b_service--title">
              first
            </h3>
            <a class="b_service--button" href="javascript:app.service.goTo( app.service.first.id );">
              Далее
            </a>
          </li>
          
          <li class="b_service--item">
            <img class="b_service--ico" src="/img/blocks/service/ico_2.svg" alt="">
            <h3 class="b_service--title">
              trade
            </h3>
            <a class="b_service--button" href="javascript:app.service.goTo( app.service.trade.id );">
              Далее
            </a>
          </li>
          
          <li class="b_service--item">
            <img class="b_service--ico" src="/img/blocks/service/ico_3.svg" alt="">
            <h3 class="b_service--title t-left">
              cabinet
            </h3>
            <a class="b_service--button" href="javascript:app.service.goTo( app.service.cabinet.id );">
              Далее
            </a>
          </li>
          
        </ul>
      </div>

    </div>
  </div>
```
В примере блок `header`. его элемент ссылка(`b_header--link`) имеет модификатор `__logo`.  
Так же в блоке используется компонент `ico` с модификатором `__mail`.

Имён может быть множжество, но все они обязаны соответсвовать структуре документа или назначению блока/элемента.
Хотя иногда допустимо именовать элемент не согласно структуре, а по его назначению:  
`b_header--img` --> `b_header--logo`

-----  

**Каждый блок:**
- подобен микросервису, показывает свои данные (живёт не зная о других блоках)
- имеет собственный файл стилей(less)  

-----  

**Преимущества:**  
- **Отсутствие привязка к тегу**.  
  SEO'шники и т.п. сколь угодно часто могут просить менять тэги с DIV на SPAN, с NAV на DIV и прочее...  

- **Персонализация элементов.**  
  У блоков и элементов персональные имена, благодаря чему элемент не спутать с другими элементами.  

- **отсутствие перегружености классов**  
  По сути у элемента может быть максимум 3 класса ( имя, модификатор, компонент).  

- **Переиспользование.**  
Соблюдая рекомандации легко переиспользовать как весь блок так и отдельные его элементы.  

- **HTML.**  
  Соблюдая рекомандации HTML код даст полное представление на какой элемент страницы ты смотришь.  

- **Адаптив.**  
  При разработке адаптива перезатираются свойства всего единственного класса.  

- **IDE.**  
  Автодополнение/Поиск/Рефакторинг при таком именовании очень кофмфортные.  

- **Взаимодействия.**  
  Общаясь с другим разработчиком вполне понятно о каком блоке идёт речь и где распологгаются его ресурсы.  

- **GIT.**  
  Используя имена блоков и элементов в коммитах ***Описание коммитов*** становится надлядней и понятней.  

-----  

**Недостатки:**
- При скудной фантазии не хватает имён блокам и модификаторам  
- каждому блоку надо выбрать подходящее и уникальное имя  
...хотя это в целом общие проблемы при вёрстке

-----  

**Пример имён основных элементов:**  

.b_name--overlay  
.b_name--layout  
.b_name--layer  
.b_name--box  
.b_name--window  
.b_name--head  
.b_name--body  
.b_name--footer  
.b_name--ico  
.b_name--img  
.b_name--pic  
.b_name--text ( модификаторы: __small __large __total )   
.b_name--title  
.b_name--header  
.b_name--form  
.b_name--label  
.b_name--button  
.b_name--input  
.b_name--preview  
.b_name--logo  
.b_name--......  и др.

-----  

## Структура ресурсов  при разработке.
Можно получить дополнительное "удобство" если при разработке проекта сформировать структуру с группировкой файлов блока, 
что бы всегда было чёркое понимание где лежат/искать файлы определённого блока. В большинстве это не доступно 
"из коропки" и при разработке с помощтю фреймворков, реализация потребует дополнительных настроек.  

### By Block  
**Удобство:** Файлы блока расположены в одном месте *при работе с блоком, в окне иерархии проекта 
не будет раскрыто несколько уровней директорий, что бы иметь доступ ко всем файлам блока*.  
#### *пример:*  
```
┗📁 source
  ┗📁 blocks
    ┠📁 banner
    ┃ ┠📄 banner__view.tpl
    ┃ ┠📄 banner__script.js
    ┃ ┠📄 banner__style.less
    ┃ ┠📄 banner__style.css
    ┃ ┗📁 img
    ┃   ┠📄 background.png
    ┃   ┗📄 icon.svg
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
  
  
В большинстве фреймворков получается структура **по типу**, в которой я бы советовал добавить в директории ресурсов 
родительскую папку `blocks` которая должна содержать файлы относящиеся исключительно к блокам, дополнительно она 
в пути к файлу укажет на причастность файла к блокам. *Если внезапно открывается файл и сразу нет представления что 
за файл открылся.*

### By Type
**Удобство:** дирректория сожержет файлы определённого типа.  
Все ресурсы сгруппированы по типу (все скрипты в одном месте, все файлы стилей одном месте и т.д.).
#### *пример:*
```
┠📁 source 
┃ ┠📁 views 
┃ ┃ ┗📁 blocks 
┃ ┃   ┠📄 banner.tpl
┃ ┃   ┗📄 menu.tpl
┃ ┠📁 styles 
┃ ┃ ┗📁 blocks 
┃ ┃   ┠📄 banner.less
┃ ┃   ┗📄 menu.less
┃ ┗📁 scripts 
┃   ┗📁 blocks 
┃     ┠📄 banner.js
┃     ┗📄 menu.js
┗📁 web 
  ┠📁 img 
  ┃  ┠📁 blocks 
  ┃  ┃ ┠📁 banner 
  ┃  ┃ ┃ ┠📄 background.png
  ┃  ┃ ┃ ┗📄 icon.svg
  ┃  ┃ ┗📁 menu 
  ┃  ┃   ┠📄 background.png
  ┃  ┃   ┗📄 icon.svg
  ┗📁 css 
    ┗📁 blocks 
      ┠📄 banner.css
      ┗📄 menu.css
... и так далее  
```
