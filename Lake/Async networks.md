![[Shared-nothing architecture#^6b450e]]

**Asynchronous packet network** (Ethernet) provides **no guarantees** regarding **when message will arive** or whether **will it arrive** at all. In other words, [[Network Unbounded Delay|latency is unbounded]].

**Async nets** are good **for bursty traffic** (sending an email, requesting a web page, etc), but are **poor for continuous traffic** (videos). ^07b634

Networks are used for [[Network for failed nodes detection|failed nodes detection]], but not at all are they reliable.

We can't know what happened when we don't receive response. Usually sender **[[Network Timeouts|timeouts]]** are used to **give up on waiting** for the response, but host **may receive response** later **when it don't wait for it anymore**.

**Issues with network** (see [[Network faults in practice]]):
- **request** may be **lost** (network cable);
- **request** may be **delayed** (overloaded network or recepient);
- **remote host** may've **failed** (powered off);
- **remote host stopped responding** (process pause);
- **response** may be **lost** (misconfigured switch);
- **response** may be **delayed** (overloaded network or local host).

