# 查询没有主键的表
select table_schema,table_name from information_schema.`TABLES`
where (table_schema,table_name) not in (
	select distinct table_schema,table_name from information_schema.`COLUMNS` where column_key='PRI'
)
and table_schema not in ('sys','mysql','information_schema','performance_schema');
# 查询某张表被哪些过程和函数使用
select * from mysql.proc 
where body like '%att_emp_detail%'
