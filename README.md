# Simple cloud control utility
*Yet he commanded the skies above...*


## Installation

Download the repo, compile the code for your platform.

```bash
$ git clone https://github.com/cbsd/nubectl
$ cd nubectl
$ ./build.sh
$ mv nubectl/nubectl /usr/local/bin/nubectl

```

Alternatively, to install to $GOPATH:
```bash
$ go install github.com/cbsd/nubectl@latest
```

## Usage

**nubectl** can be used with any CBSD-based platform, self-hosted, cloud-hosted or both

### with on-premise [CBSD](https://github.com/cbsd/cbsd) cluster

via env(1):

```bash
$ export CLOUD_URL="https://your-cbsd-api.endpoint.com"
$ export CLOUD_KEY="/path/to/your/ssh/key.pub"
$ export CLOUD_SSH="/path/to/your/ssh/id_ed2559"      # (optional, for SSH only )
$ nubectl --help
```

via args:

```bash
$ nubectl --cloud_url https://your-cbsd-api.endpoint.com --cloud_key /path/to/your/ssh/key.pub
$ nubectl -cloud_url=https://your-cbsd-api.endpoint.com -cloud_key=/path/to/your/ssh/key.pub
```

### Create VM or container
```bash
$ nubectl create vm test1
$ nubectl create container test2
$ nubectl status
$ nubectl list test1
$ nubectl ssh test1
$ nubectl destroy test1
```

### Infrastructure as a Code

Configure CLI

```bash
$ export CLOUD_KEY="/path/to/your/ssh/key.pub"
```

Create `config.yaml` file in `$PWD`. Refer to [example cloud config](dist.cloud.yaml)

```yaml
version: alfa

vm:
  - name: nodejsapp
    cpu: 1
    ram: 2g
    disksize: 10g
    image: centos7

container:
  - name: balancer
    type: jail
    disksize: 10g

  - name: fileshare
    type: jail
    disksize: 15g
```

Apply configuration

```bash
$ nubectl apply
```

Divert configuration

```bash
$ nubectl divert
```


## WIP
This project is under heavy development. Anything can be changed rapidly for no reason.

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[WTFPL](http://www.wtfpl.net/)
