# Fourier Transform Visualization with p5.js

This project provides a visualization of the **Fourier Transform** using **p5.js**. It demonstrates how a time-domain signal is transformed into its frequency components and displays both the signal and its frequency spectrum.

## Features

- **Real-Time Visualization**: View both the time-domain signal and its frequency-domain representation.
- **Interactive Controls**: Modify the input signal's parameters and see the Fourier Transform update live.
- **Signal Composition**: Combine different frequency components to create complex signals and observe how their frequency spectra change.

## Demo

You can view the live demo by visiting the GitHub Pages link (if applicable), or by opening the `index.html` file in your browser.

## Installation

### Clone the repository

To get started with this project, clone the repository to your local machine:

```bash
git clone https://github.com/Drele11ven/Fourier-transform.git
```

### Navigate to the project directory

Once cloned, navigate to the project directory:

```bash
cd Fourier-transform
```

### Open the project in your browser

Open the `index.html` file in your browser to see the visualization in action.

```bash
open index.html
```

## Usage

Once the `index.html` is opened in your browser, you will see a real-time display of the signal and its Fourier Transform.

### Controls

- Modify the **frequency** and **amplitude** of sine waves to change the time-domain signal.
- The graph updates in real-time to show how the signal is transformed into its frequency-domain representation.

## Code Example

Here's a basic overview of how the Fourier Transform is applied using **p5.js** in the project.

```javascript
let signal = [];
let frequencies = [];
let transformedSignal = [];

function setup() {
  createCanvas(800, 400);
  frameRate(30);
  // Initialize the signal array with a sine wave
  for (let i = 0; i < width; i++) {
    signal.push(sin(TWO_PI * 5 * i / width)); // A 5 Hz sine wave
  }
}

function draw() {
  background(255);

  // Update and display the time-domain signal
  stroke(50);
  noFill();
  beginShape();
  for (let i = 0; i < signal.length; i++) {
    vertex(i, height / 2 + signal[i] * 100);
  }
  endShape();

  // Perform the Fourier Transform
  transformedSignal = fourierTransform(signal);

  // Display the frequency-domain signal
  stroke(255, 0, 0);
  beginShape();
  for (let i = 0; i < transformedSignal.length; i++) {
    vertex(i, height / 2 - transformedSignal[i] * 100);
  }
  endShape();
}

// Function to perform the Fourier Transform
function fourierTransform(signal) {
  let transformed = [];
  for (let i = 0; i < signal.length; i++) {
    let sum = 0;
    for (let j = 0; j < signal.length; j++) {
      sum += signal[j] * cos(TWO_PI * i * j / signal.length);
    }
    transformed.push(sum / signal.length);
  }
  return transformed;
}
```

## Contributing

I welcome contributions! If you would like to contribute to this project, please fork the repository and submit a pull request with your changes.

### Steps to Contribute:

1. Fork the repository.
2. Clone your forked repository to your local machine.
3. Create a new branch for your feature or bug fix.
4. Make your changes and commit them.
5. Push your changes to your forked repository.
6. Submit a pull request.
