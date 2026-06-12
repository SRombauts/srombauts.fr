---
title:  "SimplexNoise: a small C++ Simplex noise library"
date:   2014-08-13 21:00:00 +0200
tags:
  - c++
  - github
---

I read [a series of articles on LinuxFr][linuxfr] about Perlin noise for map generation,
that triggered me to implement my own procedural-generation experiments: terrain heightmaps,
textures, that sort of thing. I wanted something I could drop straight into a C++ project,
so I ported Simplex noise from a [Java reference implementation][demystified]
and put it on GitHub as [SimplexNoise][SimplexNoise].

Simplex noise is the gradient noise Ken Perlin introduced in 2001 as a successor to his
classic noise from the 1980s. The win is mostly about dimensions. Classic gradient noise
samples a hypercube, so in n dimensions it has to interpolate across its 2ⁿ corners.
Simplex noise samples the simplest shape that fills the space instead, which has only n+1
corners: a triangle in 2D, a tetrahedron in 3D. The cost then grows roughly like n² rather
than 2ⁿ, with fewer visible directional artifacts as a bonus. The LinuxFr article that set
me off puts it plainly:

> Le bruit à base de simplexe est une évolution du bruit à base de gradient et proposé par
> le même Ken Perlin. Le problème du bruit à base de gradient est qu'il requiert O(2ⁿ)
> interpolation pour un bruit à n dimensions. Ceci vient du fait qu'on utilise un hypercube
> qui a 2ⁿ sommets. Pour avoir moins de points, on va utiliser un objet à n dimensions qui
> possède le moins de points possible : c'est ce qu'on appelle un simplexe. En dimension 2,
> c'est un triangle. En dimension 3, c'est un tétraèdre.

I did not reinvent any of that. For the maths I leaned entirely on [Stefan Gustavson's
"Simplex noise demystified" (2005)][demystified] and his 2012 speed-improved Java reference,
with a few optimizations credited to Peter Eastman.
I only focused on the C++ port and sharing it.

The API is simple: a single `SimplexNoise` class with `noise()` overloads for
1D, 2D and 3D, plus a fractal helper that sums several octaves of noise (fractional
Brownian motion) with configurable frequency, amplitude, lacunarity and persistence. That
fractal summation is what turns a single smooth noise field into something that reads as
natural detail. It is the family of noise behind a lot of game terrain: the same article
points out that Minecraft builds its worlds « à base de bruit de Perlin ».

Here is 2D fractal noise with 7 octaves, rendered with a small companion example that
draws the field with the [CImg][cimg] library:

![2D Simplex fractal noise, 7 octaves](/assets/images/SimplexNoise-2D-7octaves.jpg)

The repository follow my usual template: MIT licensed, small library with just a header and
a source file, a CMake build, `cpplint` and `cppcheck` wired in for style and sanity, a
Doxygen config for the docs, and continuous integration on both Travis CI (Linux) and
AppVeyor (Windows).

Code, examples and the Java reference are on GitHub: [github.com/SRombauts/SimplexNoise][SimplexNoise].
Feedback and pull requests welcome.

## Further reading

- The article that got me started: [Je crée mon jeu vidéo E10: génération procédurale de carte][linuxfr] on LinuxFr, and [its part 2][linuxfr2].
- Stefan Gustavson, [Simplex noise demystified][demystified] (2005), the PDF and Java code I ported from.
- Jérémy Cochoy, [Introduction au bruit de Perlin][cochoy], a French walk-through of Perlin and simplex noise.

note: [^1]

[^1]: Written retrospectively in 2026 while documenting a few older projects that never got their own post (the repository went up in August 2014).

[SimplexNoise]: https://github.com/SRombauts/SimplexNoise
[cimg]: https://cimg.eu/
[linuxfr]: https://linuxfr.org/news/je-cree-mon-jeu-video-e10-generation-procedurale-de-carte-partie-1
[linuxfr2]: https://linuxfr.org/news/je-cree-mon-jeu-video-e11-generation-procedurale-de-carte-partie-2
[demystified]: https://www.researchgate.net/publication/216813608_Simplex_noise_demystified
[cochoy]: https://cochoy-jeremy.developpez.com/tutoriels/2d/introduction-bruit-perlin/
