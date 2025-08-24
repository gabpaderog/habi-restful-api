
users
- id int [pk]
- email varchar [unique] not null
- phone varchar [unique] nullable
- password_hash varchar nullable
- status enum 
- created_at timestamp default now()
- updated_at timestamp default now()
- deleted_at timestamp nullable

roles
- id int [pk]
- name varchar
- desc varchar
- slug varchar

user_roles
- id int [pk]
- user_id int [fk] -> users.id(on delete cascade)
- role_id int [fk] -> roles.id
- created_at timestamp default now()

permissions
- id int [pk]
- name varchar [unique] not null
- desc varchar
- slug varchar
- created_at timestamp default now()
- updated_at timestamp default now()

role_permissions
- id int [pk]
- role_id int [fk] -> roles.id(on delete cascade)
- permission_id int [fk] -> permissions.id(on delete cascade)
- created_at timestamp default now()
- updated_at timestamp default now()

providers
- id int [pk]
- name varchar [unique] not null

user_providers
- id int [pk]
- user_id int [fk] -> users.id(on delete cascade)
- provider_id int [fk] -> providers.id(on delete cascade)
- provider_user_id varchar [unique]
- created_at timestamp

user_profiles
- id int [pk]
- user_id int [fk] -> users.id(on delete cascade)
- avatar_url varchar
- username varchar [unique] not null
- full_name varchar
- created_at timestamp default now()
- updated_at timestamp default now()
- deleted_at timestamp nullable 

user_addresses
- id int [pk]
- user_id int [fk] -> users.id(on delete cascade)
- name 
- phone
- address_line_1 varchar
- address_line_2 varchar
- barangay varchar
- municipality varchar
- province varchar
- region varchar
- country varchar
- postal_code varchar
- is_primary boolean [unique]
- created_at timestamp default now()
- updated_at timestamp default now()
- deleted_at timestamp nullable

sessions
- id int [pk]
- user_id int [fk] -> users.id(on delete cascade)
- refresh_token_hash varchar
- ip_address varchar
- user_agent varchar
- expires_at timestamp
- revoked_at timestamp nullable
- created_at timestamp default now()
- updated_at timestamp default now()

tokens 
- id int [pk]
- user_id int [fk] -> users.id(on delete cascade)
- type varchar
- token_hash varchar [unique]
- expires_at timestamp
- used_at timestamp
- created_at timestamp default now()



