[back-home](https://github.com/LucasKuhn/notes)
## SQL
### One-to-many relationship
![one-to-many schema](https://github.com/sf-sea-lions-2017/database-drill-one-to-many-schema-challenge/blob/master/readme-assets/schema-example.png)  
*One amazon user can have many orders*  
### One-to-one relationship
![many-to-many schema](https://github.com/sf-sea-lions-2017/database-drill-one-to-one-schema-challenge/blob/master/readme-assets/facebook-account-schema.png)  
*One FB user can only have on FB account, and vice-versa*  
### Many to many relationship  
![many-to-many schema](https://github.com/sf-sea-lions-2017/database-drill-many-to-many-schema-challenge/blob/master/readme-assets/many-to-many-schema.png)  
*An author can write many books, and a book can have many authors.*  

### Mixed situation 
<img src="https://github.com/sf-sea-lions-2017/database-drill-many-to-many-schema-challenge/blob/solo-lucaskuhn/many-to-many.png" width="70%">.  
*A user can have many reviews and favoritings*    
*A favoriting has a user who made it and a review*  
*A review has an author, a product, and can have many favoritings*  
*A review is about one product, one product can have many reviews*  

Writing to DB files examples : [Phase 0 Puppy Maker](https://github.com/LucasKuhn/phase-0-tracks/blob/master/databases/puppy_maker/puppy_maker.rb)
