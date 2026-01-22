# Week 6: Performance Evaluation and Analysis

**Student:** Ahmed Hassan | **Student ID:** A00022015 | **Module:** CMPN202 Operating Systems

---

## 1. Testing Approach

All tests performed via SSH from Windows workstation to Ubuntu Server. Tools used:
- **stress** - CPU and memory load testing
- **sysbench** - Benchmarking CPU and memory
- **fio** - Disk I/O testing
- **iperf3** - Network throughput testing
- **top/free/iostat** - System monitoring

---

## 2. Baseline Performance

### System Idle State
![Baseline Idle](images/01-baseline-idle.png)

---

### CPU Information
![CPU Info](images/02-cpu-info.png)

---

### Processes Baseline
![Top Baseline](images/03-top-baseline.png)

---

## 3. CPU Performance Testing

### CPU Stress Test
![CPU Stress](images/04-cpu-stress-test.png)

---

### Sysbench CPU Benchmark
![Sysbench CPU](images/05-sysbench-cpu.png)

---

## 4. Memory Performance Testing

### Memory Stress Test
![Memory Stress](images/06-memory-stress-test.png)

---

### Sysbench Memory Benchmark
![Sysbench Memory](images/07-sysbench-memory.png)

---

## 5. Disk I/O Performance Testing

### FIO Write Test
![FIO Write](images/08-fio-write-test.png)

---

### FIO Read Test
![FIO Read](images/09-fio-read-test.png)

---

### IOStat Output
![IOStat](images/10-iostat.png)

---

## 6. Network Performance Testing

### iperf3 Server
![iperf3 Server](images/11-iperf3-server.png)

---

### iperf3 Test Results
![iperf3 Test](images/12-iperf3-test.png)

---

### Ping Latency Test
![Ping Latency](images/13-ping-latency.png)

---

### Network Connections
![Network Connections](images/14-network-connections.png)

---

## 7. Performance Data Table

| Test | Metric | Value |
|------|--------|-------|
| **CPU** | | |
| Sysbench CPU | Events/sec | See screenshot |
| Stress test | CPU Usage | ~100% |
| **Memory** | | |
| Total RAM | Available | 2GB |
| Sysbench Memory | Throughput | See screenshot |
| **Disk I/O** | | |
| FIO Write | IOPS/Bandwidth | See screenshot |
| FIO Read | IOPS/Bandwidth | See screenshot |
| **Network** | | |
| iperf3 | Throughput | See screenshot |
| Ping (localhost) | Latency | <1ms |

---

## 8. Optimisation Testing

### Optimisation 1: TCP BBR (Network)

#### Before
![TCP Before](images/15-tcp-before.png)

#### Enable BBR
```bash
sudo sysctl -w net.core.default_qdisc=fq
sudo sysctl -w net.ipv4.tcp_congestion_control=bbr
```
![TCP BBR Enable](images/16-tcp-bbr-enable.png)

#### After
![TCP After](images/17-tcp-after.png)

**Result:** Changed from cubic to BBR - improves network throughput and reduces latency.

---

### Optimisation 2: Swappiness (Memory)

#### Before
![Swappiness Before](images/18-swappiness-before.png)

Default: 60 (too aggressive for servers)

#### Change Swappiness
```bash
sudo sysctl -w vm.swappiness=10
```
![Swappiness Change](images/19-swappiness-change.png)

#### After
![Swappiness After](images/20-swappiness-after.png)

**Result:** Reduced from 60 to 10 - server now prefers RAM over swap, improving performance.

---

## 9. Optimisation Summary

| Optimisation | Before | After | Improvement |
|--------------|--------|-------|-------------|
| TCP Congestion | cubic | bbr | Better throughput |
| Swappiness | 60 | 10 | Less swap usage |

---

## 10. Reflection

**Learned:** Performance testing methodology, identifying bottlenecks, system optimisation techniques.

**Key Findings:** 
- CPU stress causes 100% utilisation as expected
- Disk I/O is the main bottleneck on virtual machines
- BBR improves network performance
- Lower swappiness is better for servers with sufficient RAM

---

*Week 6 Complete - Ahmed Hassan (A00022015)*