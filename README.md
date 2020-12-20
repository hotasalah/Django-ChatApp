# Django-ChatApp

Simple real-time asynchronous chat server, using Redis as the backing store, WebSockets and Django channels.

The app consists of two pages:

- An index view that lets you type the name of a chat room to join.
- A room view that lets you see messages posted in a particular chat room.

The room view will use a WebSocket to communicate with the Django server and listen for any messages that are posted.

note: the app is written without a model (no database), so you need to include the room name before sending the message to the chat.

## Django Channels:
Channels is a project that takes Django and extends its abilities beyond HTTP - to handle WebSockets, ASGI applications, chat protocols, IoT protocols, and more.

## ASGI:
ASGI (Asynchronous Server Gateway Interface) is a spiritual successor to WSGI, intended to provide a standard interface between async-capable Python web servers, frameworks, and applications.
Where WSGI provided a standard for synchronous Python apps, ASGI provides one for both asynchronous and synchronous apps, with a WSGI backwards-compatibility implementation and multiple servers and application frameworks.

## What is Redis?
Redis is an in-memory data structure store, that can be used as a caching engine. Since it keeps data in Ram, it can deliver it very quickly.

## Why do we need Redis?
When a real-time chat application does not need database (it's possible to build a chat app with a database) , it does not mean it never save the messages. It uses message broker database like Redis to save the messages in a First-in-First-Out (“FIFO”) queue before sending them.
(it's possible to build Redis servers using django-redis package, or running a previously impelemented server using a docker image).
