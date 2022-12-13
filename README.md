# tcpinx

In production, we have a lot of `ssh -L` happening. Say you have a `10.1.10.2:8080` in a VPC and you want to access it within your `192.168.0.0/16`, what you typically do is to `ssh -L 18080:10.1.10.2:8080 bastion_user@10.1.10.1`

However, when you have tons of servers and tons of bastions, you don't know if everyone is alive and if you gateway (the one running these ssh -L commands restarts, it's a nightmare)

Here, we propose a method combining ssh tunnel and nginx, which supports multiple bastions, config as file, liveness checking and finally even load balancing.

## Milestones

- Use iperf3 to test ssh -L overhead
- POC using Rust
- check sshtunnel in golang
- In rust using io_uring

## Outcome

Other people should be able to access http://192.168.0.2:8080/proxy/10.1.10.2:8080

I'm still thinking about how to expose TCP protocols.

