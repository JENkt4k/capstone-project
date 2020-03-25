## html

source
```html
<div class="nav-toggle">
  <div class="nav-toggle-bar"></div>
</div>
<nav class="nav">
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">Portfolio</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
</nav>
```

your code
```html
<nav>
        <div class="logo">
            <h4>Marco Polo</h4>
        </div>
        <ul id="nav-links">
            ${links.map(link => `<li><a href="#" aria-label=${link.text}>${link.title}</a></li>`).join('')}
        </ul>
        <div class="burger">
            <div class="line1"></div>
            <div class="line2"></div>
            <div class="line3"></div>
        </div>
    </nav>`
```


```html
<div class="burger">
            <div class="line1"></div>
            <div class="line2"></div>
            <div class="line3"></div>
        </div>
<nav>
        <div class="logo">
            <h4>Marco Polo</h4>
        </div>
        <ul id="nav-links">
            ${links.map(link => `<li><a href="#" aria-label=${link.text}>${link.title}</a></li>`).join('')}
        </ul>
        
    </nav>
```



## CSS

```css
.nav {
  -webkit-transition: left 0.5s ease;
  -moz-transition: left 0.5s ease;
  -ms-transition: left 0.5s ease;
  -o-transition: left 0.5s ease;
  transition: left 0.5s ease;
  background: #28dde0;
  color: white;
  cursor: pointer;
  font-size: 2rem;
  height: 100vh;
  left: -20rem;
  padding: 6rem 2rem 2rem 2rem;
  position: fixed;
  top: 0;
  width: 20rem;
  z-index: 1;
}

.nav.expanded { left: 0; }

.nav ul {
  position: absolute;
  top: 50%;
  -webkit-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
  list-style: none;
  margin: 0;
  padding: 0;
}


.nav-toggle {
  -webkit-user-select: none;
  -moz-user-select: none;
  user-select: none;
  cursor: pointer;
  height: 2rem;
  left: 2rem;
  position: fixed;
  top: 2rem;
  width: 3.6rem;
  z-index: 2;
}

.nav-toggle:hover { opacity: 0.8; }

.nav-toggle .nav-toggle-bar,  .nav-toggle .nav-toggle-bar::after,  .nav-toggle .nav-toggle-bar::before {
  position: absolute;
  top: 50%;
  -webkit-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
  -webkit-transition: all 0.5s ease;
  -moz-transition: all 0.5s ease;
  -ms-transition: all 0.5s ease;
  -o-transition: all 0.5s ease;
  transition: all 0.5s ease;
  background: white;
  content: '';
  height: 0.4rem;
  width: 100%;
}

.nav-toggle .nav-toggle-bar { margin-top: 0; }

.nav-toggle .nav-toggle-bar::after { margin-top: 0.8rem; }

.nav-toggle .nav-toggle-bar::before { margin-top: -0.8rem; }

.nav-toggle.expanded .nav-toggle-bar { background: transparent; }

.nav-toggle.expanded .nav-toggle-bar::after, .nav-toggle.expanded .nav-toggle-bar::before {
  background: white;
  margin-top: 0;
}

.nav-toggle.expanded .nav-toggle-bar::after {
  -ms-transform: rotate(45deg);
  -webkit-transform: rotate(45deg);
  transform: rotate(45deg);
}

.nav-toggle.expanded .nav-toggle-bar::before {
  -ms-transform: rotate(-45deg);
  -webkit-transform: rotate(-45deg);
  transform: rotate(-45deg);
}
```

## The JavaScript to toggle the CSS classes when the menu is opened and closed.

```javascript
(function() {

  var hamburger = {
    navToggle: document.querySelector('.nav-toggle'),
    nav: document.querySelector('nav'),

    doToggle: function(e) {
      e.preventDefault();
      this.navToggle.classList.toggle('expanded');
      this.nav.classList.toggle('expanded');
    }
  };

  hamburger.navToggle.addEventListener('click', function(e) { hamburger.doToggle(e); });
  hamburger.nav.addEventListener('click', function(e) { hamburger.doToggle(e); });

}());
```