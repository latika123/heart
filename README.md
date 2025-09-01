# Twinkling Particle Heart Animation ❤️

A beautiful, animated, and responsive twinkling heart effect created with pure HTML Canvas and JavaScript. This project renders thousands of glowing particles within a heart shape, which gently pulses to simulate a heartbeat.

## ✨ Features

*   **Generative Art**: The heart shape and particle positions are generated programmatically.
*   **Particle Animation**: Uses over 5000 individual particles, each with its own lifecycle.
*   **Twinkling Effect**: Particles fade in and out at random speeds, creating a mesmerizing twinkle.
*   **Pulsing Heartbeat**: The entire heart shape gently scales up and down, simulating a smooth heartbeat.
*   **Glow Effect**: A `shadowBlur` on the canvas context gives each particle a warm, glowing aura.
*   **Fully Responsive**: The animation automatically resizes to fit the browser window.

## 🚀 How to Use

Simply open the `heartbeat.html` file in any modern web browser. No web server or build steps are required.

## ⚙️ How It Works

The entire logic is contained within a single HTML file.

1.  **HTML Setup**: The `<body>` contains a single `<canvas>` element which acts as the drawing board for the animation.

2.  **Canvas & Context**: On window load, the script gets the 2D rendering context of the canvas.

3.  **Defining the Shape**:
    *   A `Path2D` object is used to store the heart's vector path.
    *   The `createHeartPath()` function draws a mathematically precise heart shape using `bezierCurveTo()`. The size is scaled relative to the window dimensions.

4.  **The `Particle` Class**:
    *   This class acts as a blueprint for every twinkling dot.
    *   The `constructor` finds a random `(x, y)` coordinate and loops until it finds a point that is **inside** the heart path using `ctx.isPointInPath()`. This confines all particles to the heart shape.
    *   Each particle is assigned a random size, opacity, and fade speed to ensure the effect looks natural.
    *   The `update()` method handles the fade-in/fade-out logic for the twinkling.
    *   The `draw()` method renders the particle on the canvas with its current opacity and a glow effect.

5.  **The Animation Loop**:
    *   The `animate()` function is called on every frame using `requestAnimationFrame` for smooth performance.
    *   **Fading Trail**: It clears the canvas with a semi-transparent black rectangle (`rgba(0, 0, 0, 0.1)`) on each frame. This creates a subtle motion-blur effect.
    *   **Heartbeat Pulse**: A `time` variable and `Math.sin()` are used to create a smooth, wave-like value that scales the entire canvas context up and down, producing the heartbeat effect.
    *   **Render Particles**: It iterates through all particles, calling their `update()` and `draw()` methods.

6.  **Responsiveness**: An event listener on the `resize` event updates the canvas dimensions and recalculates the heart path to fit the new screen size.

## 🔧 Customization

You can easily tweak the animation by changing the constants at the top of the `<script>` tag.

*   **Particle Density**: Change the `particleCount` variable.
    ```javascript
    const particleCount = 5000; // Increase for a denser heart, decrease for a sparser one.
    ```

*   **Color**: Modify the `rgba` values in the `Particle.draw()` method.
    ```javascript
    draw() {
        // Change the shadow color for the glow
        ctx.shadowColor = `rgba(255, 69, 0, 1)`; // e.g., 'rgba(0, 191, 255, 1)' for blue
        
        // Change the main particle color
        ctx.fillStyle = `rgba(255, 69, 0, ${this.opacity})`; // e.g., 'rgba(0, 191, 255, ...)' for blue
    }
    ```

*   **Heartbeat Speed**: Adjust the increment value for `time` in the `animate` function.
    ```javascript
    // In the animate function
    time += 0.01; // Increase for a faster beat, decrease for a slower one.
    ```

## 🛠️ Technologies Used

*   **HTML5**: For the basic structure and `<canvas>` element.
*   **JavaScript (ES6)**: For all the animation logic and DOM manipulation.
*   **Tailwind CSS**: For basic centering and styling of the body.

## 📄 License

This project is open source and available under the MIT License.