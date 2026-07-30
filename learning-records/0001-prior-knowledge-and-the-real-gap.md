# Prior knowledge established, and where the real gap sits

Learner disclosed: ~20 years Unix, Perl and regex; one ~5k-line Java GUI
application (long ago); .NET CRUD services with JWT and auth; static-typing
instincts from Java and C#. Self-identified weakness: HTML, CSS, and the visual
layer generally. No modern-JS-ecosystem exposure.

This matters because it relocates the gap. The backend, data, and text-
processing half of the stated mission is already covered at depth, so hours
spent there are wasted. The entire deficit is the browser rendering layer —
which sits *below* Vue, not inside it. Teaching Vue first would leave the
learner unable to distinguish a Vue problem from a CSS problem, making every
layout bug unattributable.

**Implications:** skip OO/classes/interfaces in the TypeScript phase — already
known from Java and C#. Teach structural typing explicitly; it is the genuine
departure from nominal typing. Motivate Vue reactivity via the Java GUI
listener model. Expect Perl/Unix analogies to land and React analogies not to.
JWT work in Phase 5 leans on existing .NET knowledge rather than on new sources.
