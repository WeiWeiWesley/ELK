Redis ELK
===

結合 reids & ELK 搜集分散式 log。適合想統一異質平台或已微服務化的系統使用。

僅需將目標 log RPUSH 至指定的 redis key，便可輕鬆地藉由 logstash 取出至 elasticserach 最後由 kibana 呈現。

## Requirement
* docker-compose
* redis

## Usage

Download
```
git clone https://github.com/WeiWeiWesley/ELK.git
```
Start
```
docker-compose up
```

## Configreation
* [docker-compose.yml](https://github.com/WeiWeiWesley/ELK/blob/master/docker-compose.yml)
* [logstash.conf](https://github.com/WeiWeiWesley/ELK/blob/master/logstash/config/logstash.conf)

```conf
# logstash.conf

input {
	redis {
		data_type => "list"
		key => "wesley"            //This key is what you RPUSH to redis
		host => "pepper_redis_1"   //Your redis's host
		port => "6379"
    	id => "test_1"
  	}
}

filter {
	sleep {
        time => "1"   # Sleep 1 second
        every => 10   # on every 10th event
	}

	json {
        source => "message"
	}
}

output {
	elasticsearch {
		index => "wesley-%{+YYYY.MM.dd}" //Index pattern
		hosts => ["elasticsearch:9200"]
	}
}
```