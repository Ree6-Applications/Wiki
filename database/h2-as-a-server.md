---
description: This is a Guide if you are interested in using H2 as a embedded Server.
---

# H2 as a Server

## Why?

Well if you want to use the Bot and the Backend at the same time, using only H2 or SQLite wont work!\
Since they lock the file on every read and write operation. So if you use H2 you can enable the option called `createEmbeddedServer` which allows you to create a small H2 Database Server which handles all incomming requests for anything Database related!

### Setup

To start you will need to set the value `hikari.misc.createEmbeddedServer` to true and set the storage to h2. Once you do so only other thing you need to do is set the exact same port on the Backend and set the host to the IP of the Bot. After setting all these values the last thing to do is set the storage typ to h2-server on the Backend and it should connect to the H2 Server running on the Bot!
