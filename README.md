# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

### answer
# A simple animation that fades in an element and changes its position slightly (a simple slide-in animation).
# css animation

/* Base styles for an element */

.element {

  width: 200px;
  
  height: 200px;
  
  background-color: #3498db;
  
  margin: 50px auto;
  
  opacity: 0; /* Initially hidden */
  
  transform: translateY(50px); /* Initially positioned lower */
  
  animation: slideIn 2s ease-out forwards; /* Trigger the animation */
  
}

/* Animation keyframes */

@keyframes slideIn {

  0% {
  
    opacity: 0;
    
    transform: translateY(50px);
    
  }
  
  100% {
  
    opacity: 1;
    
    transform: translateY(0);
    
  }
  
}

## JavaScript to Store and Retrieve Data from localStorage

# We'll use localStorage to store whether the animation has already been shown to the user, so it won’t show every time the page is refreshed.

# Function to store animation state in localStorage

function storeAnimationState(state) {

  localStorage.setItem('animationState', state);
  
}

# Function to check the animation state from localStorage

function getAnimationState() {

  return localStorage.getItem('animationState');
  
}

# Trigger animation based on the stored state

function triggerAnimation() {

  const animationElement = document.querySelector(".element");

  # Check if animation has been triggered before
  
  const animationState = getAnimationState();
  
  if (animationState !== "shown") {
  
  # Apply the animation class if it hasn't been shown yet
  
    animationElement.style.animation = "slideIn 2s ease-out forwards";
    
  # Store that the animation has been shown
  
    storeAnimationState("shown");
    
  } else {
  
  # If it has been shown before, just make sure it's visible
  
    animationElement.style.opacity = "1";
    
    animationElement.style.transform = "translateY(0)";
    
  }
  
}

 # Trigger animation when the page loads
 
window.addEventListener("load", triggerAnimation);

# Here’s how the animation is triggered:

    -When the page loads, the triggerAnimation function checks if the animation has already been shown (via localStorage).

    -If not, it triggers the animation and then stores the state in localStorage as "shown".

     -On subsequent page loads, the animation won’t be shown again.

# HTML Structure

<!DOCTYPE html>

<html lang="en">
  
<head>
  
  <meta charset="UTF-8">
  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  
  <title>CSS Animation with LocalStorage</title>
  
  <link rel="stylesheet" href="style.css">
  
</head>

<body>

  <!-- The element that will animate -->
  
  <div class="element"></div>

  <script src="script.js"></script>
  
</body>

</html>

Happy Coding! 💻✨
