# MBB 291

Course material for MBB 291 taken on the 2nd semester of AY 2024-2025.

Access the website by clicking [here](https://dagsdags212.github.io/mbb291/).

## Running locally

Clone this repository:
```bash
git clone https://github.com/dagsdags212/mbb291.git
```

Move to directory:
```bash
cd mbb291
```

Install dependencies:
```bash
# Run if you are using conda
make init

# Run if you are using mamba/micromamba
make init ENV_MANAGER=micromamba
```

Start the server:
```bash
make
```

You can specify the port for the server (default: 1313):
```bash
# The two are equivalent commands.
make PORT=3000
make serve PORT=3000
```

You can now view the website in your browser through the following link: 

- http://localhost:1313/
