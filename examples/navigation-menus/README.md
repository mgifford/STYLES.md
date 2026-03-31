---
title: Accessible, responsive navigation menus
---

# Accessible, responsive navigation menus

This guide summarizes best practices for building site navigation that works for every user — mouse, keyboard, touch, and assistive technology — across screen sizes.

Derived from W3C WAI tutorials, Nielsen Norman Group research, and practitioner guidance listed in [References](#references).

---

## Why navigation accessibility matters

Navigation is the most-used interactive component on most websites. A barrier here blocks access to every other page. Common failures — keyboard traps, missing focus indicators, unlabeled hamburger buttons — disproportionately affect screen reader users, keyboard-only users, and users with motor disabilities.

Good navigation is also good UX: clear, consistent menus reduce cognitive load for every user.

---

## 1. HTML structure

### Use semantic elements

Build navigation from native HTML before reaching for ARIA. Native elements carry built-in keyboard behavior and accessibility semantics at no extra cost.

```html
<nav aria-label="Main">
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/about">About</a></li>
    <li><a href="/services">Services</a></li>
    <li><a href="/contact">Contact</a></li>
  </ul>
</nav>
```

**Rules:**

- Wrap the navigation in `<nav>`.
- Use `<ul>` and `<li>` to mark up the list of links. This tells screen readers the number of items.
- Use `<a>` elements for links to pages. Reserve `<button>` elements for actions that do not navigate (for example, opening a sub-menu).
- If a page has more than one `<nav>`, give each a unique `aria-label`: `aria-label="Main"`, `aria-label="Footer"`, `aria-label="Breadcrumb"`.

### Mark the current page

```html
<li><a href="/about" aria-current="page">About</a></li>
```

Use `aria-current="page"` on the link for the active page. Do not rely on color or font weight alone to show the current location.

### Use breadcrumbs for deep hierarchies

```html
<nav aria-label="Breadcrumb">
  <ol>
    <li><a href="/">Home</a></li>
    <li><a href="/services">Services</a></li>
    <li><span aria-current="page">Web design</span></li>
  </ol>
</nav>
```

Breadcrumbs help users orient themselves in a deep site structure. Use an `<ol>` (ordered list) because the path has a defined sequence. Wrap the current page name in `<span aria-current="page">` rather than an `<a>` element.

---

## 2. Skip navigation link

Every page must open with a visible skip link so keyboard users can bypass the navigation and jump to the main content.

```html
<a href="#main-content" class="skip-link">Skip to main content</a>

<!-- later in the page -->
<main id="main-content">
```

```css
.skip-link {
  position: absolute;
  top: -100%;
  left: 0;
  padding: 0.5rem 1rem;
  background: #000;
  color: #fff;
  z-index: 1000;
}

.skip-link:focus {
  top: 0;
}
```

**Rules:**

- The skip link must be the first focusable element on the page.
- Show it visually on focus. Do not hide it with `display: none` or `visibility: hidden` — those techniques also hide it from screen readers.
- The target anchor (`id="main-content"`) must exist and be reachable by focus. Add `tabindex="-1"` on `<main>` only if the browser does not natively focus it on programmatic navigation.

---

## 3. Keyboard navigation

All navigation must be fully operable by keyboard alone.

| Key | Expected behavior |
| :--- | :--- |
| `Tab` | Move forward through focusable elements |
| `Shift+Tab` | Move backward through focusable elements |
| `Enter` | Follow a link; activate a button |
| `Space` | Activate a button (for example, open a sub-menu) |
| `Escape` | Close an open sub-menu; return focus to the triggering button |
| `Arrow keys` | Optional: move between items in an open flyout (application-menu pattern only) |

**Rules:**

- Do not remove the browser's default focus outline. Replace it with a custom visible style if needed.
- Ensure tab order matches the visual reading order.
- When a sub-menu closes, return focus to the button or link that opened it.
- Do not require arrow key navigation for disclosure-style menus — reserve that pattern for application menus (for example, a text editor menu bar).

### Focus style minimum

```css
:focus-visible {
  outline: 3px solid #005fcc;
  outline-offset: 2px;
}
```

The focus indicator must have at least a 3:1 contrast ratio against the background. Prefer `outline` over `box-shadow` because `outline` is visible in forced-colors (Windows High Contrast) mode.

---

## 4. Responsive navigation: the hamburger menu

On small screens, a visible navigation list often collapses to a toggle button. This pattern is accessible when built correctly.

### Minimal accessible hamburger

```html
<button
  type="button"
  aria-controls="main-nav"
  aria-expanded="false"
  class="nav-toggle"
>
  <span aria-hidden="true">&#9776;</span>
  <span class="sr-only">Toggle navigation</span>
</button>

<nav id="main-nav" hidden>
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/about">About</a></li>
  </ul>
</nav>
```

```js
const toggle = document.querySelector('.nav-toggle');
const nav = document.getElementById('main-nav');

toggle.addEventListener('click', () => {
  const isExpanded = toggle.getAttribute('aria-expanded') === 'true';
  toggle.setAttribute('aria-expanded', String(!isExpanded));
  nav.hidden = isExpanded;
});

// Close on Escape
document.addEventListener('keydown', (e) => {
  if (e.key === 'Escape' && toggle.getAttribute('aria-expanded') === 'true') {
    toggle.setAttribute('aria-expanded', 'false');
    nav.hidden = true;
    toggle.focus();
  }
});
```

**Rules:**

- Use `<button type="button">`, not a `<div>` or `<span>`, for the toggle.
- Set `aria-expanded="false"` when the menu is closed; `aria-expanded="true"` when open.
- Use `aria-controls` pointing to the `id` of the controlled element.
- Give the button a visible, meaningful label. An icon alone is not enough.
- Use the HTML `hidden` attribute (or `display: none`) to hide the collapsed menu. This removes it from the accessibility tree when hidden, which is the correct behavior.
- On `Escape`, close the menu and return focus to the toggle button.

### Screen reader-only utility class

```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```

---

## 5. Flyout and disclosure sub-menus

Flyout menus add complexity. Use them only when a flat menu is not practical. Prefer the disclosure pattern (a visible button that toggles a sub-menu) over the hover-only flyout.

### Disclosure pattern

```html
<ul>
  <li>
    <button
      type="button"
      aria-expanded="false"
      aria-controls="services-submenu"
    >
      Services
    </button>
    <ul id="services-submenu" hidden>
      <li><a href="/services/web">Web design</a></li>
      <li><a href="/services/mobile">Mobile</a></li>
    </ul>
  </li>
</ul>
```

**Rules:**

- The toggle is a `<button>` adjacent to, or wrapping, the parent item label.
- `aria-expanded` reflects the open/closed state of the sub-menu.
- `aria-controls` names the controlled sub-menu element.
- Do not open sub-menus on hover alone. Hover must be supplemented by a click or focus+enter interaction.
- Close open sub-menus when focus leaves the navigation region entirely.
- Do not use ARIA `role="menu"` and `role="menuitem"` for website navigation. Those roles carry strict keyboard expectations (arrow key navigation, no tab stops) that do not fit a link list. Use them only for application-style menu bars.

---

## 6. Design and visual standards

### Touch targets

- Minimum touch target: 44×44 px for all interactive elements (WCAG 2.5.8).
- Add padding to links and buttons rather than relying on small text hitboxes.

```css
nav a,
nav button {
  min-height: 44px;
  padding: 0.5rem 1rem;
  display: inline-flex;
  align-items: center;
}
```

### Color and contrast

- Navigation text and icons: minimum 4.5:1 contrast against the background.
- Active/current page indicator: do not use color alone. Pair color with underline, bold weight, or an icon.
- Focus indicators: minimum 3:1 contrast against adjacent colors (WCAG 2.4.11).

### Visual hierarchy

- Keep the primary navigation to seven or fewer items. More than seven items increases cognitive load without improving findability.
- Group related items with visual proximity before adding labels.
- Use consistent placement: users expect primary navigation at the top of the page or in a persistent sidebar.
- Differentiate navigation from body content with a visible boundary (border, background, or clear whitespace).

### Animation and motion

```css
@media (prefers-reduced-motion: reduce) {
  nav,
  .nav-toggle,
  [id$="-submenu"] {
    transition: none;
    animation: none;
  }
}
```

Respect `prefers-reduced-motion` for any slide, fade, or expand animation on navigation elements.

---

## 7. Common pitfalls

| Pitfall | Effect | Fix |
| :--- | :--- | :--- |
| Using `<div>` or `<span>` as the toggle button | Keyboard users cannot activate it; screen readers do not announce it as interactive | Replace with `<button type="button">` |
| Omitting `aria-expanded` | Screen readers cannot tell users whether the menu is open | Add `aria-expanded="true/false"` on the toggle |
| Hover-only flyouts | Keyboard and touch users cannot open sub-menus | Supplement hover with click and keyboard activation |
| Removing focus outlines with `outline: none` | Keyboard users lose their place | Replace with a visible custom focus style |
| Using `visibility: hidden` for the skip link at rest | Screen readers cannot reach the skip link | Use the off-screen CSS pattern with `position: absolute; top: -100%` |
| Icon-only hamburger button with no label | Screen readers announce "button" without any name | Add visible text or `aria-label` with a meaningful label |
| Using ARIA `role="menu"` for site navigation | Implies strict keyboard contracts users do not expect | Use `<nav>`, `<ul>`, and disclosure buttons instead |
| Not returning focus after closing a menu | Keyboard users lose their position | Return focus to the triggering button on close |
| `display: none` for responsive nav without a toggle | Content is inaccessible on small screens | Pair hiding with an accessible toggle button |
| Opening the nav in a new browsing context | Disorienting for all users | Link within the same context; reserve `target="_blank"` for documents |

---

## 8. Testing checklist

Before shipping a navigation component, verify all of the following.

**Keyboard**

- [ ] All links and buttons are reachable by `Tab` in visual order.
- [ ] `Enter` and `Space` activate buttons.
- [ ] `Escape` closes open sub-menus and returns focus to the trigger.
- [ ] No keyboard trap exists.
- [ ] Focus is visible at every step.

**Screen reader** (test with NVDA + Firefox and VoiceOver + Safari at minimum)

- [ ] `<nav>` landmarks are announced with their label.
- [ ] The number of items in each `<ul>` is announced.
- [ ] `aria-current="page"` is announced on the active link.
- [ ] Toggle button state ("expanded/collapsed") is announced.
- [ ] Sub-menu items are reachable after opening.

**Mouse and touch**

- [ ] Touch targets are at least 44×44 px.
- [ ] Hover flyouts also open on click.
- [ ] Open menus close when clicking or tapping outside.

**Responsive**

- [ ] Navigation remains usable from 320 px to 1280 px wide.
- [ ] Hamburger toggle is visible and labeled on small screens.
- [ ] No horizontal scroll is introduced by the navigation.

**Color and motion**

- [ ] Navigation text meets 4.5:1 contrast.
- [ ] Focus indicators meet 3:1 contrast.
- [ ] Current-page indicator does not rely on color alone.
- [ ] Animations respect `prefers-reduced-motion`.

---

## References

- [W3C WAI — Menus tutorial](https://www.w3.org/WAI/tutorials/menus/)
- [W3C WAI — Menu structure](https://www.w3.org/WAI/tutorials/menus/structure/)
- [web.dev — Website navigation](https://web.dev/articles/website-navigation)
- [Level Access — Accessible navigation menus: pitfalls and best practices](https://www.levelaccess.com/blog/accessible-navigation-menus-pitfalls-and-best-practices/)
- [Accessible Web — Navigation](https://accessibleweb.dev/navigation)
- [Accessibility Design Guide — Menus](https://www.accessibilitydesignguide.ca/menus.php)
- [Smashing Magazine — Building accessible menu systems](https://www.smashingmagazine.com/2017/11/building-accessible-menu-systems/)
- [Smashing Magazine — Responsive navigation on complex websites](https://www.smashingmagazine.com/2013/09/responsive-navigation-on-complex-websites/)
- [Nielsen Norman Group — Menu design](https://www.nngroup.com/articles/menu-design/)
- [UX Design — Accessibility of the navigation menu](https://uxdesign.cc/accessibility-of-the-navigation-menu-8a915e4d3e51)
- [UserWay — Website navigation accessibility](https://userway.org/blog/website-navigation/)
- [Svarm — Accessible navigation](https://svaerm.com/en/blog/accessible-navigation/)
- [IONOS — Responsive navigation in web design](https://www.ionos.ca/digitalguide/websites/web-design/responsive-navigation-in-web-design/)
- [Pressbooks (Toronto Metropolitan University) — Tutorial 4: Navigation menus and responsive design](https://pressbooks.library.torontomu.ca/webdesignlab/chapter/tutorial-4-navigation-menus-and-responsive-design/)
- [dev.to / Ilizette — How to build an accessible navigation menu](https://dev.to/ilizette/how-to-build-an-accessible-navigation-menu-1omk)
- [Framer — Website navigation](https://www.framer.com/blog/website-navigation/)
- [Design Bootcamp — Website navigation menu examples, design and code](https://medium.com/design-bootcamp/website-navigation-menu-examples-design-code-404cf48cc135)
- [WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- [ACCESSIBILITY.md](../../ACCESSIBILITY.md)
- [STYLES.md](../../STYLES.md)
