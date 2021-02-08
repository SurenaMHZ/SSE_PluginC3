# SSE_PluginC3
Server-Sent Events|A server-sent event is when a web page automatically gets updates from a server for construct3

This was also possible before, but the web page would have to ask if any updates were available. With server-sent events, the updates come automatically.

Examples: Facebook/Twitter updates, stock price updates, news feeds, sport results, etc.
/////////////////////////////////////////////
construct3

conditions:
onerror:When an error occurs
onopen:When a connection to the server is opened
onmessage:When a message is received

actions:
connect:Server-Sent Events(SSE) connect to url
Support:check browser support for server-sent events(SSE)

expressions:
data:data callback url
error:error
//////////////////////////////////////////////////
server

For the example above to work, you need a server capable of sending data updates.

The server-side event stream syntax is simple. Set the "Content-Type" header to "text/event-stream". Now you can start sending event streams.
Example:
<?php
header('Content-Type: text/event-stream');
header('Cache-Control: no-cache');

$time = date('r');
echo "data: The server time is: {$time}\n\n";
?>

Controlling the Reconnection-timeout
The browser attempts to reconnect to the source roughly 3 seconds after each connection is closed. You can change that timeout by including a line beginning with "retry:", followed by the number of milliseconds to wait before trying to reconnect.

The following example attempts a reconnect after 10 seconds:
<?php
retry: 10000\n
?>
Example:
<?php
header('Access-Control-Allow-Origin: *'); 
header('Content-Type: text/event-stream');

echo "retry: 10000\n";
$time = date('r');
echo "data: The server time is: {$time}\n\n";
?>

