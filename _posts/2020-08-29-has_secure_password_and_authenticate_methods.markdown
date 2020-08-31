---
layout: post
title:      "Has_secure_password and .authenticate methods"
date:       2020-08-29 21:02:48 -0400
permalink:  has_secure_password_and_authenticate_methods
---


`has_secure_password`:

The `has_secure_password method` is what is known as an ActiveRecord macro, which is a method that creates methods for you when it is called. This macro also works with `bcrypt` so that the information (in this case the password) that is stored is secure, meaning that it is not stored in plain text in the database. The methods that this macro creates automatically validate the authentication of the password, that a password must be present on creation, and that the password does not exceed 72 bytes.

`.authenticate`:

`.authenticate`, is one singular method that only compares a password to its associated user. This password is compared by using the information that is stored in the database as `password_digest`, which salts and hashes the password so that it cannot be decoded by anyone else.  For example, in a controller class, `user.authenticate` is often used with an `if` condition where if a `user` exists, and the `password` matches the `id` of the `user` instance, then it allows the information to be stored into a session, and thus allowing a session to begin. Otherwise, the session will not be performed because there is no unique user with their own password stored in `password_digest` (or the user's password does not associate with the user). This allows privacy within a session and prevents others from using your session and taking your information.
