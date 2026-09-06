# Ex05 Image Carousel
## Name : JANANI S
## Date:06.09.2026

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
App.jsx
~~~
import { useState } from "react";
import "./App.css";

function App() {
  const images = [
    "https://picsum.photos/id/1015/800/500",
    "https://picsum.photos/id/1016/800/500",
    "https://picsum.photos/id/1018/800/500",
    "https://picsum.photos/id/1025/800/500",
    "https://picsum.photos/id/1035/800/500",
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const previousImage = () => {
    setCurrentIndex(
      (currentIndex - 1 + images.length) % images.length
    );
  };

  return (
    <div className="carousel-container">
      <h1>Image Carousel</h1>

      <div className="carousel">
        <button className="prev" onClick={previousImage}>
          ❮
        </button>

        <img
          src={images[currentIndex]}
          alt={`Slide ${currentIndex + 1}`}
        />

        <button className="next" onClick={nextImage}>
          ❯
        </button>
      </div>

      <p>
        Image {currentIndex + 1} of {images.length}
      </p>

      <div className="dots">
        {images.map((_, index) => (
          <span
            key={index}
            className={index === currentIndex ? "dot active" : "dot"}
            onClick={() => setCurrentIndex(index)}
          ></span>
        ))}
      </div>
    </div>
  );
}

export default App;
~~~
App.css
~~~
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f2f2f2;
}

.carousel-container {
  text-align: center;
  padding: 40px;
}

h1 {
  margin-bottom: 30px;
}

.carousel {
  position: relative;
  width: 800px;
  max-width: 90%;
  margin: auto;
  overflow: hidden;
  border-radius: 15px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
}

.carousel img {
  width: 100%;
  height: 500px;
  object-fit: cover;
  display: block;
}

.prev,
.next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  border: none;
  background: rgba(0, 0, 0, 0.6);
  color: white;
  font-size: 30px;
  padding: 10px 18px;
  cursor: pointer;
  border-radius: 50%;
}

.prev {
  left: 15px;
}

.next {
  right: 15px;
}

.prev:hover,
.next:hover {
  background: rgba(0, 0, 0, 0.9);
}

p {
  font-size: 18px;
  margin: 20px;
}

.dots {
  display: flex;
  justify-content: center;
  gap: 10px;
}

.dot {
  width: 12px;
  height: 12px;
  background: #bbb;
  border-radius: 50%;
  cursor: pointer;
}

.dot.active {
  background: #333;
}
~~~

## OUTPUT
<img width="1920" height="1080" alt="Screenshot 2026-09-06 142231" src="https://github.com/user-attachments/assets/17b060dd-9e80-48e4-b3cf-2654d7e72c22" />

## RESULT
The program for creating Image Carousel using React is executed successfully.
