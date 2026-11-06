HTML
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Typography & Fluid Images</title>
    <meta name="description" content="An article page demonstrating responsive typography using clamp() and fluid images with max-width.">
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header class="site-header">
        <div class="header-content">
            <span class="category-badge">Web Engineering</span>
            <h1>Responsive Typography & Fluid Images in Modern CSS</h1>
            <p class="post-meta">Published on November 7, 2026 by Atim Akhtar</p>
        </div>
    </header>

    <main class="article-container">
        <article class="content-article">
            <p class="lead">Building truly responsive web interfaces requires moving away from static pixel values. By combining scalable CSS units like <code>rem</code> and fluid font scaling with <code>clamp()</code>, we can create interfaces that adapt effortlessly to any screen size.</p>

            <h2>Understanding Fluid Typography with <code>clamp()</code></h2>
            <p>Traditional media queries for typography often lead to abrupt font-size shifts across breakpoints. The CSS <code>clamp()</code> function allows text to scale smoothly between a minimum and maximum size based on viewport width, ensuring readability on both mobile screens and ultra-wide desktop monitors.</p>

            <div class="image-wrapper">
                <img src="images/typography-showcase.jpg" alt="Responsive design mockup showing fluid typography scaling across devices" class="responsive-img">
                <figcaption>Figure 1: Fluid scaling ensures optimal line length and legibility across all viewports.</figcaption>
            </div>

            <h2>Preventing Image Overflow and Distortion</h2>
            <p>Images that lack proper constraints can easily break mobile layouts by forcing horizontal scrolling. Applying universal rules like <code>max-width: 100%</code> and <code>height: auto</code> ensures that raster images scale down proportionally within their parent containers without losing their aspect ratio.</p>

            <h2>Optimizing Line Lengths for Readability</h2>
            <p>According to typographic principles, an ideal line length for body text ranges between 45 and 75 characters. Constraining the article container with a max-width and utilizing flexible padding prevents lines from becoming overly stretched on large screens.</p>
        </article>
    </main>

    <footer class="site-footer">
        <p>&copy; 2026 Atim Akhtar. Invertis University. All rights reserved.</p>
    </footer>
</body>
</html>
CSS
/* style.css */
:root {
    --primary-color: #0284c7;
    --secondary-color: #0f172a;
    --bg-color: #f8fafc;
    --surface-color: #ffffff;
    --text-color: #334155;
    --text-muted: #64748b;
    --border-color: #e2e8f0;
    
    /* Responsive Fluid Typography via clamp(MIN, VAL, MAX) */
    --font-size-hero: clamp(1.75rem, 4vw, 2.75rem);
    --font-size-h2: clamp(1.25rem, 2.5vw, 1.75rem);
    --font-size-body: clamp(1rem, 1.2vw, 1.125rem);

    --space-sm: 8px;
    --space-md: 16px;
    --space-lg: 24px;
    --space-xl: 40px;
    
    --radius-md: 8px;
    --radius-lg: 12px;
    --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.05);
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    background-color: var(--bg-color);
    color: var(--text-color);
    line-height: 1.7;
    font-size: var(--font-size-body);
}

/* Header Styles */
.site-header {
    background-color: var(--secondary-color);
    color: var(--surface-color);
    padding: 4rem var(--space-md);
    text-align: center;
    border-bottom: 1px solid var(--border-color);
}

.header-content {
    max-width: 800px;
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    gap: var(--space-sm);
}

.category-badge {
    background-color: #e0f2fe;
    color: var(--primary-color);
    font-size: 0.75rem;
    font-weight: bold;
    padding: 4px 12px;
    border-radius: 20px;
    text-transform: uppercase;
    width: fit-content;
    margin: 0 auto;
}

.site-header h1 {
    font-size: var(--font-size-hero);
    line-height: 1.2;
    color: var(--surface-color);
}

.post-meta {
    font-size: 0.875rem;
    color: #94a3b8;
}

/* Article Container (Optimal line length constraint) */
.article-container {
    max-width: 760px;
    margin: 3rem auto;
    padding: 0 var(--space-md);
}

.content-article {
    background-color: var(--surface-color);
    border: 1px solid var(--border-color);
    border-radius: var(--radius-lg);
    padding: clamp(1.5rem, 4vw, 3rem);
    box-shadow: var(--shadow-sm);
    display: flex;
    flex-direction: column;
    gap: var(--space-lg);
}

.content-article h2 {
    font-size: var(--font-size-h2);
    color: var(--secondary-color);
    margin-top: 1rem;
    border-bottom: 2px solid var(--border-color);
    padding-bottom: 0.5rem;
}

.lead {
    font-size: 1.15em;
    font-weight: 500;
    color: var(--secondary-color);
}

/* Fluid Image Styling */
.image-wrapper {
    margin: 1rem 0;
}

.responsive-img {
    width: 100%;
    height: auto;
    max-width: 100%;
    display: block;
    border-radius: var(--radius-md);
    object-fit: cover;
    border: 1px solid var(--border-color);
}

.image-wrapper figcaption {
    font-size: 0.85rem;
    color: var(--text-muted);
    text-align: center;
    margin-top: var(--space-sm);
    font-style: italic;
}

/* Footer Styles */
.site-footer {
    background-color: var(--secondary-color);
    color: #94a3b8;
    text-align: center;
    padding: var(--space-lg);
    font-size: 0.875rem;
    border-top: 1px solid var(--border-color);
    margin-top: 4rem;
}