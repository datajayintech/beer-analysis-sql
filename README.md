# beer-analysis-sql
       
       ---- create table in postgresql -----

      create table beer_reviews(
      brewery_id float8
      , brewery_name varchar
      , review_time float8
      , review_overall float8
      , review_aroma float8
      , review_appearance float8
      , review_profilename varchar
      , beer_style varchar
      , review_palate float8
      , review_taste float8
      , beer_name varchar
      , beer_abv float8
      , beer_beerid float8

    );
    --- Which brewery produces the strongest beers by ABV%? ---
    
    SELECT brewery_name, beer_abv, beer_beerid
    FROM beer_reviews
    WHERE beer_abv IS NOT NULL
    ORDER BY beer_abv DESC
    LIMIT 1
    
      SELECT corr("review_overall", "review_taste") AS review_taste_corr,
         corr("review_overall","review_appearance") AS review_appearance_corr,
         corr("review_overall","review_palate") AS review_palate_corr,
         corr("review_overall","review_aroma") AS review_aroma_corr
      FROM beer_reviews
    LIMIT 3
  
      SELECT beer_style, review_aroma,review_appearance,
           MAX(review_appearance) AS appearance_max,
           MAX(review_aroma) AS aroma_max, 
           AVG(review_appearance) AS appearance_avg,
           AVG(review_aroma) AS aroma_avg, COUNT(*)
      FROM beer_reviews
      GROUP BY 1,2,3
      ORDER BY COUNT(*) DESC
     LIMIT 2
