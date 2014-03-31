lua-resty-weedfs
================

weefs,lua,nginx and file post processing with ffmpeg and graphicsmagick


1.start weedfs with 1 replica

`
./weed master  -ip="0.0.0.0" -defaultReplication="001" -mdir="." &
./weed volume -max=100 -mserver="localhost:9333" -dir="./data/v1" -port=8083  -ip="119.254.112.171" -dataCenter="dc1" -rack="rack1" &
./weed volume -max=100 -mserver="localhost:9333" -dir="./data/v2" -port=8084  -ip="119.254.112.171" -dataCenter="dc1" -rack="rack1" &
./weed volume -max=100 -mserver="localhost:9333" -dir="./data/v3" -port=8085  -ip="119.254.112.171" -dataCenter="dc1" -rack="rack1" &
`


2.upload file to weedfs
curl http://localhost:9333/dir/assign
curl -F file=@/home/chris/myphoto.jpg http://127.0.0.1:8080/3,01637037d6

curl http://localhost:9333/dir/status?pretty=y
curl http://localhost:9333/dir/assign?dataCenter=dc1
curl http://localhost:9333/dir/assign?collection=pictures
curl http://localhost:9333/dir/assign?collection=documents


3.access file public

http://domain/img/orig/123,123123
http://domain/img/80x80/123,123123
http://domain/img/200x200/123,123123
...
