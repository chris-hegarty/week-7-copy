# Database Design

We'll be building a fictional database for a twitter clone so you can see how that might work.

# Needs

Username
Email
Password
Tweet body
Tweet date
Tweet user
Followers
Folllowing
Who Liked It
What Was Liked
Retweeted Tweet
Body of Retweet
Date of Tweet Retweeted
Who retweeted it
Date of Retweet

Every table should have an ID.

###User Table

id (Auto incrementing integer)
username (Varchar20)
email (Varchar64)
password (Varchar64)
followers
following

###Tweets Table

id(Autoincrementing integer)
user_id int (References id column in users table.) This is a "foreign" key.
weet Body Varchar(280)
Tweet Date Datetime

###Likes Table
id (Autoincrementing Integer)
tweet_id(Integer)(references id column in the tweet table.)
user_id (references id column in users table)

###Retweet
id (Autoincrementing Integer)
tweet_id(Integer)(references id column in the tweet table.)
user_id (references id column in users table)
retweet_date (datetime)

###Followers
id (Autoincrementing integer.)
following_id - references id column in users table
follower_id - references id column in users table.

Tweet User
Who Liked It
Date of Tweet Retweeted
Who retweeted it
