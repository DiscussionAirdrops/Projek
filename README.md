# Build Your Own Layer-1 Blockchain

Panduan teknis membangun Private Mainnet Ethereum menggunakan Geth. Bukan Token, tapi Blockchain Asli.


---

## ⚠️ WARNING: HARDCORE MODE

Ini **BUKAN** tutorial bikin Token (ERC-20) yang "numpang" di jaringan orang. Ini adalah tutorial membangun **Infrastructure Layer-1 (Mainnet)** sendiri. Jika mental Anda masih user token micin, tutorial ini mungkin terlalu berat.

---

## 🖥️ Tech Stack

| Komponen | Teknologi |
|----------|-----------|
| **Engine** | Go-Ethereum (Geth) |
| **Consensus** | Proof-of-Work (Ethash) |
| **Client** | Terminal / CMD |
| **Wallet** | MetaMask (Custom RPC) |

---

## 📋 Langkah-Langkah Setup

### Step 1: Persiapan Workspace

Buat folder khusus agar database tidak tercampur dengan file lain.

```bash
mkdir KoinInoMainnet
cd KoinInoMainnet
```

### Step 2: Buat Akun Validator (The "Whale")

Jalankan perintah ini untuk membuat address wallet pertama.

```bash
geth --datadir data_ino account new
```

💡 **Penting:** Simpan file di folder `keystore` dan ingat password Anda!

### Step 3: Konfigurasi Genesis (Akte Kelahiran)

Buat file `genesis.json`. Ganti `0xYOUR_ADDRESS_HERE` dengan address Anda.

```json
{
  "config": {
    "chainId": 776857489,
    "homesteadBlock": 0,
    "eip150Block": 0,
    "eip155Block": 0,
    "eip158Block": 0,
    "byzantiumBlock": 0,
    "constantinopleBlock": 0,
    "petersburgBlock": 0,
    "istanbulBlock": 0,
    "berlinBlock": 0,
    "londonBlock": 0,
    "terminalTotalDifficulty": 0
  },
  "difficulty": "0x1",
  "gasLimit": "8000000",
  "alloc": {
    "0xYOUR_ADDRESS_HERE": {
      "balance": "1000000000000000000000000"
    }
  }
}
```

### Step 4: Inisialisasi Database (The Big Bang)

```bash
geth --datadir data_ino init genesis.json
```

### Step 5: Menyalakan Node (Validator Active)

Command ini akan membuka port RPC agar bisa terkoneksi ke MetaMask.

```bash
geth --datadir data_ino --networkid 776857489 --http --http.addr "0.0.0.0" --http.port 8545 --http.corsdomain "*" --http.api eth,net,web3,miner,admin,debug --nodiscover
```

---

## 🦊 Connect to MetaMask

Tambahkan custom network ke MetaMask dengan konfigurasi berikut:

| Setting | Value |
|---------|-------|
| **Network Name** | Ino Mainnet (Local) |
| **RPC URL** | `http://127.0.0.1:8545` |
| **Chain ID** | `776857489` |
| **Symbol** | `INO` |

---

## ☕ Support the Developer

Tutorial ini gratis, tapi ilmunya mahal. Kalau script ini ngebantu kalian paham bedanya Coin vs Token, boleh banget support kopi!

- **Saweria:** [saweria.co/rakian](https://saweria.co/rakian)
- **Telegram Group:** [t.me/DiscussionAirdrops](https://t.me/DiscussionAirdrops)
- **Twitter:** [@inokrambol](https://x.com/inokrambol)

**EVM Address:** `0x2473EF56532306bEB024a0Af1065470771d92920`

---

## 📢 Disclaimer

Tools ini dibuat untuk tujuan edukasi **(Educational Purpose Only)**. Penulis tidak bertanggung jawab atas hilangnya private key atau aset.

---

## 📹 Video Tutorial

Untuk pemahaman lebih visual, tonton video tutorial di channel YouTube official.
