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

## 6. Prove that there are no positive integers $x$, $y$, and $z$ such that $((x \bmod y) \bmod z)((y \bmod z) \bmod x)((z \bmod x) \bmod y) = gcd(x, y, z)$

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

## 8. Prove that there are no positive integers $x$ and $y$ such that $x^2 + 2x \mid y^2 + 1$

```lean4
import Mathlib

theorem no_x_sq_plus_two_x_dvd_y_sq_plus_one (x y : ℕ) (hx : 0 < x) (hy : 0 < y) :
    ¬ (x^2 + 2*x ∣ y^2 + 1) := by
  sorry
```

## 9. Prove that if $n$ is a positive integer such that $n \mid 2^n + 1$ and $n \mid 3^n + 1$, then $n = 1$

```lean4
import Mathlib

theorem eq_one_of_dvd_pow_add_one (n : ℕ) (hn : 0 < n) (h2 : n ∣ 2^n + 1) (h3 : n ∣ 3^n + 1) :
    n = 1 := by
  sorry
```

## 10. Prove that there are no natural numbers $x$ and $y$ such that $(((x^3 + y^3) \bmod 18) \bmod 17) = 15$

```lean4
import Mathlib

theorem no_nat_cube_sum_mod_eq (x y : ℕ) :
    (((x^3 + y^3) % 18) % 17) ≠ 15 := by
  sorry
```

## 11. Prove that there are no real numbers $x$ and $y$ such that $x^2 + y^2 + 4 = 2\sqrt{x^2y + xy^2 + x + y}$

```lean4
import Mathlib

theorem no_real_solutions_x2_y2_4 (x y : ℝ) :
    x^2 + y^2 + 4 ≠ 2 * Real.sqrt (x^2 * y + x * y^2 + x + y) := by
  sorry
```

## 12. Prove that there are infinitely many triples of positive integers ($x$, $y$, $z$) such that $\frac{z^2}{x + y} + z = \frac{x^2 + 1}{y} + \frac{y^2 + 1}{x}$

```lean4
import Mathlib

theorem infinite_solutions_z2_x_y_z :
    Set.Infinite { (x, y, z) : ℕ × ℕ × ℕ |
      0 < x ∧ 0 < y ∧ 0 < z ∧
      ((z : ℚ) ^ 2 / ((x : ℚ) + (y : ℚ))) + (z : ℚ) =
      (((x : ℚ) ^ 2 + 1) / (y : ℚ)) + (((y : ℚ) ^ 2 + 1) / (x : ℚ)) } := by
  sorry
```

## 13. Prove that the only positive real number solutions to $x^\left\lceil x \right\rceil = \left\lceil x \right\rceil^\left\lfloor x \right\rfloor + 1$ are $\sqrt{3}$ and $\sqrt[3]{10}$

```lean4
import Mathlib

theorem ceil_floor_eq_solutions (x : ℝ) (hx : 0 < x) :
    x ^ ⌈x⌉ = (⌈x⌉ : ℝ) ^ ⌊x⌋ + 1 ↔ x = Real.sqrt 3 ∨ x = (10 : ℝ) ^ (1 / 3 : ℝ) := by
  sorry
```

## 14. Prove that if $x$ and $y$ are positive rational numbers such that $x^2 + y^2 + 1 = 3xy$, then $\sqrt{x + y}$ is irrational

```lean4
import Mathlib

theorem sqrt_x_add_y_irrational (x y : ℚ) (hx : 0 < x) (hy : 0 < y)
    (h : x^2 + y^2 + 1 = 3 * x * y) :
      Irrational (Real.sqrt (x + y : ℝ)) := by
  sorry
```

## 15. Prove that the only real number solution to $\frac{x \pm y}{x \mp y} = (x \mp y)(2 - x \mp y)$ is $x = 1$ and $y = 0$

```lean4
import Mathlib

theorem div_pm_mp_eq_one_zero (x y : ℝ) :
    (x - y ≠ 0 ∧ x + y ≠ 0 ∧
      (x + y) / (x - y) = (x - y) * (2 - x - y) ∧
      (x - y) / (x + y) = (x + y) * (2 - x + y)) ↔
      (x = 1 ∧ y = 0) := by
  sorry
```

## 16. Let $S(n)$ be the base-10 digit sum of $n$. Prove that for every natural number $k$, one can find a real polynomial $P$, such that there are exactly $k$ natural numbers $n$ satisfying the equation $n = P(S(n))$

```lean4
import Mathlib

theorem exists_polynomial_with_k_digit_sum_solutions (k : ℕ) :
    ∃ (P : Polynomial ℝ), ∃ (S : Finset ℕ), S.card = k ∧
      ∀ (n : ℕ), n ∈ S ↔ (n : ℝ) = P.eval ((Nat.digits 10 n).sum : ℝ) := by
  sorry
```

## 17. Let $\\{x\\}$ be the fractional part of $x$. Prove that the number of real solutions $x$ to the equation $\\{x\\}(1026002 - x - \lfloor x \rfloor^2) = 1$ is exactly 2026

```lean4
import Mathlib

theorem real_solutions_count_2026 :
    Set.ncard {x : ℝ | Int.fract x * (1026002 - x - (Int.floor x : ℝ) ^ 2) = 1} = 2026 := by
  sorry
```

## 18. Prove that there is no natural number $n$ such that the combined base-10 digits of $n^2$ and $n^3$ contain each of the digits from 1 to 9 exactly twice

```lean4
import Mathlib

theorem no_nat_sq_cube_digits_one_through_nine_twice :
    ¬ ∃ (n : ℕ), List.Perm (Nat.digits 10 (n ^ 2) ++ Nat.digits 10 (n ^ 3))
      (List.range' 1 9 ++ List.range' 1 9) := by
  sorry
```

## 19. Prove that $\displaystyle\sum_{n = 1}^{\infty} \frac{n(n + 4)}{lcm(n, n + 2, n + 4)^2} = \frac{35}{6} - \frac{55\pi^2}{96}$

```lean4
import Mathlib

theorem series_lcm_converges :
    HasSum (fun (n : ℕ) =>
      let n' := n + 1
      ((n' : ℝ) * (n' + 4)) / ((Nat.lcm (Nat.lcm n' (n' + 2)) (n' + 4) : ℝ) ^ 2))
      ((35 / 6 : ℝ) - ((55 * Real.pi ^ 2) / 96)) := by
  sorry
```

## 20. Let $S(n)$ be the base-10 digit sum of $n$ and $P(n)$ be a polynomial with non-negative integer coefficients. Prove that for all positive integers $n$, $S(P(n)) \le P(S(n))$

```lean4
import Mathlib

theorem digit_sum_polynomial_le (P : Polynomial ℕ) (n : ℕ) (hn : 0 < n) :
    (Nat.digits 10 (P.eval n)).sum ≤ P.eval (Nat.digits 10 n).sum := by
  sorry
```

## 21. Let $\\{x\\}$ be the fractional part of $x$. Prove that for all positive integers $n$, $\displaystyle\int_{0}^{n} x \cdot \left\\{\frac{n}{x}\right\\} \cdot \left\lceil\frac{n}{x}\right\rceil \\, dx = \frac{n^2}{2}$

```lean4
import Mathlib

open MeasureTheory

theorem integral_fract_ceil (n : ℕ) (hn : 0 < n) :
    ∫ x in (0 : ℝ)..(n : ℝ),
      x * Int.fract ((n : ℝ) / x) * (Int.ceil ((n : ℝ) / x) : ℝ) = ((n : ℝ) ^ 2) / 2 := by
  sorry
```

## 22. Prove that if $x$ and $y$ are positive real numbers such that $x^2 + y^2 = 1$, then $\frac{x^{2x}}{3y} + \frac{y^{2y}}{3x} \gt \frac{1}{x^2 + y^2 + 4xy}$

```lean4
import Mathlib

theorem positive_real_inequality (x y : ℝ)
    (hx : 0 < x) (hy : 0 < y)
      (h_sum : x ^ 2 + y ^ 2 = 1) :
      ((x ^ (2 * x)) / (3 * y)) + ((y ^ (2 * y)) / (3 * x)) > 1 / (x ^ 2 + y ^ 2 + 4 * x * y) := by
  sorry
```

## 23. Prove that if $x$ and $y$ are distinct positive real numbers such that $x^y = y^x$, then $e^{x + y} \lt x^x \cdot y^y$

```lean4
import Mathlib

theorem distinct_pos_real_power_ineq (x y : ℝ) (hx : 0 < x) (hy : 0 < y)
    (hne : x ≠ y) (h : x ^ y = y ^ x) :
      Real.exp (x + y) < (x ^ x) * (y ^ y) := by
  sorry
```

## 24. Let $S(n)$ be the base-10 digit sum of $n$. Prove that $\displaystyle\sum_{n = 3 \atop S(n) \ge 2}^{\infty} \frac{1}{n \cdot S(n) \cdot ln(S(n))}$ diverges

```lean4
import Mathlib

theorem digit_sum_series_diverges :
    ¬ Summable (fun n : ℕ =>
      if n ≥ 3 ∧ (Nat.digits 10 n).sum ≥ 2 then
      1 / ((n : ℝ) * ((Nat.digits 10 n).sum : ℝ) * Real.log ((Nat.digits 10 n).sum : ℝ))
      else 0) := by
  sorry
```

## 25. Prove that the only positive real solutions to $\displaystyle\sqrt{2(x - 3)\smash{^2} + 4} = \sqrt{\tfrac{12}{x}}$ are $x = 1$ or $2$ or $3$

```lean4
import Mathlib

theorem positive_solutions_sqrt_eq (x : ℝ) (hx : 0 < x) :
    Real.sqrt (2 * (x - 3) ^ 2 + 4) = Real.sqrt (12 / x) ↔ x = 1 ∨ x = 2 ∨ x = 3 := by
  sorry
```

## 26. Prove that if $x$ and $y$ are distinct prime numbers, then $gcd(x^{y - 1} + y^{x - 1}, x \cdot y) = 1$

```lean4
import Mathlib

theorem gcd_prime_pow_sum_eq_one (x y : ℕ) (hx : Nat.Prime x) (hy : Nat.Prime y) (hne : x ≠ y) :
    Nat.gcd (x ^ (y - 1) + y ^ (x - 1)) (x * y) = 1 := by
  sorry
```

## 27. Prove that there is no natural number $n$ such that $29^n + 13n^4 + 5n^3 \equiv 5 \pmod{65}$

```lean4
import Mathlib

theorem no_nat_satisfies_congruence :
    ¬ ∃ n : ℕ, (29 ^ n + 13 * n ^ 4 + 5 * n ^ 3) % 65 = 5 := by
  sorry
```

## 28. Prove that the only non-negative real solution to $\displaystyle\sqrt[3]{19\sqrt{2x + 1} + 34\sqrt{x}} = \sqrt{2x + 1} + \sqrt{x}$ is $x = 4$

```lean4
import Mathlib

theorem unique_real_solution_nested_radical (x : ℝ) (hx : 0 ≤ x) :
    (19 * Real.sqrt (2 * x + 1) + 34 * Real.sqrt x) ^ (1 / 3 : ℝ) =
      Real.sqrt (2 * x + 1) + Real.sqrt x ↔ x = 4 := by
  sorry
```

## 29. Prove that $\displaystyle\sum_{n = -\infty}^{\infty} n \cdot arctan\left(\frac{4n + 2}{4n^4 + 8n^3 + 4n^2 + 1}\right) = \pi$

```lean4
import Mathlib

theorem sum_n_arctan_eq_pi :
    tsum (fun (n : ℤ) => (n : ℝ) * Real.arctan ((4 * (n : ℝ) + 2) /
      (4 * (n : ℝ) ^ 4 + 8 * (n : ℝ) ^ 3 + 4 * (n : ℝ) ^ 2 + 1))) = Real.pi := by
  sorry
```

## 30. Let $S(n)$ be the base-10 digit sum of $n$. Prove that the only positive odd integer solution to $x \cdot S(x) + y \cdot S(y) + z \cdot S(z) = xyz$ is $x = y = z = 3$

```lean4
import Mathlib

theorem odd_digit_sum_eq_xyz_iff (x y z : ℕ) (hx : 0 < x) (hy : 0 < y) (hz : 0 < z)
    (hxo : Odd x) (hyo : Odd y) (hzo : Odd z) :
      x * (Nat.digits 10 x).sum + y * (Nat.digits 10 y).sum + z * (Nat.digits 10 z).sum = x * y * z ↔
      x = 3 ∧ y = 3 ∧ z = 3 := by
  sorry
```

## 31. Prove that for all positive integers $x$, $y$, $z$, $\lvert((x \bmod y) \bmod z) - (x \bmod z)\rvert \le z - gcd(y, z)$

```lean4
import Mathlib

theorem abs_mod_mod_sub_mod_le (x y z : ℕ) (hx : 0 < x) (hy : 0 < y) (hz : 0 < z) :
    |((x % y % z : ℤ) - (x % z : ℤ))| ≤ (z : ℤ) - Nat.gcd y z := by
  sorry
```

## 32. Prove that for all real number $x$, $x^4 - 4x^3 + \frac{63}{8}x^2 - 12x + 9 \gt 0$

```lean4
import Mathlib

theorem quartic_pos_x4_4x3 (x : ℝ) : x ^ 4 - 4 * x ^ 3 + (63 / 8 : ℝ) * x ^ 2 - 12 * x + 9 > 0 := by
  sorry
```

## 33. Prove that for all real number $x$, $2x^4 + 5x^3 + 6x^2 + 11x + 10 \gt 0$

```lean4
import Mathlib

theorem quartic_pos_2x4_5x3 (x : ℝ) : 2 * x ^ 4 + 5 * x ^ 3 + 6 * x ^ 2 + 11 * x + 10 > 0 := by
  sorry
```

## 34. Prove that for all real numbers $x$ and $y$, $3x^8 + 2x^4y^4 - 7x^2y^2 + 2y^6 + \frac{5}{3} \gt 0$

```lean4
import Mathlib

theorem polynomial_pos_3x8_2x4 (x y : ℝ) :
    3 * x ^ 8 + 2 * x ^ 4 * y ^ 4 - 7 * x ^ 2 * y ^ 2 + 2 * y ^ 6 + 5 / 3 > 0 := by
  sorry
```

## 35. Let $L(n)$ be the base-10 digit length of $n$. Prove that the only positive integer solution to $n \cdot L(n) \le L(n!)$ is $n = 1$

```lean4
import Mathlib

theorem unique_pos_int_digit_length_ineq (n : ℕ) (hn : 0 < n) :
    n * (Nat.digits 10 n).length ≤ (Nat.digits 10 n.factorial).length ↔ n = 1 := by
  sorry
```

## 36. Prove that there is no non-negative real number $x$ such that $\sqrt{x^2 + x + 1 + 2\sqrt{x^3 + x^2}} = x + \frac{1}{x + 2}$

```lean4
import Mathlib

theorem no_real_solution_nested_radical (x : ℝ) (hx : 0 ≤ x) :
    Real.sqrt (x ^ 2 + x + 1 + 2 * Real.sqrt (x ^ 3 + x ^ 2)) ≠ x + 1 / (x + 2) := by
  sorry
```

## 37. Prove that the only real number solution to $min(x^3 - 2x^2 + 3, x^2 - 1) = max(3^x - 6, 7 - 2^x)$ is $x = 2$

```lean4
import Mathlib

theorem min_poly_eq_max_exp_iff_eq_two (x : ℝ) :
    min (x ^ 3 - 2 * x ^ 2 + 3) (x ^ 2 - 1) = max ((3 : ℝ) ^ x - 6) (7 - (2 : ℝ) ^ x) ↔ x = 2 := by
  sorry
```

## 38. Prove that if $a$, $b$, $c$, $d$, and $e$ are real numbers that sum to $0$ and the sum of their squares is $10$, then $min(|a - b|, |b - c|, |c - d|, |d - e|, |e - a|) \le 2$

```lean4
import Mathlib

theorem min_abs_diff_le_two (a b c d e : ℝ)
    (h_sum : a + b + c + d + e = 0) (h_sq : a ^ 2 + b ^ 2 + c ^ 2 + d ^ 2 + e ^ 2 = 10) :
      (min |a - b| (min |b - c| (min |c - d| (min |d - e| |e - a|)))) ≤ 2 := by
  sorry
```

## 39. Prove that there are infinitely many positive integer solutions $n$ to $tan(n\pi x) = 0$ if and only if $x$ is a rational number

```lean4
import Mathlib

theorem infinite_tan_zero_iff_rat (x : ℝ) :
    Set.Infinite { n : ℕ | n > 0 ∧ Real.tan ((n : ℝ) * Real.pi * x) = 0 } ↔ ∃ q : ℚ, x = q := by
  sorry
```

## 40. Prove that for all real numbers $x$, $y$, $z$, $2^x(y^2 + 1) + 2^{-x}(z^2 + 1) + 2(y \cos x + z \sin x) \gt 0$

```lean4
import Mathlib

theorem two_rpow_sq_add_cos_sin_pos (x y z : ℝ) :
    (2 : ℝ) ^ x * (y ^ 2 + 1) + (2 : ℝ) ^ (-x) * (z ^ 2 + 1) + 2 * (y * Real.cos x + z * Real.sin x) > 0 := by
  sorry
```

## 41. Prove that there are no positive integers $x$ and $y$ such that $x! + y! = (x + y + 1)^3 \cdot gcd(x!, y!)$

```lean4
import Mathlib

theorem no_pos_integers_factorial_eq :
    ¬ ∃ (x y : ℕ), 0 < x ∧ 0 < y ∧
      x.factorial + y.factorial = (x + y + 1) ^ 3 * Nat.gcd x.factorial y.factorial := by
  sorry
```

## 42. Prove that for all positive integer $n$, $\frac{Im((2 + i)^{2n})}{Re((1 + 2i)^n)}$ is an integer

```lean4
import Mathlib

theorem im_div_re_is_integer (n : ℕ) (hn : 0 < n) :
    ∃ k : ℤ, (((2 : ℂ) + Complex.I) ^ (2 * n)).im / (((1 : ℂ) + 2 * Complex.I) ^ n).re = (k : ℝ) := by
  sorry
```

## 43. Prove that $cos(100\pi x^2) = 2.01x^2 - 1$ has exactly $198$ unique real solutions

```lean4
import Mathlib

theorem cos_eq_solutions_count :
    Set.ncard { x : ℝ | Real.cos (100 * Real.pi * x ^ 2) = 2.01 * x ^ 2 - 1 } = 198 := by
  sorry
```

## 44. Prove that the only positive real numbers $x$ and $y$ satisfying both $x^{y^x} = y$ and $y^{x^y} = x$ are $x = y = 1$

```lean4
import Mathlib

theorem pos_reals_pow_eq_one (x y : ℝ) (hx : 0 < x) (hy : 0 < y) :
    x ^ (y ^ x) = y ∧ y ^ (x ^ y) = x ↔ x = 1 ∧ y = 1 := by
  sorry
```

## 45. Let $S(n)$ be the base-10 digit sum of $n$. Prove that $\displaystyle\int_{1}^{\infty} \frac{S(\lfloor x^2 \rfloor)}{x^5} \\, dx = \frac{5\pi^2}{132}$

```lean4
import Mathlib

open Real MeasureTheory

theorem integral_digit_sum_floor_sq :
    ∫ x in Set.Ici (1 : ℝ), ((Nat.digits 10 (Nat.floor (x ^ 2))).sum : ℝ) / x ^ 5 = (5 * π ^ 2) / 132 := by
  sorry
```

## 46. Let $S(n)$ be the base-10 digit sum of $n$. Prove that if $x$, $y$, $z$ are positive integers such that $xyz = 10^k$ for some integer $k \ge 1$, and at least one of $x$, $y$, $z$ is not a power of $10$, then $S(x) + S(y) + S(z) \ge 8$

```lean4
import Mathlib

theorem digit_sum_xyz_bounds (x y z : ℕ) (hx : 0 < x) (hy : 0 < y) (hz : 0 < z)
    (h_prod : ∃ k : ℕ, 1 ≤ k ∧ x * y * z = 10 ^ k)
      (h_not_pow : (¬ ∃ a : ℕ, x = 10 ^ a) ∨ (¬ ∃ b : ℕ, y = 10 ^ b) ∨ (¬ ∃ c : ℕ, z = 10 ^ c)) :
      (Nat.digits 10 x).sum + (Nat.digits 10 y).sum + (Nat.digits 10 z).sum ≥ 8 := by
  sorry
```

## 47. Prove that if $x$ and $y$ are positive integers such that $\displaystyle\sum_{n = 0}^{\infty} \frac{n}{2^n} \cdot \left\lfloor\frac{ny}{x}\right\rfloor = \frac{6y}{x}$, then $x \mid y$

```lean4
import Mathlib

theorem sum_floor_div_eq_implies_dvd (x y : ℕ) (hx : 0 < x) (hy : 0 < y)
    (h : ∑' (n : ℕ), ((n : ℝ) / (2 : ℝ) ^ n) * (Int.floor ((n : ℝ) * (y : ℝ) / (x : ℝ)) : ℝ) = 6 * (y : ℝ) / (x : ℝ)) :
      x ∣ y := by
  sorry
```

## 48. Prove that if $x$ and $y$ are positive integers such that $x^2 + 3y^2 - 17$ and $\frac{x^5 + y^5}{x + y}$ are prime, then both $x$ and $y$ must be odd

```lean4
import Mathlib

theorem odd_of_prime_quadratic_and_quintic (x y : ℕ) (hx : 0 < x) (hy : 0 < y)
    (h1 : Nat.Prime (x ^ 2 + 3 * y ^ 2 - 17))
      (h2 : Nat.Prime ((x ^ 5 + y ^ 5) / (x + y))) :
      Odd x ∧ Odd y := by
  sorry
```
