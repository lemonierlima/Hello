# Hi Everyone

Do you know it?

WITH ToLearn AS (
  SELECT ROW_NUMBER() OVER (ORDER BY Keyword) AS N, *
  FROM sys.dm_fts_parser('FORMSOF(INFLECTIONAL, ''study'')',1033,0,0)
)
SELECT LEFT(STUFF(@@VERSION,2,8,'y'),14) +
  UPPER(LEFT(display_term,1)) + 
  SUBSTRING(display_term,2,20) + 
  CHAR(46)
FROM ToLearn
WHERE N = 1

