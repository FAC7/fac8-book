## Redis Cheatsheet

To run redis server in terminal:
``REDIS-SERVER``

To run redis commands in terminal:
``REDIS-CLI``

### Strings
To create a key and assign it a value
``SET server:name "naaz"``

``GET server:name`` --> result="naaz"

``SET connections 10``

``GET connections`` --> result=10

``INCR connections``. This increases the value of connections by 1 --> result=11

``DECR connections``. This decreases the value of connections by 1

If you want your value to expire after a set period of time, you can use the following:

``SET resource:lock "redis Demo"``

``EXPIRE resource:lock 120`` This causes resource:lock to be deleted in 120 secs

``TTL resource:lock``
This shows you how much time is left before "redis Demo" is deleted from resource:lock

### Lists
A list is a series of ordered values

``RPUSH``
puts the new value at the end of the list e.g. ``RPUSH friends "Alice"``

``LPUSH`` puts the new value at the start of the list e.g. ``LPUSH friends "Sam"``

``LLEN`` returns current length of the list

``LRANGE`` gives a subset of the list - takes the index of the first element you want to retrieves as its first parameter and the index of the last element you want to retrieve as its second parameter. if -1 is the second parameter then retrieves elements until end of the list e.g. ``LRANGE friends 0 -1``

``LPOP`` - removes the first element from the list and returns it
RPOP - removes the last element from the string and returns it

### Set
A set is similar to a list but does not have a specific order and each element may only appear once

``SADD`` adds given value to the set e.g. SADD superpowers "flight"

``SREM`` removes the given value from the set e.g. ``SREM superpowers "reflexes"``

``SISMEMBER`` - tests is the given value is in the set. 1 --> is there. 0--> not there e.g. ``SISMEMBER superpowers "flight"``

``SMEMBERS`` returns a list of all the members of this set, e.g. ``SMEMBERS superpowers``

``SUNION`` combines 2/more sets and returns the list of all elements e.g. ``SUNION superpowers birdpowers``

### Sorted set
A Sorted set is similar to a regular set but each value has an associated score. Score is used to sort elements in the set

E.g.

``ZADD hackers 1940 "Alan Key"``

``ZADD hackers 1906 "Grace Hopper"`` --> here scores are years of the birth and values are the name of famous hackers

``ZRANGE`` e.g. ``ZRANGE 0 1`` --> Grace Hopper, Alan Key

### Hashes

 Hashes are used to store an object. Maps between string fields and string values - perfect data type to represent objects. All hash commands: http://redis.io/commands#hash

e.g.

``HSET user:1000 password "secret"``

``HSET user:1000 email "john.smith@example.com"``

``HMSET`` used to set multiple fields at once e.g. ``HMSET user:1001 name "Mary Jones" password "hidden"``

``HGETALL user:1000`` --> returns password "secret", email "john.smith@example.com"

``HGET`` e.g. ``HGET user:1000 email`` --> returns john.smith@example.com

