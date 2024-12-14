# 🎰 Крутящийся барабан 🎰

Источник: 
видео "Уроки по JavaScript. Делаем игру крутящийся барабан на Джаваскрипт" 
https://vkvideo.ru/video-101965347_456257148?sel=19460369

Барабан крутится в случайном направлении и останавливается в рандомном положении.


![7](https://github.com/user-attachments/assets/bcdcb65b-8ffd-4f41-9414-96a8f3c4939d)


https://github.com/user-attachments/assets/e82e8674-1800-4692-8560-fdea15f3ba60


# Алгоритм работы:

1. Создать нужные файлы

- создаем HTML (index.html), CSS (style.css), JS (script.js) документ в программе "WebStorm" для работы с JavaScript 
(скачать бесплатную версию https://www.jetbrains.com/webstorm/);

2. в файле index.html:

- меняем название в строке title в разделе head - Барабан

  ```html
  <title>Барабан></title>
  ```

- Указываем указатель для крутящегося барабана. А чтобы вид стрелки был симпатичный, 
берем с сайта с символами юникод (пример: https://symbl.cc/ru) 
символы стрелок и вставляем в кнопки в файле index.html в разделе body

  ```html
  <p>🢛</p>
  ```

- указатель для барабана заключаем в div, чтобы отделить её от нашего барабана. Называем класс div arrow (стрелка)

  ```html
  <div class="arrow">
    <p>🢛</p>
  </div>
  ```
  
- создаем заранее div с классом circle

  ```html
  <div class="circle"></div>
  ```

3. в файле style.css указать url (https://polechudes.tv/images/baraban.png) на изображение 

  ```css
  .circle{
    background-image: url("https://polechudes.tv/images/baraban.png");
  }
  ```

4. в файле index.html подцепляем стиль из CSS файла в разделе head

  ```html
  <link rel="stylesheet" href="style.css">
  ```

5. в файле style.css описываем изображение в .circle

  ```css
  height: 700px;
  width: 700px;
  border-radius: 9999px; /*максимально скругляем углы*/
  border-color: aqua;
  ```

6. в файле style.css ставим изображение в центр и закрепляем размер в .circle

  ```css
  background-position: center;
  background-size: cover;
  ```

![6](https://github.com/user-attachments/assets/f2a6f5a4-5f54-4085-b83c-a6d1aef924f7)


7. в файле style.css описываем стиль для стрелочки в отдельном теге p

  ```css
  p{
    position: relative;
    left: 330px; /*чем выше пиксели, тем правее стрелочка. Надо установить её по центру над изображением*/
    font-size: 70px;
  }
  ```

8. чтобы барабан крутился - в файле script.js

  ```JS
  document.getElementsByClassName('circle')[0].addEventListener('click', function(e){
    e.target.style.transform = 'rotate('+Math.random()*1000+'rad)';
  });
  ```

9. в файле index.html подцепляем скрипт из JS файла в разделе body после указанного класса барабана

  ```html
  <script src="script.js"></script>
  ```

10. в файле script.js - чтобы барабан постоянно двигался, а не при нажатии, 
указываем в getElementsByClassName - return false

  ```JS
  return false;
  ```

11. в файле style.css в .circle дополняем описание барабана - 
чтобы он сам крутился или перезапускался при нажатии и выдавал значение через 5 секунд, если нет нажатий

  ```css
  transition: 5s; /*колесо будет двигаться 5 секунд*/
  transition-timing-function: ease-in-out; /*через сколько времени можно его двигать*/
  ```

# Весь код полностью:

1. в файле script.js

```JS
document.getElementsByClassName('circle')[0].addEventListener('click', function(e){
    e.target.style.transform = 'rotate('+Math.random()*1000+'rad)';
    return false;
});
```

![2024-12-14_13-52-31](https://github.com/user-attachments/assets/200a3189-541f-4193-a41c-40c804e0d262)

2. в файле index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Барабан</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
<div class="arrow">
  <p>🢛</p>
</div>

<div class="circle"></div>
<script src="script.js"></script>
</body>
</html>
```

![2024-12-14_13-53-52](https://github.com/user-attachments/assets/8dc50d45-e6e3-4903-ba28-8a17d6371e12)

3. в файле style.css

```css
.circle{
    height: 700px;
    width: 700px;
    border-radius: 9999px; /*максимально скругляем углы*/
    border-color: aqua;
    background-image: url("https://polechudes.tv/images/baraban.png");
    background-position: center;
    background-size: cover;

    transition: 5s; /*колесо будет двигаться 5 секунд*/
    transition-timing-function: ease-in-out; /*через сколько времени можно его двигать*/
}

p{
    position: relative;
    left: 330px; /*чем выше пиксели, тем правее стрелочка. Надо установить её по центру над изображением*/
    font-size: 70px;
}
```

![2024-12-14_13-55-08](https://github.com/user-attachments/assets/c52d00d0-ac60-4a97-ab28-3f941870bdbc)
