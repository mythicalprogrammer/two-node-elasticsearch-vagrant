Elasticsearch Two Nodes Setup with Vagrant
==============================

## Run

```sh
    berks install
```

```sh
    vagrant up
```

## Problem

Elasticsearch cookbook is wonky.

This is the error when you try elasticsearch command.

```sh
You must set the ES_CLASSPATH var
```

I have no idea (actually I have a hunch that the default installation for deb cookbook is bad). What I do know is you need to bring your elasticsearch to the foreground and get it going. 

```sh
   /usr/local/elasticsearch/bin/elasticsearch -f
```

And then send it back to the background CTRL-Z

Here's the discussion on the error: https://github.com/elasticsearch/cookbook-elasticsearch/issues/20

## Setup

### Vagrant

Install it. 

### [Berkshelf](http://berkshelf.com/)

Install it.

```sh
    gem install berkshelf
```

```sh
    vagrant plugin list
```

```sh
    vagrant plugin install vagrant-berkshelf
```

## TODO

Roll own shell command installation of elasticsearch since the cookbook is wonky as hell

## References

1. http://misheska.com/blog/2013/06/16/getting-started-writing-chef-cookbooks-the-berkshelf-way/
2. http://www.opscode.com/blog/chefconf-talks/the-berkshelf-way-jamie-winsor/
3. http://red-badger.com/blog/2013/06/24/berkshelf-application-cookbooks/
