---
layout: post
title:      "Has_secure_password and .authenticate methods"
date:       2020-08-30 01:02:47 +0000
permalink:  has_secure_password_and_authenticate_methods
---


`has_secure_password`:

The `has_secure_password method` is what is known as an ActiveRecord macro, which is a method that creates methods for you when it is called. This macro also works with `bcrypt` so that the information (in this case the password) that is stored is secure, meaning that it is not stored in plain text in the database. The methods that this macro creates automatically validate the authentication of the password, that a password must be present on creation, and that the password does not exceed 72 bytes.

`.authenticate`:

Another `bcrypt` method, `.authenticate`, is one singular method that validates the identity and correctness of a password. This is method is often taken care of by the `has_secure_password` macro when writing code in a model as it already validates a password automatically. However, there are other uses for the `.authenticate` method. For example, in a controller class, `user.authenticate` is often used with an `if` condition where if a `user` exists, and the `password` matches the `id` of the `user` instance, then it allows the information to be stored into a session, and thus allowing a session to begin. Otherwise, the session will not be performed because there is no unique user with their own password. This allows privacy within a session and prevents others from using your session and taking your information.
