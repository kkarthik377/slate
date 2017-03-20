---
title: IChatBot API Documentation

language_tabs:
  - shell: cURL

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='#'>Documentation Powered by iChatBot</a>

includes:
  - admin
  - chatbot
  - errors

search: true
---

# Introduction

IChatBot offers various services to manage it's users, manage multiple chat bots, generate reports about the coversations between the bot and the users and offers a tool that will help to create custom chat widgets which can easily be integrated with any websites.

# Authentication

IChatBot uses JWT authentication mechanism to provide a secure way to access it's APIs.

when the user successfully logs in to iChatBot using their credentials, a JSON Web Token will be returned and must be saved locally (typically in local storage, but cookies can be also used), instead of the traditional approach of creating a session in the server and returning a cookie.

Whenever the user wants to access iChatBot's private APIs, the user agent should send the JWT, typically in the Authorization header using the Bearer schema. The content of the header should look like the following:

<aside class="notice">
Authorization: Bearer <code>&lt;JWT Token&gt;</code>
</aside>

This is a stateless authentication mechanism as the user state is never saved in server memory. The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources. 
As JWTs are self-contained, all the necessary information is there, reducing the need to query the database multiple times.

This allows you to fully rely on data APIs that are stateless and even make requests to downstream services.It doesn't matter which domains are serving your APIs, so Cross-Origin Resource Sharing (CORS) won't be an issue as it doesn't use cookies.

> Make sure to mention `JWT Token` with your API key.

