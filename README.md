# Modifications of the Ethereum client OpenEthereum

## Distinuishing between `create` and `create2` messages in traces

Some time after the fork introducing the instruction `CREATE2`, Parity/OpenEthereum started to distinuish between `create` and `create2` messages in the RPC traces. However, shortly after the transition from Parity to OpenEthereum (OE), the developer team decided to revert to an old version of the project, to increase stability, and OE lost again the ability to distinguish between `create` and `create2` in the traces. The patch `distinction-create-create2-in-traces.patch` adds this ability again to recent versions of OE.

After executing the following commands, the directory `openethereum` contains the patched version of OE.

```bash
$ git clone https://github.com/openethereum/openethereum.git    # clone OE
$ git clone https://github.com/gsalzer/openethereum.git patch   # clone patch
$ cd openethereum
$ git apply ../patch/distinction-create-create2-in-traces.patch # apply patch
$ git add crates/vm/vm/src/action_type.rs                       # renamed from call_type.rs
$ git commit -a -m 'distinction create/create2 in traces'       # commit changes
$ rm -rf ../patch                                               # remove patch
```
