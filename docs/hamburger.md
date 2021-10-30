### Hamburger Menu
<ClientOnly>
  <style lang="css">
    .mini-container {
      background-color: rgb(12, 38, 89);
      border-radius: 10px;
      padding: 10px;
      margin: 10px;
      width: 100px;
      height: 100px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .hamburger .line{
      width: 50px;
      height: 5px;
      background-color: #ecf0f1;
      display: block;
      margin: 8px auto;
      -webkit-transition: all 0.3s ease-in-out;
      -o-transition: all 0.3s ease-in-out;
      transition: all 0.3s ease-in-out;
    }

    .hamburger:hover{
      cursor: pointer;
    }

    #hamburger-1.is-active .line:nth-child(2){
      opacity: 0;
    }

    #hamburger-1.is-active .line:nth-child(1){
      -webkit-transform: translateY(13px) rotate(45deg);
      -ms-transform: translateY(13px) rotate(45deg);
      -o-transform: translateY(13px) rotate(45deg);
      transform: translateY(13px) rotate(45deg);
    }

    #hamburger-1.is-active .line:nth-child(3){
      -webkit-transform: translateY(-13px) rotate(-45deg);
      -ms-transform: translateY(-13px) rotate(-45deg);
      -o-transform: translateY(-13px) rotate(-45deg);
      transform: translateY(-13px) rotate(-45deg);
    }
    #hamburger-9{
  position: relative;
  -webkit-transition: all 0.3s ease-in-out;
  -o-transition: all 0.3s ease-in-out;
  transition: all 0.3s ease-in-out;
}

#hamburger-9.is-active{
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
  transform: rotate(45deg);
}

#hamburger-9:before{
  content: "";
  position: absolute;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  width: 70px;
  height: 70px;
  border: 5px solid transparent;
  top: calc(50% - 35px);
  left: calc(50% - 35px);
  border-radius: 100%;
  -webkit-transition: all 0.3s ease-in-out;
  -o-transition: all 0.3s ease-in-out;
  transition: all 0.3s ease-in-out;
}

#hamburger-9.is-active:before{
  border: 5px solid #ecf0f1;
}

#hamburger-9.is-active .line{
  width: 35px;
}

#hamburger-9.is-active .line:nth-child(2){
  opacity: 0;
}

#hamburger-9.is-active .line:nth-child(1){
  -webkit-transform: translateY(13px);
  -ms-transform: translateY(13px);
  -o-transform: translateY(13px);
  transform: translateY(13px);
}

#hamburger-9.is-active .line:nth-child(3){
  -webkit-transform: translateY(-13px) rotate(90deg);
  -ms-transform: translateY(-13px) rotate(90deg);
  -o-transform: translateY(-13px) rotate(90deg);
  transform: translateY(-13px) rotate(90deg);
}

#hamburger-2.is-active .line:nth-child(1){
  -webkit-transform: translateY(13px);
  -ms-transform: translateY(13px);
  -o-transform: translateY(13px);
  transform: translateY(13px);
}

#hamburger-2.is-active .line:nth-child(3){
  -webkit-transform: translateY(-13px);
  -ms-transform: translateY(-13px);
  -o-transform: translateY(-13px);
  transform: translateY(-13px);
}
</style>

<div class="mini-container">
  <div @click="e => e.currentTarget.classList.toggle('is-active')" class="hamburger" id="hamburger-1">
    <span class="line"></span>
    <span class="line"></span>
    <span class="line"></span>
  </div>
</div>

```html
<div class="hamburger" id="hamburger-1">
  <span class="line"></span>
  <span class="line"></span>
  <span class="line"></span>
</div>
  ```

```js
document.ready(function(){
  document.getElementByClassName("hamburger").click(function(){
    this.classList.toggle("is-active");
  });
});
```

```css
.hamburger {
  background-color: rgb(12, 38, 89);
  border-radius: 10px;
  padding: 10px;
  margin: 10px;
}

.hamburger .line{
  width: 50px;
  height: 5px;
  background-color: #ecf0f1;
  display: block;
  margin: 8px auto;
  transition: all 0.3s ease-in-out;
}

.hamburger:hover{
  cursor: pointer;
}

#hamburger-1.is-active .line:nth-child(2){
  opacity: 0;
}

#hamburger-1.is-active .line:nth-child(1){
  transform: translateY(13px) rotate(45deg);
}

#hamburger-1.is-active .line:nth-child(3){
  transform: translateY(-13px) rotate(-45deg);
}
```

<div class="mini-container">
  <div @click="e => e.currentTarget.classList.toggle('is-active')" class="hamburger" id="hamburger-9">
    <span class="line"></span>
    <span class="line"></span>
    <span class="line"></span>
  </div>
</div>

```css
#hamburger-9{
  position: relative;
  transition: all 0.3s ease-in-out;
}

#hamburger-9.is-active{
  transform: rotate(45deg);
}

#hamburger-9:before{
  content: "";
  position: absolute;
  box-sizing: border-box;
  width: 70px;
  height: 70px;
  border: 5px solid transparent;
  top: calc(50% - 35px);
  left: calc(50% - 35px);
  border-radius: 100%;
  transition: all 0.3s ease-in-out;
}

#hamburger-9.is-active:before{
  border: 5px solid #ecf0f1;
}

#hamburger-9.is-active .line{
  width: 35px;
}

#hamburger-9.is-active .line:nth-child(2){
  opacity: 0;
}

#hamburger-9.is-active .line:nth-child(1){
  transform: translateY(13px);
}

#hamburger-9.is-active .line:nth-child(3){
  transform: translateY(-13px) rotate(90deg);
}
```

<div class="mini-container">
  <div @click="e => e.currentTarget.classList.toggle('is-active')" class="hamburger" id="hamburger-2">
    <span class="line"></span>
    <span class="line"></span>
    <span class="line"></span>
  </div>
</div>

```css
#hamburger-2.is-active .line:nth-child(1){
  transform: translateY(13px);
}

#hamburger-2.is-active .line:nth-child(3){
  transform: translateY(-13px);
}
```
</ClientOnly>