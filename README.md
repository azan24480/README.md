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
def read_file(file_path):
    with open(file_path, "r") as f:
        return f.readlines()

def write_file(file_path, data):
    with open(file_path, "w") as f:
        f.write(data)
