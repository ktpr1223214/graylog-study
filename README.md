# graylog-study

## Setup / Test
``` bash
# 立ち上げ
$ docker-compose up
# web 画面にログイン → System/Inputs から使いたいログ形式を有効化
# ただし、予めログ形式に対応した port は開放しておく必要あり(docker-compose.yml で対応)

# ex. plain text
$ echo 'First log message' | nc 127.0.0.1 5555

# ex. gelf(tcp)
$ curl -XPOST http://127.0.0.1:12201/gelf -p0 -d '{"short_message":"Hello there", "host":"example.org", "facility":"test", "_foo":"bar"}'

# ex. gelf(udp)
# cf. http://docs.graylog.org/en/2.5/pages/gelf.html
$ echo -n '{ "version": "1.1", "host": "example.org", "short_message": "A short message", "level": 5, "_some_info": "foo" }' | nc -w0 -u 127.0.0.1 12201  
```
