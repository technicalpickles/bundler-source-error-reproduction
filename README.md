# bug reproduction

https://github.com/rubygems/rubygems/issues/7909


## Reproducing

Run gemstash:

```
$ gem install gemstash
$ gemstash
```

Configure for pushing locally:

```
$ gemstash authorize
$ vim ~/.gem/credentials # add the key as local_gemstash
```

Download an old bigdecimal, and publish it to gemstash

```
$ gem install bigdecimal --version 3.1.1
$ gem env path # check for cache/bigdecimal-3.1.1.gem in each
$ gem push --host http://localhost:9292/private --key local_gemstash path/to/cache/bigdecimal-3.1.1.gem
```

Bundle install, then try updating bigdecimal

```
$ bundle install
$ bundle update bigdecimal --conservative
```
