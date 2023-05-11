# SQL-Sample
SQL code to demonstrate proficiency on table queries and analysis
 SELECT * FROM survey
 LIMIT 10;

 SELECT COUNT (DISTINCT user_id) AS '
   user_answers', 
   question FROM   
   survey
 GROUP BY question;
 
SELECT quiz.user_id, home_try_on.user_id IS NOT  
  NULL 
  AS 'is_home-try_on', home_try_on.
  number_of_pairs, purchase.user_id IS NOT NULL 
  AS 'is_purchase'
FROM quiz
  LEFT JOIN home_try_on
  ON quiz.user_id = home_try_on.user_id
  LEFT JOIN purchase
  ON home_try_on.user_id = purchase.user_id
LIMIT 10;


SELECT 1.0 * 
(
  SELECT COUNT(*)
  FROM subscriptions
  WHERE subscription_start < '2017-01-01'
  AND (
    subscription_end
    BETWEEN '2017-01-01'
    AND '2017-01-31'
  )
) / (
  SELECT COUNT(*) 
  FROM subscriptions 
  WHERE subscription_start < '2017-01-01'
  AND (
    (subscription_end >= '2017-01-01')
    OR (subscription_end IS NULL)
  )
) 
AS result;
