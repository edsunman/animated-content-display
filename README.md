This project uses Vite. To run project locally use:

```
npm run dev
```

To build for prodution use:

```
npm run build
```

This will create the bundled javascript file in /dist/assets which creates a webcomponent that can be added to an existing application with an `<animated-paper />` tag.

See /dist/index.html as an example.

## Images

Change the envioment variable VITE_IMAGE_FILEPATH in .env to specify where the images are located.

## Fonts

Include in the HTML head to import fonts:

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
    href="https://fonts.googleapis.com/css2?family=Crimson+Text:ital,wght@0,400;0,600;0,700;1,400;1,600;1,700&family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap"
    rel="stylesheet"
/>
```

Fonts and color can be controlled with css variables:

```css
:root {
    --paper-scroll-color: #5d5b5b;
    --paper-title-color: #303030;
    --paper-body-color: #303030;
    --paper-title-font: "Crimson Text", serif;
    --paper-body-font: "Inter", sans-serif;
    * {
        margin: 0;
    }
}
```
