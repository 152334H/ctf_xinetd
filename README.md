# ctf_xinetd

Modified from ctf_xinetd. This is a **template docker** folder to be copied for reuse.

This docker is designed to host a single binary-as-a-service on an open port. The binary will run with `stdbuf` and a timeout of 100s by default; change this in `ctf.xinetd` if you wish.

## Configuration

Put ALL challenge files in  `bin`; they'll be copied to /home/ctf.

Run `./setup.sh PORT EXECUTABLE NAME`. This will build & run everything in one command. Alternatively,

1. edit `Dockerfile, ctf.xinetd, start.sh` to custom your environment.
2. docker build -t "helloworld" .
3. docker run -d -p "0.0.0.0:pub_port:9999" -h "helloworld" --name="helloworld" helloworld

## Capture traffic

If you want to capture challenge traffic, just run `tcpdump` on the host. Here is an example.

```bash
tcpdump -w helloworld.pcap -i eth0 port pub_port
```
