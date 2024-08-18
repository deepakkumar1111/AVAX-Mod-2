# Hyper SDK Using Custom VM

## Description
Deploying and managing a HyperChain on the Avalanche network is streamlined with this project. It offers an easy-to-follow approach for launching, configuring, and operating your personal HyperChain.

## Getting Started

### Normalize dependencies

Run the following command inside your project folder to normalize all dependencies:

```bash
go mod tidy
```

### Configure project constants

Edit the `consts/consts.go` file and fill in the missing parts:

```go
const (
	HRP = "DeepakCHAIN"
	Name = "DeepakToken"
	Symbol = "DT"
)
```

### Register actions

Go to `registry/registry.go` and register the `CreateAsset` and `MintAsset` actions:

```go
consts.ActionRegistry.Register(&actions.CreateAsset{}, actions.UnmarshalCreateAsset, false)
consts.ActionRegistry.Register(&actions.MintAsset{}, actions.UnmarshalMintAsset, false)
```

### Run the VM locally

Make sure Go is on your path. If not, run:

```bash
export PATH=$PATH:$(go env GOPATH)/bin
# OR
export PATH=$PATH:/usr/local/go/bin
```

Run the following commands:

```bash
MODE="run-single" ./scripts/run.sh
./scripts/build.sh
```

### Load demo private key

Load the demo private key included in the project:

```bash
./build/token-cli key import demo.pk
./build/token-cli chain import-anr
```

### Interact with your HyperChain

### Mint and Trade
#### Create Your Asset
```bash
./build/token-cli action create-asset
```
#### Mint Your Asset
```bash
./build/token-cli action mint-asset
```

#### View Your Balance
```bash
./build/token-cli key balance
```

### Close your Local Avalanche Network

To stop the Local Avalanche Network, run:

```bash
killall avalanche-network-runner
```

## Help

If you encounter any issues, refer to the README file or run the appropriate command for helper information.

## Authors

- Deepak Kumar

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
