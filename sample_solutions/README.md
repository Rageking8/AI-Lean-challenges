# Sample solutions

Bunch of sample solutions from various models.

## Prompt structure

### First prompt

#### Normal

```txt
Complete the following lean 4 proof:
import Mathlib

...
```

#### Golf

```txt
Complete the following lean 4 proof and golf it to the smallest size possible:
import Mathlib

...
```

#### Restrictions

```txt
Complete the following lean 4 proof without using native_decide:
import Mathlib

...
```

### Follow-up prompt

#### Errors

```txt
Line <Number> error(s):
...

Line <Number> error(s):
...
```

#### Refusal

The model refuses to attempt the task or provides a low-effort response, typically citing difficulties with completion or flagging practical constraints, such as not having access to a Lean environment. In such cases, follow-up prompts would include a mix of affirmations that the task is doable and an explicit request for a proper, full-effort attempt or continuation.
