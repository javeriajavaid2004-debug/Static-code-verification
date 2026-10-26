# Code Review Report

| Line Number | Defect Type | Why It Is a Problem | Proposed Fix | Severity |
|---|---|---|---|---|
| 27, 41–42 | Array Overflow | The program can add more monsters than the array can hold. | Check the array capacity before adding a monster. | High |
| 47 | Incorrect Assignment | The `=` operator changes the monster ID instead of comparing it. | Replace `=` with `==`. | High |
| 54–56 | Null Pointer | The program accesses health even when the monster is not found. | Check whether `m == nullptr` before accessing health. | Critical |
| 55–56 | Arithmetic Error | Unsigned arithmetic can make the health check incorrect. | Reject negative damage and use safe signed arithmetic. | High |
| 64–65 | Array Bounds | The loop accesses one extra array element. | Replace `i <= monsterCount` with `i < monsterCount`. | High |
| 70–73 | Dangling Reference | The function returns a reference to a local variable that is destroyed when the function ends. | Return `std::string` by value. | High |
| 77 | Uninitialized Variable | The variable `sum` contains an undefined initial value. | Initialize it with `double sum = 0;`. | High |
| 78–80 | Division by Zero | The function divides by zero if there are no monsters. | Return a safe value when `monsterCount == 0`. | High |
| 80 | Return Type | The integer return type removes the decimal part of the average. | Change the return type to `double` if decimals are required. | Medium |
| 84–86 | Use-After-Free | The code accesses the monster's name after deleting the object. | Save the name before deletion. | Critical |
| 83–86 | Null Pointer | The function accesses the name even when the monster is not found. | Check whether `m == nullptr`. | Critical |
| 91 | Integer Division | Integer division can remove the decimal part of the damage calculation. | Use `100.0` if a decimal result is required. | Medium |
| 94–99 | Missing Return | The function does not return a value for scores of 100 or less. | Add an `else` statement with a default rank. | High |
| 102, 105 | Buffer Overflow | A long boss name can exceed the allocated buffer. | Use `std::string` or safely limit the input length. | Critical |
| 102, 109 | Memory Deallocation | Memory allocated with `new[]` is released using `delete`. | Use `delete[]` or replace the buffer with `std::string`. | High |
| 119 | Array Overflow | The sixth monster is added even though the array capacity is five. | Increase the capacity or prevent extra monsters from being added. | High |
| 121 | Memory Leak | The memory allocated for `bonus` is never released. | Remove the unnecessary allocation or manage its memory safely. | Medium |
| 133 | Shallow Copy | Both `Game` objects share the same monster pointers and may delete the same objects. | Disable copying or implement a deep copy. | Critical |
| 35–37, 85 | Double Deletion | A deleted monster may remain in the array and be deleted again by the destructor. | Remove the monster from the array and update `monsterCount`. | Critical |

