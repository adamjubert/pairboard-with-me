# Schema Information

### users
column name | data type | details
------------ | ------------- | -------------
id | integer | not null, primary key
email | string | not null, indexed, unique
password_digest | string | not null
session_token | string | not null, indexed, unique
first_name | string | not null, max length: 20
last_name | string | not null

### days

column name | data type | details
------------ | ------------- | -------------
id | integer | not null, primary key
date | string | not null
user_id | integer | not null
comment | text |


### pairs
column name | data type | details
------------ | ------------- | -------------
id | integer | not null, primary key
date | string | not null
user1_id | integer | not null, foreign key
user2_id | integer | foreign key

<!-- ### messages
column name | data type | details
------------ | ------------- | -------------
id | integer | not null, primary key
user_id | integer | not null, foreign_key
pair_id | integer | not null, foreign_key
body | text | not null -->
