# Elasticsearch Users Management module for Ansible
### *Manage Users in an esusers Realm*

---
### Requirements
* See how to manage users in an esusers Realm at https://www.elastic.co/guide/en/shield/current/managing-users.html
* See official Ansible docs

---
### Modules

  * [elasticsearch_esusers - manage elasticsearch users in an esusers realm](#elasticsearch_esusers)

---

## elasticsearch_esusers
Manage Elasticsearch users in an esusers Realm

  * Synopsis
  * Options
  * Examples

#### Synopsis
 Manages Elasticsearch users.

#### Options

| Parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
| username  |   yes  |  | |  Name of the user to add or remove  |
| update_password  |   no  |  always  | <ul> <li>always</li>  <li>on_create</li> </ul> |  C(always) update user password and roles.  C(on_create) will only set the password for newly created users  |
| force  |   no  |  False  | <ul> <li>yes</li>  <li>no</li> </ul> |  Deletes and recreates the user. If set to C(yes) the C(update_password) will be skipped  |
| roles  |   no  |    | |  Roles to be associated to the user. These are comma separated list of role  |
| state  |   no  |  present  | <ul> <li>present</li>  <li>absent</li> </ul> |  Whether the user should exist.  When C(absent), removes the user  |
| password  |   no  |    | |  Set the user's password. (Required when adding a user)  |
| esusers_bin  |   no  |  /usr/share/elasticsearch/bin/shield/esusers  | |  Location of the esusers binary  |


 
#### Examples

```
# Adds a user to your cluster
- elasticsearch_esusers: state=present username="bob" password="123456"

# Add a user to your cluster and associate him with roles
- elasticsearch_esusers: state=present username="bob" password="123456" roles="admin, marvel"

# Delete a user to your cluster
- elasticsearch_esusers: state=absent username="bob"

```

---

---
Created by Network to Code, LLC
For: @barryib 2015

