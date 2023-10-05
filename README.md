# SharePublic
sudo apt install openjdk-8-jre-headless

sudo apt-get update

sudo apt-get install logstash

sudo vi /etc/logstash/conf.d/logstash.conf

input {
		file {
				path => "/home/gobangcir/access.log"
					start_position => "beginning"
		}
}

filter {
		grok {
				match => { "message" => "%{COMBINEDAPACHELOG}" }
		}
		date {
				match => [ "timestamp", "dd/MMM/yyyy:HH:mm:ss Z" ]
		}
}

output {
		elasticsearch {
				host => ["localhost:9200"]
		}
		stdout {
				codec => rubydebug
		}
}

sudo wget media.sundog-soft.com/es/access_log

sudo apt-get update && sudo apt-get install logstash

cd /usr/share/logstash/

sudo bin/logstash -f /etc/logstash/conf.d/logstash.conf
