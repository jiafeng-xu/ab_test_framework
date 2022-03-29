# ab_test_framework
## Guidance:
#### How to use the tool to generate XP metrics results:


1.   Activate the function - **'test_result'**
2.   Prepare the SQL query 
3.   Make sure the query returns the correct structure as requested
4.   Run the function on the SQL output 

##### 1.Functions explained:
* '**welschs_ttest_2**' function: ratio-based test 
* '**ttest**' function: Mean-based T-test 
* '**test_result**' function: return results 

##### 2.Example SQL queries can be found within the ipynb file 
##### 3.SQL output 需要确保**表结构**和**字段名称**与以下要求一致以正常运行
* Ratio-based test --> metric, exp, variation, convert, total
* Mean-based T-test --> metric, exp, variation, avg, stddev, sample size

##### 4.Example / 案例教学
1. Want to know if "user-level MARGIN %" of XP is significantly changed
2. Write a SQL query that has an output as  
"""
######## select 
 ########  'gross margin' as metric
 ########  , id|| ' - ' ||name as exp
 ########  , variation
 ########  , avg(gm_base) as avg
 ########  , stddev(gm_base) as stddev
 ########  , count(user_id) as n
 ########  from (....)
"""
3. Run the function on the SQL query
