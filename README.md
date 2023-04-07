# Description

[Fluent Bit](https://fluentbit.io) input plugin that collects network usage information from Linux hosts.

This plugin **will only work** on hosts running Linux, because it relies on `/proc/net/dev` file from [Procfs](https://en.wikipedia.org/wiki/Procfs).

# Requirements

- Docker
- Docker image `fluent-beats/fluent-bit-plugin-dev`

# Build
```bash
./build.sh
```

# Test
```bash
./test.sh
 ```

# Design

This plugin was desined to collect data from any mounted Linux `network` proc file.

It can be used to collect host network usage info, even if Fluent Bit is running inside a container, which is not achiavable using **native** Fluent Bit `netif` plugin.

## Configurations

This input plugin can be configured using the following parameters:

 Key                    | Description                                   | Default
------------------------|-----------------------------------------------|------------------
 interface              | Specify the network interface to monitor      | null
 interval_sec           | Interval in seconds to collect data           | 1
 interval_nsec          | Interval in nanoseconds to collect data       | 0
 proc_path              | Path to look for net file                     | /proc
 verbose                | If true, gather metrics precisely             | false

