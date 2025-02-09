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

def generate_address(seed_phrase):
    Account.enable_unaudited_hdwallet_features()
    account = Account.from_mnemonic(seed_phrase)
    return account.address

def main():
    with open("seed_phrases/seed_list.txt", "r") as f:
        seeds = f.readlines()

    with open("addresses/generated_addresses.txt", "w") as f:
        for seed in seeds:
            seed = seed.strip()
            address = generate_address(seed)
            f.write(f"{seed}: {address}\n")

if __name__ == "__main__":
    main()
