# firehose_sample

```
$ cf api https://api.10.244.0.34.xip.io --skip-ssl-validation
$ cf login
```
and then look into ```$ ~/.cf/config.json ```
```
"AccessToken": "bearer longtoken123..."
```

Note: In order to access the full firehose stream you'll need to use an admin user during cf login to generate admin access token

Once toke generated:

```
$ export CF_ACCESS_TOKEN="bearer longtoken123..."
```

And then

```
$ cd $GOPATH/src/github.com/ActiveState/firehose_sample
$ go get
$ go build -o bin/firehose_sample firehose_sample/main.go
$ $GOPATH/src/github.com/firehose_sample/bin/firehose_sample
```
The default doppler address is "ws://192.168.6.19.xip.io:51200" to update this you'll need to find out what is a correct port address by running
```
> kato config get doppler | grep outgoing_port

outgoing_port: 51200
```
and then 

```
$ $GOPATH/src/github.com/firehose_sample/bin/firehose_sample -dopplerAddress="ws://192.168.6.19.xip.io:51200"

```
