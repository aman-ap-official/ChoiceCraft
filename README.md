# 🎮 ChoiceCraft: An Interactive Story Engine

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

ChoiceCraft is a lightweight, beginner-friendly interactive fiction engine. It allows creators to build complex branching narratives using a simple JSON structure without touching deep logic.

## 🚀 [Live Demo](https://your-username.github.io/choicecraft/)

## ✨ Features

*   **Data-Driven:** Entire stories are powered by a single `story.json` file.
*   **Visuals:** Supports dynamic background images for every scene.
*   **Responsive:** Fully playable on mobile and desktop.
*   **Minimalist:** Zero dependencies, just vanilla HTML, CSS, and JS.

## 🤔 Why Contribute?

*   **For Writers:** You don't need to touch the JS. Just add your creativity to `story.json`.
*   **For Devs:** This is a sandbox for UI/UX experimentation. Try adding sound, inventory systems, or local-save features.
*   **For Beginners:** The code is strictly documented and uses modern ES6+ standards, making it a great learning resource.

## 🛠️ Tech Stack

*   **Frontend:** HTML5, CSS3 (Modern Flexbox UI)
*   **Logic:** Vanilla JavaScript (ES6+ Fetch API)
*   **Storage:** JSON-based state management

## 🤝 Contributing

We love contributions! You can help by:
1.  **Adding Stories:** Edit `story.json` to add new branches.
2.  **UI/UX:** Improve the CSS theme or add animations.
3.  **Features:** Add inventory systems or sound effects.

### How to add a new scene:
Add a new entry to the `story.json` file:
```json
"your_scene_id": {
  "text": "The description of the scene.",
  "image": "URL_TO_IMAGE",
  "choices": [
    { "text": "Choice A", "next": "another_scene_id" }
  ]
}
```

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.
