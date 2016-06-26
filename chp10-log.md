# A Primer About Software Engineering
# Chapter 10: Logging

Generally speaking there are two kinds of events you want to log: business and technical. Business events are relevant for the business. If you are using event sourcing you already log these events and are done. Technical events are relevant only for developers when trying to figure out bugs and the business events cannot provide a clear picture.

## Technical Logging
Generally speaking technical logging is stupid. You write your code robust and handle technical problems with code and not log messages. In practice you need these technical log messages. Exceptions that you somehow forget to catch properly. Or external systems that have unpredictable behavior.

If you communicate with an external system, remember to log all messages that are exchanged. Just remember to log in such a way, that you can correlate these messages, even if they are asynchronous. You can run into a performance problem here which you need to figure out. In the end what's the point in logging less when you cannot fix your system when it breaks?

Log exceptions properly: `log.error("Error reading configuration file", e);`
