---
comments: true
difficulty: 中等
edit_url: https://github.com/doocs/leetcode/edit/main/solution/2600-2699/2686.Immediate%20Food%20Delivery%20III/README.md
tags:
    - 数据库
---

# [2686. 即时食物配送 III 🔒](https://leetcode.cn/problems/immediate-food-delivery-iii)

[English Version](/solution/2600-2699/2686.Immediate%20Food%20Delivery%20III/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p><code>Delivery</code>&nbsp;表：</p>

<pre>
+-----------------------------+---------+
| 字段名                       | 类型   |
+-----------------------------+---------+
| delivery_id                 | int     |
| customer_id                 | int     |
| order_date                  | date    |
| customer_pref_delivery_date | date    |
+-----------------------------+---------+
delivery_id 是该表的具有唯一值的列。
每一行包含有关向顾客交付食物的信息，顾客在某个日期下订单，并指定了一个首选交付日期（在订单日期当天或之后）。
</pre>

<p>&nbsp;</p>

<p>如果顾客的首选交付日期与订单日期相同，则该订单称为 <strong>立即交付</strong>&nbsp;，否则称为 <strong>计划交付</strong>&nbsp;。</p>

<p>编写解决方案，找出每个唯一的 <code>order_date</code> 中立即交付订单的百分比。<strong>结果保留两位小数</strong>。</p>

<p>返回查询结果并按 <code>order_date</code> <strong>升序</strong> 排序。</p>

<p>查询结果的格式如下所示。</p>

<p>&nbsp;</p>

<p><b>示例 1：</b></p>

<pre>
<b>输入：</b>
Delivery 表:
+-------------+-------------+------------+-----------------------------+
| delivery_id | customer_id | order_date | customer_pref_delivery_date |
+-------------+-------------+------------+-----------------------------+
| 1           | 1           | 2019-08-01 | 2019-08-02                  |
| 2           | 2           | 2019-08-01 | 2019-08-01                  |
| 3           | 1           | 2019-08-01 | 2019-08-01                  |
| 4           | 3           | 2019-08-02 | 2019-08-13                  |
| 5           | 3           | 2019-08-02 | 2019-08-02                  |
| 6           | 2           | 2019-08-02 | 2019-08-02                  |
| 7           | 4           | 2019-08-03 | 2019-08-03                  |
| 8           | 1           | 2019-08-03 | 2019-08-03                  |
| 9           | 5           | 2019-08-04 | 2019-08-08                  |
| 10          | 2           | 2019-08-04 | 2019-08-18                  |
+-------------+-------------+------------+-----------------------------+
<b>输出：</b>
+------------+----------------------+
| order_date | immediate_percentage |
+------------+----------------------+
| 2019-08-01 | 66.67                |
| 2019-08-02 | 66.67                |
| 2019-08-03 | 100.00               |
| 2019-08-04 | 0.00                 |
+------------+----------------------+
<b>解释：</b>
– 2019年8月1日共有3个订单，其中2个是即时订单，1个是预定订单。因此，该日期的即时订单百分比为66.67。
– 2019年8月2日共有3个订单，其中2个是即时订单，1个是预定订单。因此，该日期的即时订单百分比为66.67。
– 2019年8月3日共有2个订单，均为即时订单。因此，该日期的即时订单百分比为100.00。
– 2019年8月4日共有2个订单，均为预定订单。因此，该日期的即时订单百分比为0.00。
order_dste 按升序排序。</pre>

## 解法

### 方法一

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
SELECT  order_date
       ,ROUND(100*SUM(IF(customer_pref_delivery_date = order_date,1,0))/COUNT(*),2) AS immediate_percentage
FROM Delivery
GROUP BY  order_date
ORDER BY order_date
```

<!-- tabs:end -->

<!-- end -->
