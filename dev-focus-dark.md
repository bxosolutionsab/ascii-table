## Style Guide: Dev-Focus Dark

### 1. Design Philosophy

**Dev-Focus Dark** is a design system for developer tools and technical web applications. Its core principles are:

*   **Clarity Above All:** The dark, low-contrast background reduces eye strain, allowing syntax-highlighted colors and key information to stand out.
*   **Information Density:** The layout efficiently presents data without feeling cluttered, using clean lines and a structured grid.
*   **Interactive Feedback:** The user's actions (hovering, clicking, focusing) are met with immediate and intuitive visual feedback, making the interface feel responsive and alive.
*   **Professional Polish:** The aesthetic is clean, modern, and tech-centric, avoiding superfluous decoration in favor of functional elegance.

### 2. Color Palette

The palette is built around a deep blue/charcoal base, an electric cyan accent for key interactions, and a warm yellow for highlighting. Colors are defined in the `:root` for easy theming.

| Role                      | CSS Variable              | Hex Code   | Usage                                                              |
| ------------------------- | ------------------------- | ---------- | ------------------------------------------------------------------ |
| **Deep Space Background** | `--bg-color`              | `#1a1d24`  | The main background for the entire page.                           |
| **Component Background**  | `--card-bg-color`         | `#242832`  | Background for cards, inputs, and other raised elements.           |
| **Primary Text**          | `--font-color`            | `#e0e0e0`  | Main body text, labels. Off-white for reduced glare.               |
| **Interactive Accent**    | `--accent-color`          | `#00bcd4`  | Hover effects, focus indicators, links, and primary character display. |
| **Accent Glow**           | `--accent-glow`           | `rgba(0, 188, 212, 0.5)` | Soft outer glow for focused elements.                              |
| **Highlight / Search**    | `--highlight-color`       | `#ffeb3b`  | Borders and glows for highlighted/search-matched items.              |
| **Highlight Glow**        | `--highlight-glow`        | `rgba(255, 235, 59, 0.6)`| Soft outer glow for highlighted elements.                        |
| **Subtle Border**         | `--border-color`          | `#3a3f4c`  | Default borders for cards and inputs.                              |
| **Special Text**          | `--special-char-color`    | `#8c9eff`  | Used for non-standard text like control codes (e.g., NUL, ACK).      |
| **Success Feedback**      | `--success-color`         | `#4caf50`  | Used for positive confirmation, like the "Copied!" button state.     |

### 3. Typography

Typography is clean, modern, and highly legible, using a combination of a system UI font for general text and a monospace font for code/data.

| Element          | CSS Variable      | Font Stack                                                  | Style & Purpose                                                                          |
| ---------------- | ----------------- | ----------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| **Main Font**    | `--font-main`     | `-apple-system, "Segoe UI", Roboto, Helvetica, Arial`        | For all UI text (headings, descriptions). Uses the native OS font for performance and familiarity. |
| **Monospace Font** | `--font-mono`     | `'SF Mono', 'Consolas', 'Courier New', monospace`           | For all code snippets (`<code>`), data displays, and character representations. Ensures alignment and clarity. |
| **H1 Heading**   |                   | `2.5rem`, `font-weight: 300`, `letter-spacing: 2px`         | Large, light, and spaced-out for a modern title. Features a gradient text fill for a premium look. |
| **Body Text**    |                   | `1rem` (base), `line-height: 1.6`                           | Standard text size with generous line spacing for readability.                           |
| **Code Snippets**|                   | `<code>` tag style                                          | Has a slightly darker background (`--bg-color`) to differentiate it from the card background. |

### 4. Layout & Spacing

A consistent spacing and layout system creates a sense of order and rhythm.

*   **Grid System:** The primary content area uses `display: grid` with `grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));`. This creates a fully responsive, wrapping grid of cards that adapts to any screen size without media queries.
*   **Spacing Unit:** The primary spacing unit is `rem`. This provides scalability and accessibility.
*   **Key Values:**
    *   `1rem` (16px): Standard padding inside components, spacing between text elements.
    *   `1.25rem` (20px): The `gap` between grid items (cards).
    *   `2rem - 2.5rem` (32px - 40px): Margin between large sections like the header and main content.

### 5. Core Components

#### a. Cards (`.card`)

The primary container for displaying a unit of information.

*   **Structure:** `background-color: var(--card-bg-color)`, `border: 1px solid var(--border-color)`, `border-radius: 8px`.
*   **Padding:** `1rem`.
*   **Hover State:** This is a key interaction. On hover, the card:
    1.  Lifts slightly: `transform: translateY(-5px);`
    2.  Gains a pronounced shadow: `box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);`
    3.  The border color changes: `border-color: var(--accent-color);`
    4.  All changes are animated: `transition: all 0.2s ease-out;`

#### b. Form Inputs (`.input-field`)

Designed for high visibility and clear focus states.

*   **Shape:** Fully rounded `border-radius: 50px` for a modern, "pill" shape.
*   **Colors:** `background-color: var(--card-bg-color)`, `border: 2px solid var(--border-color)`.
*   **Focus State:** Crucial for accessibility and style. On `:focus`, the input:
    1.  Changes border color: `border-color: var(--accent-color);`
    2.  Gains an outer glow: `box-shadow: 0 0 15px var(--accent-glow);`

#### c. Buttons (`.button`)

Designed to be discoverable and provide clear feedback.

*   **Default State:** Subtle, often appearing on hover to de-clutter the UI. The copy button is a prime example, with `opacity: 0` by default and `opacity: 1` on card hover.
*   **Interaction:** Simple background color change on its own hover state.
*   **Feedback State:** Use a distinct color (`--success-color`) and icon change to confirm an action, like the copy button's "copied" state.

### 6. Animation & Interaction

Motion is used purposefully to guide the user and enhance the experience.

*   **Page Load:** Content animates in with a gentle `fadeInUp` or `fadeInDown` effect to prevent a jarring appearance.
*   **Microinteractions:** Small, fast animations provide feedback. The "lift" of a card on hover or the color-and-icon switch on the copy button are perfect examples.
*   **Transitions:** All state changes (hover, focus) use a smooth `transition` (e.g., `0.2s ease-out`) to feel fluid and responsive, never abrupt.

---

### Quick Implementation Starter

To use this style guide in a new project, start with this basic HTML structure and CSS `:root`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My New Dev Tool</title>
    <style>
        :root {
            --bg-color: #1a1d24;
            --card-bg-color: #242832;
            --font-color: #e0e0e0;
            --accent-color: #00bcd4;
            --accent-glow: rgba(0, 188, 212, 0.5);
            --highlight-color: #ffeb3b;
            --border-color: #3a3f4c;
            --font-main: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            --font-mono: 'SF Mono', 'Consolas', 'Courier New', monospace;
        }

        body {
            background-color: var(--bg-color);
            color: var(--font-color);
            font-family: var(--font-main);
            margin: 0;
            padding: 2rem;
        }
        
        /* Add other styles here, reusing the variables */
    </style>
</head>
<body>
    <!-- Your content here -->
</body>
</html>
```