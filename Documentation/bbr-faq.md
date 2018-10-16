# BBR FAQ

Here are some frequently asked questions about BBR congestion control.

## Where can I discuss BBR?

Comments, questions, and discussion are welcome on the public bbr-dev mailing
list:

  https://groups.google.com/d/forum/bbr-dev

## Where can I read about BBR?

There are Google publications about BBR linked at the top of the bbr-dev
mailing list home page:

  https://groups.google.com/d/forum/bbr-dev


## How can I try out Linux TCP BBR?

Check out [TCP BBR Quick-Start: Building and Running TCP BBR on Google Compute Engine](https://github.com/google/bbr/blob/master/Documentation/bbr-quick-start.md).

## How can I monitor Linux TCP BBR connections?

You can see output that includes BBR state variables, including pacing rate,
cwnd, bandwidth estimate, min_rtt estimate, etc., if you run:

```
ss -tin
```

If your machine does not have a recent enough version of ss to show those stats for BBR, you can download ss using the instructions here:
  https://wiki.linuxfoundation.org/networking/iproute2

Specifically, you can try something like:

```
git clone git://git.kernel.org/pub/scm/network/iproute2/iproute2.git
cd iproute2/
./configure
make
```

Then you can run the tool as:
```
misc/ss -tin
```

And get output like the following:


```
  bbr wscale:8,7 rto:216 rtt:15.924/4.256 ato:40 mss:1348 pmtu:1500 rcvmss:1208 advmss:1428 cwnd:16 bytes_acked:3744 bytes_received:8845 segs_out:15 segs_in:16 data_segs_out:6 data_segs_in:13 bbr:(bw:2.0Mbps,mrtt:14.451,pacing_gain:2.88672,cwnd_gain:2.88672) send 10.8Mbps lastsnd:8208 lastrcv:8188 lastack:8188 pacing_rate 22.7Mbps delivery_rate 2.0Mbps app_limited busy:68ms rcv_rtt:18.349 rcv_space:28800 rcv_ssthresh:46964 minrtt:14.451
```
