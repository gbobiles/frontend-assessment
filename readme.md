-------- Front End Assessment ------------

Please see folders exercise1 and exercise2 for each of the required assessment exercises.

---

Repository forked from mindarc/frontend-assessment.

---

Build Tool: Vite
CSS Framework: Tailwind
JS Framework: Vue 3
Animation Library: GSAP (for exercise 2)

---

Bonus Question:

Q: Explain why the result of `('b' + 'a' + + 'a' + 'a').toLowerCase()` is `banana`.

A: Regular + operator concatenate strings like b and a, but ++ will require a number to be concatenated, since 'a' isn't a number, it will result into a NaN value. This then will result into a concatenated string of baNaNa which then tranformed into lowercase.
