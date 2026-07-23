# AI Lean challenges

List of Lean challenges that can be used to test various AI models.

## 1. Prove that $\left\lceil\left(\frac{5+\sqrt{17}}{2}\right)^x\right\rceil$ is odd for all natural $x$

```lean4
import Mathlib

theorem ceil_pow_expr_odd (x : ℕ) :
    Odd ⌈(((5 : ℝ) + Real.sqrt 17) / 2) ^ x⌉ := by
  sorry
```

## 2. Prove that if $x + y + z = \pi$, then $\sin{x}\sin{y}\sin{z} \le \frac{3\sqrt{3}}{8}$

```lean4
import Mathlib

theorem sin_mul_upper_bound
    (x y z : ℝ)
    (h : x + y + z = Real.pi) :
    Real.sin x * Real.sin y * Real.sin z ≤
      (3 * Real.sqrt 3) / 8 := by
  sorry
```

## 3. Prove that no finite sum of distinct irreducible fractions of the form $\frac{2}{n}$ equals $\frac{5}{121}$

```lean4
import Mathlib

theorem no_distinct_irreducible_two_over_n_sum :
    ¬ ∃ (S : Finset ℕ), (∀ n ∈ S, n > 0 ∧ Nat.Coprime 2 n) ∧
      (∑ n ∈ S, (2 : ℚ) / (n : ℚ)) = 5 / 121 := by
  sorry
```

## 4. Prove that $\left\lvert\ln{x}\right\rvert + \left\lvert\ln{y}\right\rvert \geq 2\ln{\left(\frac{x + y}{2\sqrt{xy}}\right)}$

```lean4
import Mathlib

theorem log_abs_sum_lower_bound (x y : ℝ) (hx : 0 < x) (hy : 0 < y) :
    |Real.log x| + |Real.log y| ≥
      2 * Real.log ((x + y) / (2 * Real.sqrt (x * y))) := by
  sorry
```

## 5. Prove that if $1 < x < y$ and $x^y = y^x$, then $x^{y^y} > y^{x^x}$

```lean4
import Mathlib

theorem power_tower_inequality {x y : ℝ} (h1 : 1 < x) (h2 : x < y) (h3 : x ^ y = y ^ x) :
    x ^ (y ^ y) > y ^ (x ^ x) := by
  sorry
```

## 6. Prove that no natural x, y, z > 0 satisfies $((x \bmod y) \bmod z)((y \bmod z) \bmod x)((z \bmod x) \bmod y) = gcd(x, y, z)$

```lean4
import Mathlib

theorem no_mod_mod_mod_eq_gcd (x y z : ℕ) (hx : 0 < x) (hy : 0 < y) (hz : 0 < z) :
    ((x % y) % z) * ((y % z) % x) * ((z % x) % y) ≠ Nat.gcd x (Nat.gcd y z) := by
  sorry
```

## 7. Let $S(n)$ be the base-10 digit sum of $n$. Prove that for all positive integers $n$ and $x$, $S(n^x) \leq S(n)^x$

```lean4
import Mathlib

theorem digit_sum_pow_le (n x : ℕ) (hn : 0 < n) (hx : 0 < x) :
    (Nat.digits 10 (n ^ x)).sum ≤ ((Nat.digits 10 n).sum) ^ x := by
  sorry
```
