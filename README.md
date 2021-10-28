# Modifications of the Ethereum client [OpenEthereum](https://github.com/openethereum/openethereum)

## Distinguishing between `create` and `create2` messages in traces

Some time after the fork introducing the instruction `CREATE2`, Parity/OpenEthereum started to distinguish between `create` and `create2` messages in the RPC traces. However, shortly after the transition from Parity to OpenEthereum (OE), the developer team decided to revert to an old version of the project, to increase stability, and OE lost again the `create`/`create2` distinction in the traces ([OE issue #114](https://github.com/openethereum/openethereum/issues/114)). The patch `distinction-create-create2-in-traces.patch` reintroduces this ability to recent versions of OE.

After executing the following commands, the directory `openethereum` contains the patched version of OE.

```bash
git clone https://github.com/openethereum/openethereum.git    # clone OE
git clone https://github.com/gsalzer/openethereum.git patch   # clone patch
cd openethereum
git apply ../patch/distinction-create-create2-in-traces.patch # apply patch
git add crates/vm/vm/src/action_type.rs                       # renamed from call_type.rs
git commit -a -m 'distinction create/create2 in traces'       # commit changes
rm -rf ../patch                                               # remove patch
```

Latest version tested: `OE v3.3.0-rc.12` with `rustc 1.51.0`
