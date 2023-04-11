# NorthwindBI

## ikinci başlık

### üçüncü


<details>
  <summary>ETL nedir? </summary>
  
Veriler farklı sebeplerle sürekli olarak yer değiştirebilir. Bu aktarım süreçlerinede ETL (Extract Transform Load) deniliyor. Biz bu örnekte Source'dan ODS'ye, ODS'den DW'ye aktarım yapıyoruz. 
</details>

bu kod şu işi yapar


```sql

DECLARE @LatestDate DATETIME

SELECT @LatestDate = (SELECT MAX(ModifiedDate) FROM NorthwindODS.dbo.[Products] WITH (NOLOCK))

IF @LatestDate IS NOT NULL
	SELECT *
	FROM [Northwind].[dbo].[Products] WITH (NOLOCK)
	WHERE ModifiedDate > @LatestDate
ELSE
	SELECT *
	FROM [Northwind].[dbo].[Products] WITH (NOLOCK)

```


