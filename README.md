# Aleo_-demo_deploy

- Create an Aleo wallet

To create an Aleo wallet, click [here](https://aleo.tools/account). Click the Generate button, and you will see that the Private Key, View Key, and Address have been generated. Save all three parameters.

![image](https://github.com/AntonMatveychuk/Aleo_-demo_deploy/assets/101927107/32052f41-d550-4a6f-8516-dc289aa5d29f)

-  Requesting test tokens

In order to [receive](https://faucet.aleo.org/) test tokens, you need to send an SMS to the following phone number: +1-867-888-5688. The text message should read as follows:

![image](https://github.com/AntonMatveychuk/Aleo_-demo_deploy/assets/101927107/a09d7806-90b7-4d67-ae1d-31b62df33267)

- Take the server and connect to it

![image](https://github.com/AntonMatveychuk/Aleo_-demo_deploy/assets/101927107/6164827e-d782-4391-b836-57f0dbfcea91)

- Installing SnarkOS

Let's proceed to installing SnarkOS. To do this, enter the following commands into the terminal, press Enter after each command, and wait for execution:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Press Y

```
sudo apt-get install
```
```
screen -S anasayfa
```

If an error occurs, install the screen with the `apt install screen` command, then re-run the previous command and continue down the list.

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Select option 1 and press Enter

![image](https://github.com/AntonMatveychuk/Aleo_-demo_deploy/assets/101927107/96ba3d9c-be2e-4838-ac81-0c44c45a5624)

Clone the following repository from Github

```
git clone https://github.com/AleoHQ/snarkOS.git --depth 1
```
If an error occurs, install `git` with the `apt install git` command, then run the previous command again and continue down the list.

```
cd snarkOS
```
```
./build_ubuntu.sh
```
```
source $HOME/.cargo/env
```
```
cargo install --path .
```

- Customizing the Leo language

```
cd
```
```
git clone https://github.com/AleoHQ/leo
```
```
cd leo
```
```
cargo install --path .
```
```
leo
```

![image](https://github.com/AntonMatveychuk/Aleo_-demo_deploy/assets/101927107/48064983-fbf3-4ba8-98df-6c4f9048e889)

- Deploying a test app
```
cd $HOME
```
```
mkdir demo_deploy_Leo_app && cd demo_deploy_Leo_app
```

In the next command, insert your Aleo wallet address between the quotes:

```
WALLETADDRESS=""
```
```
APPNAME=helloworld_"${WALLETADDRESS:4:6}"
```
```
echo $APPNAME
```
```
leo new "${APPNAME}"
```
```
cd "${APPNAME}" && leo run && cd -
```
```
PATHTOAPP=$(realpath -q $APPNAME)
```
```
echo $PATHTOAPP
```
```
cd $PATHTOAPP && cd ..
```

In the next command, insert the private key of your Aleo wallet between the quotes:

```
PRIVATEKEY=""
```
```
snarkos developer deploy "${APPNAME}.aleo" --private-key "${PRIVATEKEY}" --query "https://vm.aleo.org/api" --path "./${APPNAME}/build/" --broadcast "https://vm.aleo.org/api/testnet3/transaction/broadcast" --priority-fee 0
```

![image](https://github.com/AntonMatveychuk/Aleo_-demo_deploy/assets/101927107/4534c010-f87e-49e9-a117-397f318ac26e)

I congratulate you, you have successfully deployed the application on Aleo, you can also check our application by entering the address of the smart contract in the explorer [here](https://aleo123.io/).
