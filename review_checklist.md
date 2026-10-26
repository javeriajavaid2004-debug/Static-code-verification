# Code Review Checklist

| Category | Result | Defect |
|---|---|---|
| Initialization | FAIL | The variable `sum` is not initialized. |
| Pointers | FAIL | Null pointer access, dangling reference, and use-after-free may occur. |
| Arrays/Buffers | FAIL | The program adds 6 monsters to an array with a capacity of 5. The boss name buffer can overflow. |
| Loops | FAIL | The loop in `totalMonsterHealth()` uses `<=` and accesses an extra array element. |
| Arithmetic | FAIL | Unsigned arithmetic may cause incorrect health checks. Integer division may remove decimal values. |
| Control Flow | FAIL | `playerRank()` does not return a value for scores of 100 or less. |
| Function Calls | FAIL | Some functions do not safely handle missing monsters or invalid input. |
| Classes | FAIL | The `Game` class has unsafe copying and memory management problems. |

