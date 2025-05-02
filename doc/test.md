# `%chain-watcher` Testing

Here are some of the key queries:

```
=s -build-file /=chain-watcher=/sur/chain-watcher/hoon
.^((set path) %gx /=chain-watcher=/dogs/noun)
.^((map path config:s) %gx /=chain-watcher=/dogs/configs/noun)
.^(@ %gx /=chain-watcher=/block/…/atom)
```

And here are some basic commands to track Ethereum contract interactions:

```
:chain-watcher &chain-watcher-poke [%watch path=/chain/usdc config=['https://sepolia.drpc.org' | ~s10 ~m1 5.621.625 ~ [0xb962.e45f.3381.4833.744b.8a10.2c7c.626a.98b3.2e38]~ `6 ~]]
:chain-watcher &chain-watcher-poke [%watch path=/chain/susd config=['https://sepolia.drpc.org' | ~s10 ~m1 6.227.269 ~ [0xb962.e45f.3381.4833.744b.8a10.2c7c.626a.98b3.2e38]~ `6 ~[0x0 0x0 0x1117.bfea.1e43.d16b.a9c2.6d06.1a77.a347.3908.330e]]]
:chain-watcher &chain-watcher-poke [%watch path=/chain/sazp config=['https://sepolia.drpc.org' | ~s10 ~m1 5.823.305 ~ [0xabe2.8c76.e1c9.750e.b78f.32a0.7c29.5afa.99b5.57fd]~ `6 ~[0x0 0x0 0x6e3d.b180.ad7d.ea45.08f7.766a.5c05.c406.cd6c.9dcf 0x0]]]
:chain-watcher &chain-watcher-poke [%clear path=/chain/usdc]
```
