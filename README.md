# README.md

trust-wallet-pentest/
│
├── addresses/
│   ├── target_addresses.txt
│   └── generated_addresses.txt
│
├── seed_phrases/
│   ├── seed_list.txt
│   └── cracked_seeds.txt
│
├── scripts/
│   ├── address_generator.py
│   ├── seed_cracker.py
│   └── utils.py
│
├── results/
│   ├── found_seeds.txt
│   └── report.txt
│
├── README.md
└── requirements.txt
from eth_account import Account
from web3 import Web3

def crack_seed(target_address):
    Account.enable_unaudited_hdwallet_features()
    with open("seed_phrases/seed_list.txt", "r") as f:
        seeds = f.readlines()

    found_seeds = []
    for seed in seeds:
        seed = seed.strip()
        account = Account.from_mnemonic(seed)
        if account.address == target_address:
            found_seeds.append(seed)

    with open("results/found_seeds.txt", "w") as f:
        for seed in found_seeds:
            f.write(f"{seed}\n")

def main():
    with open("addresses/target_addresses.txt", "r") as f:
        target_addresses = f.readlines()

    for address in target_addresses:
        address = address.strip()
        crack_seed(address)

if __name__ == "__main__":
    main()
