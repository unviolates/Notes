
## Problem 3 — area between (x=y^2) and (x+y=1)

### Step A — rewrite equations

The two curves are
[
x = y^2\quad\text{(a parabola opening right)}\qquad\text{and}\qquad x = 1-y\quad\text{(a line).}
]
We will integrate with respect to (y) (vertical slices) because both are given as (x=) (functions of (y)). For a given (y), the horizontal width of the region is
[
\text{(right)}-\text{(left)} = (1-y) - y^2.
]

### Step B — intersection points (limits of integration)

Set the two (x)-expressions equal:
[
y^2 = 1-y \quad\Rightarrow\quad y^2 + y - 1 = 0.
]
Solve the quadratic:
[
y = \frac{-1 \pm \sqrt{1+4}}{2} = \frac{-1\pm\sqrt5}{2}.
]
Call the lower root (y_1=\dfrac{-1-\sqrt5}{2}) and the upper root (y_2=\dfrac{-1+\sqrt5}{2}).

### Step C — integral for area

[
A=\int_{y_1}^{y_2}\big[(1-y)-y^2\big],dy
=\int_{y_1}^{y_2} (1-y-y^2),dy.
]

Antiderivative (primitive):
[
\int (1-y-y^2),dy = y - \frac{y^2}{2} - \frac{y^3}{3} + C.
]
So
[
A = \Big[y - \tfrac{y^2}{2} - \tfrac{y^3}{3}\Big]_{y_1}^{y_2}.
]

### Step D — simplify the evaluation using the fact that (y_1,y_2) are roots

This is the nice trick to avoid messy cubic arithmetic: each root (y) satisfies (y^2 + y - 1 = 0), so on a root
[
y^2 = 1-y\qquad\text{and}\qquad y^3 = y\cdot y^2 = y(1-y)=y-y^2.
]
But (y^2 = 1-y) so
[
y^3 = y - (1-y) = 2y-1.
]

Now plug these into the antiderivative evaluated at a root (y):
[
F(y):= y - \frac{y^2}{2} - \frac{y^3}{3}
= y - \frac{1-y}{2} - \frac{2y-1}{3}.
]
Simplify step-by-step:
[
F(y)= y - \tfrac{1}{2} + \tfrac{y}{2} - \tfrac{2y}{3} + \tfrac{1}{3}
= \left(1+\tfrac12 -\tfrac{2}{3}\right)y + \left(-\tfrac12+\tfrac13\right).
]
Compute coefficients:
[
1+\tfrac12-\tfrac23=\tfrac{6+3-4}{6}=\tfrac{5}{6},\qquad -\tfrac12+\tfrac13=-\tfrac{1}{6}.
]
So
[
F(y)=\frac{5y-1}{6}.
]

Therefore the area (difference (F(y_2)-F(y_1))) is
[
A=\frac{5y_2-1}{6}-\frac{5y_1-1}{6}=\frac{5(y_2-y_1)}{6}.
]
But (y_2-y_1 = \dfrac{-1+\sqrt5}{2} - \dfrac{-1-\sqrt5}{2} = \sqrt5). So
[
\boxed{A=\frac{5\sqrt5}{6}.}
]

Numeric value (\approx 1.86339.)

---

## Problem 9 — area bounded by (y=x^3+1,; x=0,; y=2)

This one is straightforward.

### Step A — picture & limits

* The curve (y=x^3+1) intersects the horizontal line (y=2) when
  [
  x^3+1=2 \Rightarrow x^3=1 \Rightarrow x=1.
  ]
  The left boundary is (x=0). So (x) runs from (0) to (1).

### Step B — top minus bottom

Top curve is (y=2), bottom is (y=x^3+1). So
[
A=\int_{0}^{1} \big[2-(x^3+1)\big],dx=\int_0^1 (1-x^3),dx.
]

### Step C — integrate

[
\int_0^1 (1-x^3),dx=\Big[x-\tfrac{x^4}{4}\Big]_0^1
=1-\tfrac14=\tfrac34.
]

So
[
\boxed{A=\tfrac{3}{4}=0.75.}
]

---

## Problem 15 — arc length of ((x+3)^2 = 8(y-1)^3) from (x=-2) to (x=5)

This is a curve-length problem (not area). Arc length formula for a curve (y=f(x)) is
[
L=\int_a^b \sqrt{1+\big(f'(x)\big)^2},dx.
]

### Step A — write (y) as a function of (x)

Solve the given equation for (y):
[
(x+3)^2=8(y-1)^3 \quad\Rightarrow\quad (y-1)^3=\frac{(x+3)^2}{8}.
]
Take cube root:
[
y-1=\Big(\frac{(x+3)^2}{8}\Big)^{1/3}=\frac{1}{2}(x+3)^{2/3}.
]
So
[
y(x)=1+\frac12(x+3)^{2/3}.
]

(We take the real cube root; over the interval from (x=-2) to (x=5) (x+3) is positive so there is no sign issue.)

### Step B — compute derivative

[
\frac{dy}{dx}=\frac12\cdot\frac{2}{3}(x+3)^{-1/3}=\frac{1}{3}(x+3)^{-1/3}.
]

Then
[
\Big(\frac{dy}{dx}\Big)^2=\frac{1}{9}(x+3)^{-2/3}.
]

So the integrand becomes
[
\sqrt{1+\big(y'(x)\big)^2}
=\sqrt{1+\frac{1}{9}(x+3)^{-2/3}}.
]

This form looks messy, so we do a substitution that simplifies it.

### Step C — substitution (u=(x+3)^{1/3})

Let (u=(x+3)^{1/3}). Then
[
u^3=x+3\quad\Rightarrow\quad dx = 3u^2,du.
]
Also
[
(x+3)^{-2/3}=u^{-2}.
]

Now rewrite the integrand:
[
\sqrt{1+\frac{1}{9}u^{-2}}=\sqrt{\frac{9u^2+1}{9u^2}}=\frac{1}{3u}\sqrt{9u^2+1}.
]

Multiply by (dx=3u^2,du):
[
\sqrt{1+(y')^2},dx = \frac{1}{3u}\sqrt{9u^2+1}\cdot 3u^2,du = u\sqrt{9u^2+1},du.
]

### Step D — new limits

When (x=-2): (u=(x+3)^{1/3}=(1)^{1/3}=1).
When (x=5): (u=(8)^{1/3}=2).

So the length integral becomes
[
L=\int_{x=-2}^{5}\sqrt{1+(y')^2},dx=\int_{u=1}^{2} u\sqrt{9u^2+1},du.
]

### Step E — evaluate the integral

Let (w=9u^2+1). Then (dw=18u,du), so (u,du=\dfrac{dw}{18}). Also (\sqrt{9u^2+1}=\sqrt{w}). Thus
[
\int u\sqrt{9u^2+1},du = \int \sqrt{w}\cdot\frac{dw}{18} = \frac{1}{18}\int w^{1/2},dw
=\frac{1}{18}\cdot\frac{2}{3}w^{3/2} + C = \frac{1}{27}w^{3/2}+C.
]

Restore (w=9u^2+1). Evaluate from (u=1) to (u=2):
[
L=\frac{1}{27}\Big[(9u^2+1)^{3/2}\Big]_{1}^{2}
=\frac{1}{27}\big((9\cdot2^2+1)^{3/2} - (9\cdot1^2+1)^{3/2}\big).
]
Compute inside:
[
9\cdot2^2+1=9\cdot4+1=37,\qquad 9\cdot1^2+1=10.
]
So
[
\boxed{,L=\frac{1}{27}\big(37^{3/2}-10^{3/2}\big)
=\frac{37\sqrt{37}-10\sqrt{10}}{27}\approx 7.164424.}
]

---

## Quick recap

* Problem 3: used integration **w.r.t. (y)**, exploited root relations to simplify the integral result → (A=\dfrac{5\sqrt5}{6}).
* Problem 9: straightforward vertical-slice area from (x=0) to (x=1) → (A=\tfrac34).
* Problem 15: arc length; solved for (y(x)), computed (y'), used substitution (u=(x+3)^{1/3}) to reduce integrand to a standard form and integrated → exact length (\dfrac{1}{27}(37^{3/2}-10^{3/2})).
