aws s3 ls s3://fil.aws.training/session09/sales_csv/ --recursive

aws s3 cp filename.csv s3://fil.aws.training/session09/sales_csv/year=2018/month=12/filename.csv

aws s3 ls s3://fil.aws.training/session09/sales_csv/ --recursive | grep filename.csv

SELECT * FROM "session09"."sales_pq" limit 10;

SELECT distinct category , sum(total_price) over (partition by category) as total
FROM "session09"."sales_pq"
order by total desc
limit 5

Answer 1
========
SELECT distinct gender , cast (count(*) over (partition by gender) as double) / cast( count(*) over () as double)
FROM "session09"."sales_pq"
