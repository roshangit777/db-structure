# DB Structure (Users, Roles, Menus, Mappings)

## This document contains the database structure for:

1. Users table
2. Roles table
3. Menus table
4. Role–Menu mapping
5. User–Role mapping

## 1. users Table

| Column        | Type                    |
| ------------- | ----------------------- |
| user_id       | SERIAL PRIMARY KEY      |
| name          | VARCHAR(100)            |
| email         | VARCHAR(150) UNIQUE     |
| password_hash | VARCHAR(255)            |
| is_active     | BOOLEAN DEFAULT true    |
| created_at    | TIMESTAMP DEFAULT NOW() |
| updated_at    | TIMESTAMP DEFAULT NOW() |

## 2. roles Table

| Column      | Type                |
| ----------- | ------------------- |
| role_id     | SERIAL PRIMARY KEY  |
| role_name   | VARCHAR(100) UNIQUE |
| description | VARCHAR(255)        |

## 3. menus Table

| Column    | Type                     |
| --------- | ------------------------ |
| menu_id   | SERIAL PRIMARY KEY       |
| menu_name | VARCHAR(100)             |
| menu_path | VARCHAR(255)             |
| parent_id | INT (FK → menus.menu_id) |
| order_no  | INT DEFAULT 0            |
| desc      | VARCHAR(255)             |

## 4. role_menu_mapping Table

| Column  | Type                   |
| ------- | ---------------------- |
| id      | SERIAL PRIMARY KEY     |
| role_id | INT FK → roles.role_id |
| menu_id | INT FK → menus.menu_id |

## 5. user_role_mapping Table

| Column  | Type                   |
| ------- | ---------------------- |
| id      | SERIAL PRIMARY KEY     |
| user_id | INT FK → users.user_id |
| role_id | INT FK → roles.role_id |

## Image

![ER](Diagram.png)
