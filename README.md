# Darknode Overview
Welcome to the definitive source of information on Republic Protocol Darknodes.

## Sections

### 0. Overview
#### 0.1. Introduction
#### 0.2. FAQ
#### 0.3. Reference Links


### 1. Apply
#### 1.0. Applying to be a Darknode Operator
#### 1.1. Adding the Republic Protocol Bot
#### 1.2. The application
#### 1.3. The approval process


### 2. Install
#### 2.0. Installing and deploying a Darknode
#### 2.1. Receiving Kovan Testnet Tokens 
#### 2.2. Setting up Amazon Web Servers (AWS)
#### 2.3. Downloading and installing the Darknode CLI
#### 2.4. Deploy a Darknode
#### 2.5. Depositing ETH to operate Darknode
#### 2.6. Registering a Darknode


### 3. Operate
#### 3.0. Monitoring and maintaining a Darknode
#### 3.1. List all Darknodes on the network
#### 3.2. Starting a Darknode
#### 3.3. Stopping a Darknode
#### 3.4. Updating a Darknode
#### 3.5. SSH into a Darknode
#### 3.6. Withdrawing funds from a Darknode
#### 3.7. Deploying multiple Darknodes


### 4. Destroy
#### 4.0. Deregistering a Darknode and providing feedback
#### 4.1. Destroying a Darknode
#### 4.2. Withdrawing REN from a Darknode
#### 4.3. Providing feedback


## 0.1. Introduction
Darknodes are essential to Republic Protocol’s dark pool operation. They provide functionality to facilitate the order book, order matching engine and trade settlement.

Darknodes match orders within Republic Protocol. Requirement for running a darknode is 100,000 REN tokens staked as collateral and a fast, stable Internet connection. It is not computationally expensive to run a node. Darknodes earn fees from the orders that they match and settle. Maximum number of nodes in the protocol is expected to be less than 4,000 (not finalized). Users who provide liquidity are able to run additional darknodes because they are economically aligned with the network. This ruleset is hardcoded into the protocol. Fees can be earned in ETH and arbitrary ERC20 tokens.


## 0.2. FAQ
#### What are the requirements for running a Darknode?
100,000 REN tokens for staking as collateral.
A consistent internet connection . We recommend  using a setup with similar specifications as a T2.Small on AWS or higher — If you are unfamiliar with using cloud providers, the team will step you through the entire setup process.

#### Where can I get Kovan Testnet REN from?

#### Where can I get Kovan Testnet ETH from?
If you do not have Kovan ETH, obtain some via a public faucet such as: https://gitter.im/kovan-testnet/faucet

#### How many Darknodes can there be in operation?
10,000

#### How have the incentives been designed? 
<need more info on this>

#### Can I reserve a position as a Darknode Operator on the Mainnet (when it is launched in Q3)? 
No, This is a voluntary activity and we really appreciate active operators that are helpful in identifying issues, providing feedback and maintaining the uptime of their Darknodes.

#### Do I require Mainnet REN tokens to run a Testnet Darknode?
No, In an effort to preserve privacy, we will not be requiring users to hold mainnet REN to join the testnet.

#### When will the Mainnet be launched?
The mainnet will be launched in Q3, 2018. The team is on track and your feedback will help us in achieving this. 

#### Where do I report a bug or request help?
If you’ve found a bug, head to ..
To request help from our team, head to the Telegram.. 


## Installation
To download and install the Darknode CLI, open a terminal and run:

```sh
curl https://darknode.republicprotocol.com/install.sh -sSf | sh
```

This will download the required binaries and templates and install them to the `$HOME/.darknode` directory. Open a new terminal to begin using the Darknode CLI.

## Updating Darknode CLI
To update your Darknode CLI, open a terminal and run:

```sh
curl https://darknode.republicprotocol.com/update.sh -sSf | sh
```

This will update your Darknode CLI to the latest version.

## Usage

### Deploy a Darknode

#### AWS
To deploy a Darknode on AWS, open a terminal and run:

```sh
darknode up --name my-first-darknode --aws --aws-access-key YOUR-AWS-ACCESS-KEY --aws-secret-key YOUR-AWS-SECRET-KEY
```

The Darknode CLI will automatically use the credentials available at `$HOME/.aws/credentials` if you do not explicitly set the `--access-key` and `--secret-key` arguments.

You can also specify the region and instance type you want to use for the Darknode:

```sh
darknode up --name my-first-darknode --aws --aws-access-key YOUR-AWS-ACCESS-KEY --aws-secret-key YOUR-AWS-SECRET-KEY --aws-region eu-west-1 --aws-instance t2.small
```

You can find all available regions and instance types at [AWS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html).

You can also associate the darknode to an elastic IP by specifing the `allocation_id`.
Make sure you give the same region of the elastic to the darknode.

```sh
darknode up --name my-first-darknode --aws --aws-access-key YOUR-AWS-ACCESS-KEY --aws-secret-key YOUR-AWS-SECRET-KEY --aws-region same-region-as-EIP -aws-elastic-ip XXX.XXX.XXX.XXX
```

#### Digital Ocean

> Coming soon!

### Destroy a Darknode
/WARNING: Before destroying a Darknode make sure you have deregistered it, and withdrawn all fees earned!/

Destroying a Darknode will turn it off and tear down all resources allocated by the cloud provider. To destroy a Darknode, open a terminal and run:

```sh
darknode destroy --name my-first-darknode
```

To avoid the command-line prompt reminding you to deregister your Darknode, use the `--force` argument:

```sh
darknode destroy --name my-first-darknode --force
```

We do not recommend using the `--force` argument unless you are developing custom tools that manage your Darknodes automatically.

### List all Darknodes
The Darknode CLI supports deploying multiple Darknodes. To list all available Darknodes, open a terminal and run:

```sh
darknode list
```

### Start Darknode
To turn on your darknode, open a terminal and run:

```sh
darknode start --name my-first-darknode
```

If it's already on, `start` will do nothing.

### Stop Darknode
To turn off your darknode, open a terminal and run:

```sh
darknode stop --name my-first-darknode

```

If it's already off, `stop` will do nothing.

### SSH into Darknode
To access your Darknode using SSH, open a terminal and run:

```sh
darknode ssh --name my-first-darknode
```

### Update a Darknode
To update your Darknode to the latest stable version, open a terminal and run:

```sh
darknode update --name my-first-darknode
```

To update the config of your darknode, first edit the local version of config, by running:

```sh
nano $HOME/.darknode/darknodes/YOUR-NODE-NAME/config.json
```

Then run

```sh
darknode update --name my-first-darknode --config
```
