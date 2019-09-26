## Word Pattern II 
http://www.lintcode.com/problem/word-pattern-ii/
- 做法和 Wildcard Match / Regular Expression Match 类似

- 除了往下传递字符串，还要传递一一映射关系（映射表 mapping），因为一个字母只能匹配一个单词，不能同时对应多个字符串。
- 没法向regular expression match那样记忆化，因为一共4个参数，用memo存起来太麻烦（mapping是个哈希表，基本不会拿来做key），优化效果不是很好。记忆化的话有重复的效果好，这个题没啥重复
