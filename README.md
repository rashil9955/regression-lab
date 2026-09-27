# Regression!

### A hands-on machine learning playground, with a comic-book twist.

I was learning machine learning and wanted to visualize what the equations were doing. I could read a linear regression formula, but I wanted to see what happened when I changed a weight, added another input, or made the data noisier.

That curiosity became **Regression!**: a small interactive website where I can move sliders and watch the math take shape. It starts with a line, moves into a plane, and uses slices to explore relationships in higher dimensions. The comic style keeps it playful while I experiment.

## What you can explore

- **2–5 model parameters:** adjust the intercept and up to four input weights.
- **Live regression graphs:** see a 2D line, a 3D plane, or a slice through a higher-dimensional model.
- **The loss bowl:** explore mean squared error as a surface over the intercept and first weight.
- **Noisy data:** change the noise level, choose 40, 80, or 150 observations, and shuffle the dataset.
- **The best fit:** calculate the least-squares solution and compare it with your own choices.
- **Prediction errors:** display the distances between the observations and the model.
- **Interactive 3D views:** drag to rotate and scroll to zoom, with keyboard controls too.

## The idea that helped it click

Adding inputs does not make linear regression itself curved. One input gives a line; two inputs give a plane. The **bowl** comes from plotting the squared-error loss against model parameters.

The model is:

```text
ŷ = β₀ + β₁x₁ + β₂x₂ + …
```

Here, `β₀` is the intercept, the other `β` values are weights, and the `x` values are inputs. This playground counts the intercept as one of the model parameters.

| Parameters | Inputs | Regression view |
| --- | --- | --- |
| 2 | 1 | A line in 2D |
| 3 | 2 | A plane in 3D |
| 4 | 3 | A 3D slice, holding one input fixed |
| 5 | 4 | A 3D slice, holding two inputs fixed |

For higher-dimensional slices, the dots are adjusted to the selected slice using the current model weights. The reported mean squared error always uses the original observations and all active inputs.

The loss landscape varies `β₀` and `β₁` while holding other weights fixed. Its white point marks the minimum of that slice. **Find the best fit** optimizes all active parameters together.

## Run it locally

No package installation or build step is needed. With Python 3 installed:

```bash
git clone https://github.com/rashil9955/regression-lab.git
cd regression-lab
python3 -m http.server 4173 --directory dist
```

Open [localhost:4173](http://localhost:4173).

The application runs in the browser using HTML, CSS, JavaScript, and Canvas. Google Fonts supplies the typefaces; fallback fonts are used when unavailable. The example data is generated locally.

## Try this first

1. Start with **2 parameters** and change **Weight 1**. Watch the line tilt.
2. Increase **Data noise** and turn on **Show errors**.
3. Click **Find the best fit** and watch the MSE fall.
4. Choose **3 parameters**, then drag the plane to inspect it.
5. Switch to **Loss landscape** to see where the bowl comes from.
6. Choose **4 or 5 parameters** and move the extra-input sliders to explore different slices.

Focus the graph and use the arrow keys to rotate 3D views, or `+` and `−` to zoom. **Reset view** restores the camera.

## Project structure

```text
dist/
├── index.html   # Page structure and explanations
├── style.css    # Comic-inspired styling and responsive layout
└── app.js       # Data generation, regression, controls, and plotting
```

The least-squares calculation was checked for all supported parameter counts, including exact coefficient recovery with noiseless data and minimum-error behavior with noisy data. The interface was also checked at desktop and mobile widths.

Built while learning, to make the connection between an equation and its graph easier to see.
