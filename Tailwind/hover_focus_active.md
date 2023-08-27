# Topic hover focus active and other states

[CWH Notes - hover, focus, active, ...](https://www.codewithharry.com/videos/tailwind-course-in-hindi-8/)

# (1) What is the difference between :focus and :active?

:focus and :active are two different states.

- :focus represents the state when the element is currently selected to receive input and
  - `Tab` button press करने पे changes observe होगा ।

- :active represents the state when the element is currently being activated by the user.
  - Mouse से click करने पे changes observe होगा । 

For example let's say we have a `<button>`. The `<button>` will not have any state to begin with. It just exists. If we use Tab to give "focus" to the `<button>`, it now enters its :focus state. If you then click (or press space), you then make the button enter its (:active) state.

On that note, when you click on an element, you give it focus, which also cultivates the illusion that :focus and :active are the same. They are not the same. When clicked the button is in :focus:active state.

---


