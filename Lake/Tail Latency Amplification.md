**Tail latency amplification** - effect such that when in order **to serve single request**, there're multiple **other backend calls needed**. Even though ran in parallel, source request will have to **wait for the slowest request**.