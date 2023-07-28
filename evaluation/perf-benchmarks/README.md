## Testing using Bandwith Tests
A set of bandwidth benchmarks were used to test the monitoring tools:
|Operation| Command| Description|
|:----|:----|:----|
|Send| ib_send_bw|  bandwidth test with send transactions|
|RDMA Read| ib_read_bw|  bandwidth test with RDMA read transactions|
|RDMA Write| ib_write_bw|  bandwidth test with RDMA write transactions|
|RDMA Atomic| ib_atomic_bw|  bandwidth test with atomic transactions|


The benchmarks generate a synthetic stream of operations, which is very useful for hardware and software benchmarking and analysis. The benchmarks are not designed to emulate any real application traffic. Real application traffic may be affected by many parameters, and hence might not be predictable based only on the results of those benchmarks.

Command Examples:
On server side:
```
ib_write_bw -d mlx5_2 -R
```
On client side:
```
ib_write_bw  -d mlx5_2 10.128.14.17 -R -F -D 100
```
The screenshots from experiments are as follows:
![alt text](https://github.com/niks16/iNet/blob/main/screenshots/RDMA_SEND_perf.png?raw=true)
![alt text](https://github.com/niks16/iNet/blob/main/screenshots/RDMA_READ_perf.png?raw=true)
![alt text](https://github.com/niks16/iNet/blob/main/screenshots/RDMA_WRITE_perf.png?raw=true)
![alt text](https://github.com/niks16/iNet/blob/main/screenshots/RDMA_ATOMIC_perf.png?raw=true)
