<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.1/css/all.min.css"
      integrity="sha512-+4zCK9k+qNFUR5X+cKL9EIR+ZOhtIloNl9GIKS57V1MyNsYpYcUrUeQc9vNfzsWfV28IaLL3i96P9sdNyeRssA=="
      crossorigin="anonymous"
    />
    <link rel="stylesheet" href="style.css" />
    <title>Background Slider</title>
  </head>
  <body>
    <div class="slider-container">
      <div
        class="slide active"
        style="
          background-image: url('https://images.unsplash.com/photo-1610620746460-de78cf3d1705?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=2100&q=80');
        "
      ></div>
      <div
        class="slide"
        style="
          background-image: url('https://images.unsplash.com/photo-1609589079958-8192b9cdab91?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=2100&q=80');
        "
      ></div>
      <div
        class="slide"
        style="
          background-image: url('https://images.unsplash.com/photo-1605718665998-85fbd49c5eff?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=2100&q=80');
        "
      ></div>
      <div
        class="slide"
        style="
          background-image: url('https://images.unsplash.com/photo-1609589079852-0b1c745a71ec?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=2100&q=80');
        "
      ></div>
      <div
        class="slide"
        style="
          background-image: url('https://images.unsplash.com/photo-1604916010805-18ea15fa6d32?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=2100&q=80');
        "
      ></div>
      <button class="arrow left-arrow" id="left">
        <i class="fas fa-arrow-left"></i>
      </button>
      <button class="arrow right-arrow" id="right">
        <i class="fas fa-arrow-right"></i>
      </button>
    </div>
    <script src="script.js"></script>
  </body>
</html>

#CSS
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

body {
  font-family: 'Roboto', sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden;
  margin: 0;
  background-position: center center;
  background-size: cover;
  transition: 0.4s;
}

body::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.7);
  z-index: -1;
}

.slider-container {
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
  height: 70vh;
  width: 70vw;
  position: relative;
  overflow: hidden;
}

.slide {
  opacity: 0;
  height: 100vh;
  width: 100vw;
  background-position: center center;
  background-size: cover;
  position: absolute;
  top: -15vh;
  left: -15vw;
  transition: 0.4s ease;
  z-index: 1;
}

.slide.active {
  opacity: 1;
}

.arrow {
  position: fixed;
  background-color: transparent;
  color: #fff;
  padding: 20px;
  font-size: 30px;
  border: 2px solid orange;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
}

.arrow:focus {
  outline: 0;
}

.left-arrow {
  left: calc(15vw - 65px);
}

.right-arrow {
  right: calc(15vw - 65px);
}
#JS
const body = document.body
const slides = document.querySelectorAll('.slide')
const leftBtn = document.getElementById('left')
const rightBtn = document.getElementById('right')

let activeSlide = 0

rightBtn.addEventListener('click', () => {
  activeSlide++

  if (activeSlide > slides.length - 1) {
    activeSlide = 0
  }

  setBgToBody()
  setActiveSlide()
})

leftBtn.addEventListener('click', () => {
  activeSlide--

  if (activeSlide < 0) {
    activeSlide = slides.length - 1
  }

  setBgToBody()
  setActiveSlide()
})

setBgToBody()

function setBgToBody() {
  body.style.backgroundImage = slides[activeSlide].style.backgroundImage
}

function setActiveSlide() {
  slides.forEach((slide) => slide.classList.remove('active'))

  slides[activeSlide].classList.add('active')
}
