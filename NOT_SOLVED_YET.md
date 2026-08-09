# Not solved yet

Possibly unsound problems that have not been solved.

## Problems

```lean4
import Mathlib

noncomputable def P (n : ℕ) : ℕ := sInf { p : ℕ | Nat.Prime p ∧ n < p }

theorem next_prime_quadratic_eq_iff_two (n : ℕ) (hn : 0 < n) :
    (P n : ℝ) = ((n : ℝ) ^ 2 - (n : ℝ) + 1) / ((P n : ℝ) - (n : ℝ)) ↔ n = 2 := by
  sorry
```

```lean4
import Mathlib

theorem digit_sum_prod_finitely_many_solutions :
    Set.Finite { n : ℕ | 0 < n ∧ ((Nat.digits 10 n).sum) ^ 2 + 8 = (Nat.digits 10 n).prod } := by
  sorry
```

```lean4
import Mathlib

theorem binom_equation_unique_solution (a b c d : ℕ)
    (ha : 0 < a) (hb : 0 < b) (hc : 0 < c) (hd : 0 < d) :
      (2 * a + 1) ^ (b + 2) - 1 = 2 ^ c * Nat.choose d (2 * a + 2) ↔
      a = 1 ∧ b = 2 ∧ c = 4 ∧ d = 5 := by
  sorry
```

```lean4
import Mathlib

def P (x : ℝ) : ℝ := x^2 + x + 1

theorem floor_p_pow_r_odd_even_iff (r : ℝ) :
    ({n : ℕ | 0 < n ∧ Even ⌊(P (n : ℝ)) ^ r⌋}.Infinite ∧
      {n : ℕ | 0 < n ∧ Odd ⌊(P (n : ℝ)) ^ r⌋}.Infinite) ↔
      (0 < r ∧ ¬ ∃ k : ℤ, r = (k : ℝ)) := by
  sorry
```

```lean4
import Mathlib

theorem digit_product_sq_eq_div (n : ℕ) (hn : 0 < n) :
    ((Nat.digits 10 n).prod) ^ 2 = Nat.floor ((n : ℝ) / 11) ↔ n = 10 ∨ n = 11 := by
  sorry
```

```lean4
import Mathlib

theorem no_prime_solution_xy_2 (x y z : ℕ)
    (hx : Nat.Prime x) (hy : Nat.Prime y) (hz : Nat.Prime z) :
      x ^ y + 2 ≠ 2 ^ z + y ^ x := by
  sorry
```
