## ✅ Image Slider Setup Guide

### 🔧 **Step 1: Create the Project Folder**

1. Create a folder on your desktop or wherever you like, e.g.:

   ```
   ImageSliderProject
   ```

---

### 📄 **Step 2: Create the HTML File**

1. Inside that folder, create a new file:

   ```
   index.html
   ```

2. Open `index.html` in a text editor (e.g., Notepad, VS Code, Sublime Text).

3. Paste the following code into `index.html`:

   *(This is a complete working example of the slider)*

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8" />
     <meta name="viewport" content="width=device-width, initial-scale=1.0" />
     <title>Image Slider</title>
     <style>
       body {
         margin: 0;
         font-family: Arial, sans-serif;
         background: #f0f0f0;
         display: flex;
         justify-content: center;
         align-items: center;
         height: 100vh;
       }

       .slider {
         position: relative;
         width: 800px;
         height: 400px;
         overflow: hidden;
         box-shadow: 0 0 10px rgba(0,0,0,0.5);
         background: #000;
       }

       .slides {
         display: flex;
         width: 100%;
         height: 100%;
         transition: transform 0.5s ease-in-out;
       }

       .slide {
         min-width: 100%;
         height: 100%;
         object-fit: cover;
       }

       .prev, .next {
         position: absolute;
         top: 50%;
         transform: translateY(-50%);
         font-size: 2rem;
         color: white;
         background-color: rgba(0,0,0,0.5);
         border: none;
         cursor: pointer;
         padding: 10px 15px;
         z-index: 10;
       }

       .prev {
         left: 10px;
       }

       .next {
         right: 10px;
       }

       .prev:hover,
       .next:hover {
         background-color: rgba(0, 0, 0, 0.8);
       }
     </style>
   </head>
   <body>
     <div class="slider">
       <div class="slides">
         <img class="slide" src="https://picsum.photos/id/1015/800/400" alt="Slide 1" />
         <img class="slide" src="https://picsum.photos/id/1016/800/400" alt="Slide 2" />
         <img class="slide" src="https://picsum.photos/id/1018/800/400" alt="Slide 3" />
       </div>
       <button class="prev">&#10094;</button>
       <button class="next">&#10095;</button>
     </div>

     <script>
       let currentIndex = 0;
       const slides = document.querySelectorAll(".slide");

       function showSlide(index) {
         const totalSlides = slides.length;
         if (index >= totalSlides) currentIndex = 0;
         else if (index < 0) currentIndex = totalSlides - 1;
         else currentIndex = index;

         const offset = -currentIndex * 100;
         document.querySelector(".slides").style.transform = `translateX(${offset}%)`;
       }

       function nextSlide() {
         showSlide(currentIndex + 1);
       }

       function prevSlide() {
         showSlide(currentIndex - 1);
       }

       setInterval(() => {
         nextSlide();
       }, 3000);

       document.querySelector(".next").addEventListener("click", nextSlide);
       document.querySelector(".prev").addEventListener("click", prevSlide);

       showSlide(currentIndex);
     </script>
   </body>
   </html>
   ```

---

### 🌐 **Step 3: Open in Your Browser**

1. Save the `index.html` file.
2. Open the project folder.
3. Double-click `index.html` to open it in your default web browser.

> 💡 You should now see a working image slider with 3 images rotating every 3 seconds, and navigation arrows!

---

### 🖼️ **Optional: Use Your Own Images**

Replace the image URLs:

```html
<img class="slide" src="https://picsum.photos/id/1015/800/400" />
```

With your own images, like:

```html
<img class="slide" src="images/photo1.jpg" />
```

And store those images inside an `images/` folder next to `index.html`.
