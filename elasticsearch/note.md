
# 1. Match Query（匹配查询） #
## Links ##
1. [Elasticsearch: 权威指南 » 深入搜索 » 全文搜索 » 匹配查询](http://106.186.120.253/preview/match-query.html)
2. [Elasticsearch: The Definitive Guide [2.x] » Search in Depth » Full-Text Search » The match Query](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/match-query.html)
3. [Elasticsearch Reference [5.4] » Query DSL » Full text queries » Match Query](https://www.elastic.co/guide/en/elasticsearch/reference/5.4/query-dsl-match-query.html)
## Notes ##
1.它是一个高级 全文查询 ，这表示它既能处理**全文字段**，又能处理**精确字段**。  
2.一个单词项时，match查询执行的是单个底层 **term 查询**。

# 2. 多字符串查询 #
## Links ##
1. [多字符串查询](http://106.186.120.253/preview/multi-query-strings.html)
## Notes ##
1.最简单的多字段查询可以将搜索项映射到具体的字段。将不同查询字符串映射到不同字段。

# 3. 单字符串查询 #
## Links ##
1. [单字符串查询](http://106.186.120.253/preview/_single_query_string.html)
## Notes ##
1.将所有的搜索项堆积到单个字段中。  
2.单个字符串查询的情形：  
- [最佳字段](https://github.com/niaomingjian/ProjectNote/blob/master/elasticsearch/note.md#4-最佳字段) ： 相同字段中包含的词越多越好。比如，“brown fox”词组比单词更有意义。
- [多数字段](https://github.com/niaomingjian/ProjectNote/blob/master/elasticsearch/note.md#5-多数字段) ： 将一个字段索引到不同的字段，它们各自具有独立的分析链，以此来提高相关度评分。
- [混合字段](https://github.com/niaomingjian/ProjectNote/blob/master/elasticsearch/note.md#6-混合字段) ： 在多个字段中确定其信息，如名和姓。这就像是在包含了所有要检索的字段的大字段中进行搜索一样，有点类似于_field字段。

# 4. 最佳字段 #
## Links ##
1. [最佳字段](http://106.186.120.253/preview/_best_fields.html)
2. [最佳字段查询调优](http://106.186.120.253/preview/_tuning_best_fields_queries.html)
3. [multi_match 查询](http://106.186.120.253/preview/multi-match-query.html)
## Notes ##
1. 使用dis_max 查询来实现最佳字段
2. 在dis_max 查询中使用tie_breaker 参数来调优
3. **best_fields**类型的multi_match多匹配查询实际上就是用dis_max 查询来实现最佳字段匹配

# 5. 多数字段 #
## Links ##
1. [多数字段](http://106.186.120.253/preview/most-fields.html)
## Notes ##
1. 使用**most_fields**类型的multi_match多匹配查询来实现多数字段匹配

# 6. 混合字段 #
## Links ##
1. [跨字段实体搜索 - most_fields方式的问题](http://106.186.120.253/preview/_cross_fields_entity_search.html#_most_fields_方式的问题)
2. [自定义 _all 字段](http://106.186.120.253/preview/custom-all.html)
3. [cross-fields 跨字段查询](http://106.186.120.253/preview/_cross_fields_queries.html)
## Notes ##
1. 使用词中心式查询来实现混合字段匹配。
2. 混合字段匹配在索引时的解决方案：自定义 _all字段。
3. 混合字段匹配在检索时的解决方案：cross_fields 类型的multi_match查询。

# 7. multi_match Query #


