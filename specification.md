## Services

### treactor-ui


## treactor-api

`/treact/split?molecule=[h]`

## bound-n

`/treact/bound/n?molecule=[h]`

## atom-x

`/treact/atom/x?symbol=[h]`


## Environment Variables

NAME | Description | Default
---- | ----------- | -------
PORT | Port |
SERVICE_NAME | Application name | treactor
SERVICE_VERSION | Application version | 0.0.0
TREACTOR_MODE | Reactor mode (local, k8s) | local
TREACTOR_TRACE_PROPAGATION | OpenTelemetry propagator (w3c)  | w3c

## Molecule spec


```
S    [H,x=1,y=2,z=3]*2[O,x=1,y=2,z=3],x=1,y=2,z=3
A     H,x=1,y=2,z=3
A                      O,x=1,y=2,z=3
```


```
S    2[5[Ur,log:1,xyz:4]^5[C,log:1,xyz:4]],x:1,y:2
O1     5[Ur,log:1,xyz:4]^5[C,log:1,xyz:4]
A        Ur,log:1,xyz:4
A                          C,log:1,xyz:4
```
