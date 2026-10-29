2026-09-23 09:00

Course: #eas501 

## Big Ideas

*quick summary of ideas - 3-5 bullet points max*

## Key Concepts

*place links to full notes here*

## Notes

### Summary
- **Setup:** a linear system is $A\mathbf{x} = \mathbf{c}$ with $A \in \mathbb{R}^{m\times n}$. Work on the augmented matrix $(A\,|\,\mathbf{c})$.
- **Elementary row operations** (none of them change the solution set):
	- Multiply a row by a non-zero scalar.
	- Add a multiple of one row to another row.
	- Swap two rows.
- **Leading entry:** the first non-zero entry in a row.
- **Row echelon form (REF):** each leading entry sits to the right of the one above it, with zeros below. The slides also scale each leading entry to 1.
- **Reduced row echelon form (RREF):** leading entries are 1, and every other entry in a leading entry's column is 0. Getting there is **Gauss–Jordan** reduction.
- **Reading the answer off the REF:**
	- A row $(0\ 0 \cdots 0\,|\,b)$ with $b \neq 0$ means **no solution** (inconsistent).
	- Otherwise, a column with no leading entry is a **free variable**. Each free variable becomes a parameter.
	- No free variables means a **unique solution**.
$$\#\text{parameters} = n - \#\text{leading entries}$$
- **Back substitution:** solve the last equation first and work upward.

> [!tip] Intuition
> Each equation is a plane (in 3-D). Row operations swap one set of planes for another set with the *same* intersection, because every operation can be undone. Elimination just tilts the planes until the intersection is easy to read: a point (unique), a line or plane (free parameters), or nothing (parallel planes, $0 = b$).

> [!warning] Slide typos / notation
> - The second row operation reads "to add an equation multiplied". It is cut off. It means *add a scalar multiple of one equation to another*.
> - The slides' REF scales every leading entry to 1. Many textbooks only require zeros below the leading entries. Either works on the exam as long as you finish correctly.
> - In Example 2, the slide scales $0 = -13$ to $0 = 1$. That step isn't needed: $0 = -13$ already shows the system is inconsistent.

---
### Worked Examples

Ex 1: Unique solution
$$\begin{cases} x + 2y + z = 4 \\ 2x + 5y + 3z = 10 \\ -x + y + 4z = 4 \end{cases}$$
- $R_2 - 2R_1$ and $R_3 + R_1$:
$$\left(\begin{array}{ccc|c} 1 & 2 & 1 & 4 \\ 0 & 1 & 1 & 2 \\ 0 & 3 & 5 & 8 \end{array}\right)$$
- $R_3 - 3R_2$:
$$\left(\begin{array}{ccc|c} 1 & 2 & 1 & 4 \\ 0 & 1 & 1 & 2 \\ 0 & 0 & 2 & 2 \end{array}\right)$$
- Back substitution: $z = 1$, then $y = 2 - 1 = 1$, then $x = 4 - 2 - 1 = 1$.
- Check in the original equations: $1+2+1 = 4$ ✓, $2+5+3 = 10$ ✓, $-1+1+4 = 4$ ✓

Ex 2: Likely test style — classify by a parameter
$$\begin{cases} x + y + z = 1 \\ x + 2y + 3z = 2 \\ 2x + 3y + kz = m \end{cases}$$
- $R_2 - R_1$ gives $(0,1,2\,|\,1)$. $R_3 - 2R_1$ gives $(0,1,k-2\,|\,m-2)$.
- Then $R_3 - R_2$:
$$\left(\begin{array}{ccc|c} 1 & 1 & 1 & 1 \\ 0 & 1 & 2 & 1 \\ 0 & 0 & k-4 & m-3 \end{array}\right)$$
- Read the last row:
	- $k \neq 4$: unique solution.
	- $k = 4,\ m = 3$: the last row is $0 = 0$, so there are infinitely many solutions with 1 parameter.
	- $k = 4,\ m \neq 3$: the last row is $0 = m - 3 \neq 0$, so there is no solution.

Test Strategy
- Write each row operation next to the arrow ($R_3 - 3R_2$). He gives partial credit, and a labeled operation is easy to credit even if the arithmetic slips.
- If some row has a leading 1, swap it to the top first. Fewer fractions means fewer arithmetic errors.
- Plug the final answer back into the **original** equations. It takes 30 seconds.

## Questions/Gaps/Concerns



## Follow-up 

*actions items to follow-up on (e.g., watch video, re-read notes, hw)*



## References

*link to other notes, attachments, or actual lecture slides*
- [[Lec0923_2026.pdf]]
