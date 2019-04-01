# Oracle-optimization
Some  record for optimization 
----2019/4/1------
case 1:
where 子句中存在case when 会导致执行计划优先选择nested loop。导致在执行复杂SQL的时候，虽然结果集数据量不大，就几十万，也会执行超过3个小时。
action:
将case when拆分，换成UNIONI ALL方式，执行时间从3小时缩小为8分钟。由于SQL中存在大量子查询使用分析函数，待将分析函数先落地临时表后性能还会进一步提高。
