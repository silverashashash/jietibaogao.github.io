## Two  Sum 类

|  | Time Complexity | Space Complexity |
| :--- | :--- | :--- |
| Hash | O\(n\) | O\(n\) |
| Two Pointers | O\(nlogn\) 要先排序 | O\(1\) |

Two sum  这题要求的是返回满足条件的两个值，这是不需要额外空间的。

如果要求的是返回下标，则必须要额外空间存储，以为Two pointers预先要排序。

具体方法是用一个tail记录每个数原本的index（排序二元组 \(x,y））

二元组排序的基本做法是，x不用的排x，x相同的排y（python里的tuple能完成）

