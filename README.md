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

Open Kibana

http://127.0.0.1:5601

## Configreation
* [docker-compose.yml](https://github.com/WeiWeiWesley/ELK/blob/master/docker-compose.yml)
* [logstash.conf](https://github.com/WeiWeiWesley/ELK/blob/master/logstash/config/logstash.conf)

```conf
# logstash.conf

input {
	redis {
		data_type => "list"
		key => "ios_key"
		host => "redisA"
		port => "6379"
		id => "ios"
		tags => ["ios", "example"]
	}

	redis {
		data_type => "list"
		key => "android_key"
		host => "redisB"
		port => "6379"
		id => "android"
		tags => ["android", "example"]
	}
}

filter {
	if "example" in [tags] {
		json {
			source => "message"
		}
	}
}

output {
	if "_jsonparsefailure" not in [tags] {
		if "ios" in [tags] {
			elasticsearch {
				index => "ios-%{+YYYY.MM.dd}"
				hosts => ["elasticsearch:9200"]
			}
		}

		if "android" in [tags] {
			elasticsearch {
				index => "android-%{+YYYY.MM.dd}"
				hosts => ["elasticsearch:9200"]
			}
		}
	}

}

```