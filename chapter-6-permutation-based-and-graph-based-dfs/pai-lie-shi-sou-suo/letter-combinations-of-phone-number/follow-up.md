## Follow up
- 如果有一个词典(Dictionary)，要求组成的单词都是词典里的，如何优化?
    - 使用`trie`的数据结构
    - 搜索中经常用到trie优化
    - 替代方法：用一个哈希表存储字典里单词的所有的前缀 prefix-hash，用来直接查询有没有这个前缀组成的单词。
        - prefix-hash里存的是单词转换成的数字，这样查询时更直接，直接查询用户的输入。key是一个string，value是一个set

