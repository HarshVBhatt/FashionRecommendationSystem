# FashionRecommendationSystem
A hybrid recommendation system utilizing collaborative, product-based and user attributes-based filtering to recommend fashion products

## Content
- Scraping: Scrape a fashion products website to derive products and reviews data
- Generate Dataframes: Generate 2 datasets - products.csv containing product attributes such as length, occasion, neckline, etc.; and reviews.csv containing inidividual user-product reviews
- Collaborative Filtering: Generate sparse matrix of user-product with ratings as the value, utilize decomposition and reconstruction techniques to derive approximate ratings and recommend the top expected-ratings products
- Content-based Filtering: For a given product, find subset 'S' of top similar products and recommend the top expected-ratings products from 'S'
- User Attribute-based Filtering; For a given user, find subset 'U' of top similar user, get subset 'Q' of products rated by 'U' users and recommend the top expected-ratings products from 'Q'
- Recommendation Driver: For a given user id, generate 3 types of recommendations - Similar users also like (Collaborative), Similar fit products (User Attribute-based), Similar to products you like (Content-based)

## Full System Architecture
![Full System Architecture](https://github.com/HarshVBhatt/FashionRecommendationSystem/assets/69580380/b1220bfe-2c29-4a7b-80ab-d356b52aa3b7)

## System Management
- Updating Collaborative Recommendations - After 'n' new user-product updates, incremental SVD can be used to update and reconstruct the user-product expected ratings matrix
- Solving New Product Cold Start - For a new product 'y', find cosine similarity with all existing products and return subset 'S' of top similar products. Whenever a product from S is recommended, also recommend 'y'
- Solving New User Cold Start - For a new user 'x', find cosine similartiy with all existing users based on attributes and return subset 'U'. For all users in 'U', return subset 'Q' containing all the products purchased. Recommend top rated products from 'Q' 
