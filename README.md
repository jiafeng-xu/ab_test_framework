# ab_test_framework
## Guidance:
#### How to use the tool to generate XP metrics results:


1.   Activate the function - **'test_result'**
2.   Prepare the SQL query 
3.   Make sure the query returns the correct structure as requested
4.   Run the function on the SQL output 

##### 1.Functions explained:
* '**ratio_ttest_2**' function: ratio-based test 
* '**ttest**' function: Mean-based T-test 

##### 2.Example SQL queries can be found within the ipynb file 
##### 3.SQL output 需要确保**表结构**和**字段名称**与以下要求一致以正常运行
* 'ratio_ttest_2' function: ratio-based test
  * SQL output must return 4 columns:
    * col, variation, convert, total
  * col: (optional) dimensions such as language, device_type, etc. Assign NULL / '' if dimension analysis is not needed. When multiple dimensions are needed, please concat them into col (e.p. language || '-' ||device_type as col).
  * variation: please return 1 & 2 as the result
  * convert: numerator
  * total: denominator
* 'ttest' function: Mean-based T-test
  * SQL output must return 4 columns:
    * col, variation, id, metrics
  * col: (optional) dimensions such as language, device_type, etc. Assign NULL / '' if dimension analysis is not needed. When multiple dimensions are needed, please concat them into col (e.p. language || '-' ||device_type as col).
  * variation: please return 1 & 2 as the result
  * id: granularity of the XP (device_id/user_id)
  * metrics: returned values for metrics

##### 4.Example / 案例教学
1. Want to know if "user-level booking & margin across languages" of XP is significantly changed
2. Write a SQL query that has an output as  
 **select**
 language as col
 , variation
 , user_id
 , sum(total) as avg
 , sum(gm_margin) as margin
 from (....)

3. Run the function on the SQL query
