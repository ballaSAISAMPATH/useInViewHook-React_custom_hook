# 📌 useInViewHook

[![React](https://img.shields.io/badge/React-18.2.0-blue?logo=react&logoColor=white)](https://reactjs.org/) 
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE) 
[![Live Demo](https://img.shields.io/badge/Live%20Demo-Click%20Here-blue)](https://codesandbox.io/s/useinview-f5oxe)

A **lightweight React hook** powered by the **Intersection Observer API** to detect when elements enter the viewport. Perfect for animations, lazy-loading, and visibility-triggered effects.

---

## ✨ Features
- ✅ Simple, reusable hook  
- ✅ Native Intersection Observer API  
- ✅ Supports `root`, `rootMargin`, `threshold` options  
- ✅ Auto-unobserves element after first visibility  
- ✅ Ideal for animations, lazy-loading, analytics, and video autoplay  

---

## 🚀 Installation
Copy the hook file into your project:

src/hooks/useInViewHook.js

Or fork the live demo sandbox: https://codesandbox.io/s/useinview-f5oxe


---

## ⚙️ Hook API

const [ref, isInView] = useInViewHook(options);

### Parameters

options: {
  root?: HTMLElement | null;        // Element used as viewport (default: browser)
  rootMargin?: string;              // Margin around root, CSS-like values (default: "0px")
  threshold?: number | number[];    // Visibility percentage(s) to trigger isInView (default: 0)
}

### Returns

[
  ref: React.RefObject, // Attach this to the element to observe
  isInView: boolean     // Becomes true when the element is visible
]

---

## 🎯 Example Use Cases

// Scroll-based animations
// Lazy-load images or components
// Track analytics (element visibility)
// Start video autoplay when visible
// Infinite scroll / load more content

---

## 📝 Notes

// By default, hook unobserves after first visibility.
// To continuously observe, remove:
observer.unobserve(entry.target);

// Works well with dynamic content. Ensure element exists before observing.
// Combine with CSS transitions for smooth animations.

---

## 🔗 Live Demo

https://codesandbox.io/s/useinview-f5oxe

---

## 🤝 Contributing

// Fork, improve, and submit PRs!
// Suggestions and feature requests are welcome.

---

## 📜 License

MIT License — free for personal and commercial use.
```jsx
import React from "react";
import useInViewHook from "./hooks/useInViewHook";

export default function ExampleComponent() {
  const [ref, isInView] = useInViewHook({
    threshold: 0.5,
  });

  return (
    <div
      ref={ref}
      style={{
        height: "200px",
        margin: "100vh 0",
        background: isInView
          ? "linear-gradient(to right, #00b09b, #96c93d)"
          : "lightcoral",
        color: "#fff",
        transition: "all 0.5s ease",
        display: "flex",
        justifyContent: "center",
        alignItems: "center",
        fontSize: "1.5rem",
        borderRadius: "12px",
        boxShadow: "0 10px 20px rgba(0,0,0,0.2)",
      }}
    >
      {isInView ? "✅ I'm visible!" : "❌ Not in view yet"}
    </div>
  );
}
