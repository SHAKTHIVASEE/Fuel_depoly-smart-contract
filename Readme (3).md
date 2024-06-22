
# Deploying a Contract on Fuel Network 

## Install Dependencies 

```
sudo apt update
sudo apt upgrade -y
sudo apt-get install curl screen -y 
```

## Install RUST 

```
curl --proto '=https' --tlsv1.3 https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustc --version
```

```
rustup install stable
rustup update stable
rustup default stable
```

## Install GIT 
```
sudo apt install git -y 
```


## Install Fuel-Toolchain 

```
curl https://install.fuel.network | sh
```

### Press y then enter

### Setting PATH 

```
PATH="${HOME}/.fuelup/bin:${PATH}"
```
```
source /root/.bashrc
```
```
sudo su
```
### Setting FUELUP

```
fuelup toolchain install latest
fuelup self update
fuelup update && fuelup default latest
```

## Creating Project 

```
mkdir fuel-project && cd fuel-project
forc new counter-contract
```
### Editing Contract 

```
nano counter-contract/src/main.sw
```

Clear/delete everything and paste below code

```
contract;
 
storage {
    counter: u64 = 0,
}
 
abi Counter {
    #[storage(read, write)]
    fn increment();
 
    #[storage(read)]
    fn count() -> u64;
}
 
impl Counter for Contract {
    #[storage(read)]
    fn count() -> u64 {
        storage.counter.read()
    }
 
    #[storage(read, write)]
    fn increment() {
        let incremented = storage.counter.read() + 1;
        storage.counter.write(incremented);
    }
}
```


### Save and exit with Ctrl X then y   and click  ENTER 

--------------------------------------

## Build Contract 
```
cd counter-contract
forc build 
```

## Deploying Contract 



### Importing wallet Phrase key from fuel wallet
```
forc wallet import 
```

### Note - password are always not shown


### Create Account 

```
forc wallet account new
```

### Import account and input password 



### Check Address 

```
forc wallet accounts
```
---------

### Deploy Contract 

```
forc deploy --testnet 
```

### Enter 0 as Index and click y

### Now your CONTRACT as been DEPLOYED 

### Check you transaction in fuel wallet transaction  history...

# For upcoming project Follow in github..











