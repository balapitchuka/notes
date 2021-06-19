
Redis is key sensitive

redis-cli -p 6370

0 - not found, does not exist, not success
1 - found, exists, success

# insert key
set name 200
get name

# list all keys
keys *

# delete a key
del name
keys *

# clear screen
clear

# increment integer like counter
set seq_id 1
get seq_id

incr seq_id
incr seq_id

# alternate to find the number of keys
dbsize

# set multiple values in single commands
mset soft 100 tv 200 bed 300

# get multiple values in single commands
mget soft tv bed

# check for existence of key
exists soft
exists hello

# TTL(Time To Live)
# set to 60 secondss
set color red EX 60

# expire manually using command
expire Bed 60
get Bed
persist Bed