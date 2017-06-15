# Load Testing Utility
Ruby utility to load test your service/URL from mutiple instances in different AWS regions in an effort to simulate real world traffic.

# What's involved?
* Clone the repository locally
* Add all key pair .pem files (for different regions) to the config directory
* Add details to config.yml
* `docker build -t loadtest .`
* `docker run -t loadtest`
* `docker exec -it <contaner id> bash`
* `ruby load_test.rb`

# Sample Output
<pre>
ap-south-1 Instances:
--------------------------------------------------------------------------------
i-012d982950f687d04 - pending
i-05843e3bc8a2bfbe1 - pending
i-02ed55d9ec915f223 - pending
--------------------------------------------------------------------------------
us-east-1 Instances:
--------------------------------------------------------------------------------
i-013644e8b6bb377d8 - pending
i-0690d7be69ac72458 - pending
--------------------------------------------------------------------------------
Sleeping for 5 minutes to make sure instances are ready...
/Master command id for ap-south-1: 45118391-a684-4f2e-8b1d-16caf6071657
Master command id for us-east-1: 3b3bce1f-d1c9-4987-84ea-e889ae0a783f
Sleeping for 1 minute to make sure command invocation has reached the EC2 instances...
~~~~~~~~~~~~~~~~~~\___/~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~********************************************************************************
Output on instance id i-012d982950f687d04 from region ap-south-1
********************************************************************************
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking example.com (be patient).....done


Server Software:        ECS
Server Hostname:        example.com
Server Port:            80

Document Path:          /
Document Length:        1270 bytes

Concurrency Level:      10
Time taken for tests:   2.116 seconds
Complete requests:      100
Failed requests:        0
Keep-Alive requests:    100
Total transferred:      160500 bytes
HTML transferred:       127000 bytes
Requests per second:    47.26 [#/sec] (mean)
Time per request:       211.600 [ms] (mean)
Time per request:       21.160 [ms] (mean, across all concurrent requests)
Transfer rate:          74.07 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0   19  55.9      0     192
Processing:   184  186   2.4    185     193
Waiting:      184  186   2.4    185     193
Total:        184  204  55.9    185     384

Percentage of the requests served within a certain time (ms)
  50%    185
  66%    186
  75%    187
  80%    187
  90%    367
  95%    370
  98%    373
  99%    384
 100%    384 (longest request)
################################################################################
********************************************************************************
Output on instance id i-05843e3bc8a2bfbe1 from region ap-south-1
********************************************************************************
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking example.com (be patient).....done


Server Software:        ECS
Server Hostname:        example.com
Server Port:            80

Document Path:          /
Document Length:        1270 bytes

Concurrency Level:      10
Time taken for tests:   2.098 seconds
Complete requests:      100
Failed requests:        0
Keep-Alive requests:    100
Total transferred:      160500 bytes
HTML transferred:       127000 bytes
Requests per second:    47.66 [#/sec] (mean)
Time per request:       209.819 [ms] (mean)
Time per request:       20.982 [ms] (mean, across all concurrent requests)
Transfer rate:          74.70 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0   19  56.2      0     190
Processing:   184  187   1.8    186     191
Waiting:      184  187   1.8    186     191
Total:        184  206  56.2    186     381

Percentage of the requests served within a certain time (ms)
  50%    186
  66%    188
  75%    189
  80%    191
  90%    368
  95%    372
  98%    378
  99%    381
 100%    381 (longest request)
################################################################################
********************************************************************************
Output on instance id i-02ed55d9ec915f223 from region ap-south-1
********************************************************************************
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking example.com (be patient).....done


Server Software:        ECS
Server Hostname:        example.com
Server Port:            80

Document Path:          /
Document Length:        1270 bytes

Concurrency Level:      10
Time taken for tests:   2.119 seconds
Complete requests:      100
Failed requests:        0
Keep-Alive requests:    100
Total transferred:      160500 bytes
HTML transferred:       127000 bytes
Requests per second:    47.18 [#/sec] (mean)
Time per request:       211.949 [ms] (mean)
Time per request:       21.195 [ms] (mean, across all concurrent requests)
Transfer rate:          73.95 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0   19  56.7      0     192
Processing:   184  189   2.5    190     194
Waiting:      184  189   2.5    190     194
Total:        184  208  56.8    190     385

Percentage of the requests served within a certain time (ms)
  50%    190
  66%    190
  75%    191
  80%    192
  90%    368
  95%    379
  98%    381
  99%    385
 100%    385 (longest request)
################################################################################
********************************************************************************
Output on instance id i-013644e8b6bb377d8 from region us-east-1
********************************************************************************
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking example.com (be patient).....done


Server Software:        ECS
Server Hostname:        example.com
Server Port:            80

Document Path:          /
Document Length:        1270 bytes

Concurrency Level:      10
Time taken for tests:   0.030 seconds
Complete requests:      100
Failed requests:        0
Keep-Alive requests:    100
Total transferred:      160000 bytes
HTML transferred:       127000 bytes
Requests per second:    3289.37 [#/sec] (mean)
Time per request:       3.040 [ms] (mean)
Time per request:       0.304 [ms] (mean, across all concurrent requests)
Transfer rate:          5139.63 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.4      0       2
Processing:     2    3   0.7      2       5
Waiting:        2    3   0.7      2       5
Total:          2    3   1.0      3       6
WARNING: The median and mean for the processing time are not within a normal deviation
        These results are probably not that reliable.
WARNING: The median and mean for the waiting time are not within a normal deviation
        These results are probably not that reliable.

Percentage of the requests served within a certain time (ms)
  50%      3
  66%      3
  75%      3
  80%      3
  90%      4
  95%      6
  98%      6
  99%      6
 100%      6 (longest request)
################################################################################
********************************************************************************
Output on instance id i-0690d7be69ac72458 from region us-east-1
********************************************************************************
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking example.com (be patient).....done


Server Software:        ECS
Server Hostname:        example.com
Server Port:            80

Document Path:          /
Document Length:        1270 bytes

Concurrency Level:      10
Time taken for tests:   0.033 seconds
Complete requests:      100
Failed requests:        0
Keep-Alive requests:    100
Total transferred:      160000 bytes
HTML transferred:       127000 bytes
Requests per second:    3058.29 [#/sec] (mean)
Time per request:       3.270 [ms] (mean)
Time per request:       0.327 [ms] (mean, across all concurrent requests)
Transfer rate:          4778.58 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.6      0       2
Processing:     2    3   0.9      3       5
Waiting:        2    3   0.7      2       5
Total:          2    3   1.2      3       6
WARNING: The median and mean for the waiting time are not within a normal deviation
        These results are probably not that reliable.

Percentage of the requests served within a certain time (ms)
  50%      3
  66%      3
  75%      4
  80%      4
  90%      5
  95%      6
  98%      6
  99%      6
 100%      6 (longest request)
################################################################################
Sleeping for 2 minutes before terminating EC2 instances. In case you do not want this press <ctrl> c ...
-Terminating instance i-012d982950f687d04  ︻デ┳═ー
Terminating instance i-05843e3bc8a2bfbe1  ︻デ┳═ー
Terminating instance i-02ed55d9ec915f223  ︻デ┳═ー
Terminating instance i-013644e8b6bb377d8  ︻デ┳═ー
Terminating instance i-0690d7be69ac72458  ︻デ┳═ー
</pre>

# Config file
Be careful with extra spaces and tabs while editing the yml file.
<pre>
---
:aws_access_key_id: Your AWS_ACCESS_KEY_ID
:aws_secret_access_key: Your AWS_SECRET_ACCESS_KEY
:instance_type: t2.micro
:ssm_role: "IAM Role used by SSM"
:command_timeout: 18000
:region_data:
- :region: ap-south-1
  :ami_id: ami-995c23f6
  :key: mumbai-loadtesting
  :node_count: 3
  :commands:
  - ab -k -c 10 -n 100 "http://example.com/"
- :region: us-east-1
  :ami_id: ami-34193d22
  :key: loadtesting
  :node_count: 2
  :commands:
  - ab -k -c 10 -n 100 "http://example.com/"
</pre>

