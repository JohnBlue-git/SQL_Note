
## select top distinct from where
```sql
SELECT TOP(100) ... FROM [...].[...].[table]
WHERE commodity
IN(SELECT commodity FROM […] WHERE update_date>'2023-11-10 10:00:00' AND update_date<'2023-11-10 14:30:00')
AND wart_no IN(SELECT wart_no FROM […] WHERE update_date>'2023-11-10 10:00:00' AND update_date<'2023-11-10 14:30:00')

SELECT 'DataSource'as'data_source', id, age FROM Customers;

SELECT DISTINCT ...(要選的所有欄位)
國外也常用GROUP(選定欄位)
```

## insert update delete truncate
```sql
INSERT @another
SELECT … FROM @this

UPDATE @another
SET 日期=@yesterday WHERE 日期=@today


DELETE FROM
WHERE 日期=@today

TRNCATE TABLE […]
```

## define & cast & getdate
```sql
-- date datetime smalldatetime

SELECT … FROM @this
WHERE CAST(… AS date)=‘2023-11-06’

DECLARE @year int = DATEPART(year, GETDATE())
DECLARE @month int = DATEPART(month, GETDATE())
DECLARE @day int = DATEPART(day, GETDATE())
DECLARE @today SMALLDATETIME = CAST(CAST(@year*10000 + @month*100 + @day AS varchar(255)) AS SMALLDATETIME)
DECLARE @hour_start int = 10 SELECT DATEADD(hour, @hour_start, @today)

SELECT DATEADD(hour, @hour_start, CAST(CAST(GETDATE() AS DATE) AS SMALLDATETIME))
SELECT … FROM … WHERE update_date>'2023-11-13 10:00:00' AND update_date<'2023-11-13 14:30:00'
```

## create
```console
IF OBJECT_ID(‘…A…’, ‘U’) IS NULL
BEGIN
	USE […B…]
	SET ANSI_NULLS ON
	SET QUOTED_IDENTIFIER ON
	CREATE TABLE […C…].[…A…] (
		[xxx] 	[varchar](30)	NOT NULL
		[xxx] 	[int]		NULL
	CONSTRAINT [PK_…A…] PRIMARY KEY CLUSTERED (
		[時間] ASC,
		[代號] ASC
	) WITH (PAD_INDEX = OFF, STATISTICS….
	) ON [PRIMARY]
END
```

## monitor DB
https://blog.darkthread.net/blog/detect-column-update-in-trigger/#google_vignette

## online sql
https://www.programiz.com/sql/online-compiler/
