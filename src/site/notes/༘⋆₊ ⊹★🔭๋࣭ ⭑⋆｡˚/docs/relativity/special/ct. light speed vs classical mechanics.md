---
{"dg-publish":true,"permalink":"/༘⋆₊ ⊹★🔭๋࣭ ⭑⋆｡˚/docs/relativity/special/ct. light speed vs classical mechanics/","tags":["physics","relativity","math"]}
---


>[!info] summary
>an example on why [[༘⋆₊ ⊹★🔭๋࣭ ⭑⋆｡˚/docs/relativity/special/einstein's idea for special relativity\|einstein's idea for special relativity]] was surprising


# setting the scene
imagine 2 coordinate systems. let's consider a *single* spatial coordinate for ease

>[!note] we will usually plot $x$ on the horizontal axis and $t$, on the vertical

- a [[༘⋆₊ ⊹★🔭๋࣭ ⭑⋆｡˚/docs/classical-mechanics/reference frame\|R.F.]] unmoving, stationary - using unprimed coordinates $(x, t)$
- another [[༘⋆₊ ⊹★🔭๋࣭ ⭑⋆｡˚/docs/classical-mechanics/reference frame\|R.F.]], moving at uniform velocity wrt the first one, away from them - using primed coordinates $(x', t')$

>[!tip] you might as well imagine you're on the stationary frame

![Imagen de WhatsApp 2024-11-12 a las 19.53.42_4b5e7948.jpg|400](/img/user/%F0%9F%97%84files/Imagen%20de%20WhatsApp%202024-11-12%20a%20las%2019.53.42_4b5e7948.jpg)

## trajectory of light
assuming that the speed of light is constant as a law of physics ([[༘⋆₊ ⊹★🔭๋࣭ ⭑⋆｡˚/docs/relativity/special/principle of light constancy\|principle of light constancy]]), say, speed $c$, then we can say that if the person at the origin turns on a light beam, the trajectory of light is
$$
x = ct
$$

## trajectory of person moving away
let's assume
- at time $t = 0$, both people are together, i.e. at the origin
	given that the coordinates for the moving person are primed, we say that at time $0$, $x = x' = 0$
- $v > 0$, i.e. the person is moving *away* from the origin

thus, the trajectory of the person moving away in the stationary [[༘⋆₊ ⊹★🔭๋࣭ ⭑⋆｡˚/docs/classical-mechanics/reference frame\|R.F.]] is
$$
x = vt
$$

which, in their own [[༘⋆₊ ⊹★🔭๋࣭ ⭑⋆｡˚/docs/classical-mechanics/reference frame\|R.F.]] is 
$$
x' = 0
$$
(from their POV, they're not moving, it's you who is moving away)

---

# coordinate transform 

>[!question] what is the relationship between the 2 coordinates?

## via classical mechanics

1. given that $x = x' = 0$, we can say that the spatial transform is
$$
x' = x - vt
$$
2. given the [[༘⋆₊ ⊹★🔭๋࣭ ⭑⋆｡˚/docs/relativity/special/pre-relativistic physics assumptions\|pre-relativistic physics assumptions]], the 2 people can synchronize their clocks and we can assume that their readings are not affected by the movements of the 2 people, i.e. they always show the same time, thus
$$
t' = t
$$

### how does this match up with the [[༘⋆₊ ⊹★🔭๋࣭ ⭑⋆｡˚/docs/relativity/special/principle of light constancy\|principle of light constancy]]?

let's get the trajectory of light in the primed coordinates:

- trajectory of light: $x = ct$
and we plug it in the spatial coordinate transform $x' = x-vt$:
$$
x' = x - vt = ct - vt = (c - v)t
$$
thus, light moves with velocity $c - v \neq c$ (bc $v > 0$) => :

>[!error] contradiction with the [[༘⋆₊ ⊹★🔭๋࣭ ⭑⋆｡˚/docs/relativity/special/principle of light constancy\|principle of light constancy]]

