# Set cors headers
Header always set Access-Control-Allow-Methods  "*"
Header always set Access-Control-Allow-Headers "Content-Type, x-requested-with, Authorization, Accept"
Header always set Access-Control-Allow-Credentials "true"
# Add cors headers (May result duplicate headers)
Header add Access-Control-Allow-Methods  "*"
Header add Access-Control-Allow-Headers "Content-Type, x-requested-with, Authorization, Accept"
Header add Access-Control-Allow-Credentials "true"
# Proxy pass http and websocket
ProxyPass "/"  "http://localhost:3000/"
#ProxyPassReverse "/"  "http://localhost:3000/"
RewriteCond %{HTTP:Upgrade} websocket [NC]
RewriteCond %{HTTP:Connection} upgrade [NC]
RewriteRule ^/?(.*) "ws://localhost:3000/$1" [P,L]