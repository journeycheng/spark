# sql

## DISTINCT
- 只返回不同的值
- 不能部分使用DISTINCT。DISTINCT关键字应用于所有列
```sql
SELECT DISTINCT vend_id
FROM products;
```

## LIMIT
- 查询结果返回前几行
```sql
SELECT prod_name
FROM products
LIMIT 5;
```

## ORDER BY
- 取一个或多个列的名字，据此对输出进行排序，默认升序；
- 多个列的情况，按照出现的顺序优先级逐渐降低；
```sql
SELECT prod_name
FROM products
ORDER BY prod_name;
```

```sql
SELECT prod_id, prod_price, prod_name
FROM products
ORDER BY prod_price, prod_name;
```
- 指定排序方向 DESC
```sql
SELECT prod_id, prod_price, prod_name
FROM products
ORDER BY prod_price DESC, prod_name
```

- ORDER BY和LIMIT的组合，找到一个列中最高或最低的值
```sql
SELECT prod_price
FROM products
ORDER BY prod_price DESC
limit 1;
```

## where

- 根据WHERE字句中指定的搜索条件进行过滤
- 条件操作符
  - != 使用在数字比较的时候
  - 字符串用单引号
  - between num1 and num2
  - 空值检查：prod_price IS NULL

| 操作符        | 说明   |
| --------   | -----:  |
| ＝     | 等于 |
| <> 或 !=      |   不等于   |
| <        |    小于    |
| <=        |    小于等于  |
| >        |    大于  |
| >=        |    大于等于    |
| between        |    在指定的两个值之间  |

- 逻辑操作符
  - AND
  - OR
  - IN，合法值由逗号分隔，全都括在圆括号中
  - NOT IN
  
```sql
WHERE ven_id IN (1002, 1003)
```


