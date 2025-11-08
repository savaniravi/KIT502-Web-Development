Path to the group's account in usermin :
https://ictteach-www.its.utas.edu.au/groupwork/kit502-group-07/myApp/public/index.php

-----------------------------------------------------------------
- Credentials
--------------------
System Administrator
--------------------
system@manager.com
password

--------------------
Project Administrator
--------------------
health@manager.com
password

education@manager.com
password

environment@manager.com
password

--------------------
Charity
--------------------
ravi@gmail.com
Ravi@123

pjpatel@pjpatel.com
Password@1
------------------------------------------------------------------
------------------------------------------------------------------
------------------------------------------------------------------
Database Scheme

-------------------------
roles
-------------------------
- id                      : integer (primary_key)
- name                    : string (not_null)
- created_at              : timestamp (nullable)
- updated_at              : timestamp (nullable)

-------------------------
charity_project_categories
-------------------------
- id                      : integer (primary_key)
- name                    : string (not_null)
- created_at              : timestamp (nullable)
- updated_at              : timestamp (nullable)

-------------------------
charity_project_progress
-------------------------
- id                      : integer (primary_key)
- name                    : string (not_null)
- created_at              : timestamp (nullable)
- updated_at              : timestamp (nullable)

-------------------------
users
-------------------------
- id                      : integer (primary_key)
- role_id                 : integer (foreign_key references id in roles table)
- category_id             : integer (foreign_key  references id in charity_project_categories table)
- name                    : string (not_null)
- email                   : string (unique, not_null)
- bank_name               : string (nullable)
- credit_card_number      : string (nullable)
- dob                     : date (not_null)
- email_verified_at       : timestamp (nullable)
- password                : string (not_null)
- remember_token          : string (nullable)
- created_at              : timestamp (nullable)
- updated_at              : timestamp (nullable)

-------------------------
charity_project
-------------------------
- id                      : integer (primary_key)
- user_id                 : integer (foreign_key references id in users table)
- name                    : string (not_null)
- category_id             : integer (foreign_key references id in charity_project_categories table)
- goal_amount             : integer (not_null)
- progress_id             : integer (foreign_key references id in charity_project_progress table)
- description             : text (nullable)
- created_at              : timestamp (nullable)
- updated_at              : timestamp (nullable)

-------------------------
charity_project_donations
-------------------------
- id                      : integer (primary_key)
- user_id                 : integer (foreign_key references id in users table)
- charity_id              : integer (foreign_key references id in charity_project table)
- amount                  : integer (not_null)
- bank_name               : string (not_null)
- credit_card_number      : string (not_null)
- created_at              : timestamp (nullable)
- updated_at              : timestamp (nullable)