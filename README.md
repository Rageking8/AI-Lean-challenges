# AI Lean challenges

List of Lean challenges that can be used to test various AI models.

## 1. Prove that $\left\lceil\left(\frac{5+\sqrt{17}}{2}\right)^x\right\rceil$ is odd for all natural $x$

```lean4
import Mathlib

theorem ceil_pow_expr_odd (x : ℕ) :
    Odd ⌈(((5 : ℝ) + Real.sqrt 17) / 2) ^ x⌉ := by
  sorry
```

## 2. Given $x + y + z = \pi$, prove that $\sin{x}\sin{y}\sin{z} \le \frac{3\sqrt{3}}{8}$

```lean4
import Mathlib

theorem sin_mul_upper_bound
    (x y z : ℝ)
    (h : x + y + z = Real.pi) :
    Real.sin x * Real.sin y * Real.sin z ≤
      (3 * Real.sqrt 3) / 8 := by
  sorry
```
