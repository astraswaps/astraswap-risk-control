# 📜 AstraSwap Risk Control 

## ⚠️ **Disclaimer**
AstraSwap Risk Control is provided **"as-is"**, without any warranty or guarantee of performance. Users are free to **modify and use** this software as per their needs, but **AstraSwap is not responsible for any unintended consequences** that may arise due to its operation.

By using this software, you acknowledge that:
- You are operating **at your own risk**.
- AstraSwap **assumes no liability** for losses, bugs, or malfunctions.
- You should thoroughly **test and audit** the software before deploying it to a production environment.
- AstraSwap does **not provide official support** for modifications or external integrations.

Please ensure you understand the **technical implications** of this software before utilizing it in a live environment.

---

## 🌟 **Introduction**
AstraSwap Risk Control is an advanced **margin maintenance bot** specifically designed for **AstraSwap XUSD**. This bot automates margin maintenance for **Vaults** that hold collateralized assets and ensures that margin positions are adequately maintained.

### 🔄 **How It Works**
AstraSwap Risk Control continuously loops through active **Vaults**, each uniquely identified by:
- **Collateral Hash**
- **fToken Hash**
- **Account Address**

Whenever the bot detects a Vault that has surpassed the **maximum Loan-to-Value (LTV) threshold**, it takes immediate action:
✅ Transfers a predefined quantity of **fTokens** to the Vault.
✅ Receives **collateral in exchange**, ensuring that positions remain stable.

### 📅 **Operational Cycle** (As of March 20, 2025)
AstraSwap Risk Control follows a structured cycle to **monitor and maintain margin positions**:
1️⃣ Fetches the **off-chain price** of the collateral via the **AstraSwap API**.
2️⃣ Fetches **on-chain prices** for both the fToken and the collateral from AstraSwap swap pools.
3️⃣ Computes a **combined price** using the **arithmetic average** of both values.
4️⃣ Identifies **open Vaults** that have minted fTokens against collateral.
5️⃣ Loops through each Vault and evaluates its **LTV ratio**:
   - If **$FTOKEN_VALUE / $COLLATERAL_VALUE > MAX_LTV_THRESHOLD**, initiates **margin maintenance** by sending fTokens to the Vault.
6️⃣ If a **predefined collateral threshold** is reached, automatically **converts collateral into additional fTokens** using AstraSwap pools.
7️⃣ Pauses for a short period (**sleep mode**) before starting the next cycle.

By automating this process, AstraSwap Risk Control **prevents liquidations**, maintains **market stability**, and ensures that users' assets remain **secure and well-managed**.

---

## 🚀 **Getting Started**

### 🔧 **Installation & Setup**
To get started with AstraSwap Risk Control, follow these steps:

1️⃣ **Install Dependencies:**
```sh
npm install
```

2️⃣ **Choose Your Environment:**
- To run on **testnet**: `export NODE_ENV=test`
- To run on **mainnet**: `export NODE_ENV=prod`

3️⃣ **Set Up Your Wallet Private Key:**
```sh
export PRIVATE_KEY=<YOUR_PRIVATE_KEY>
```
⚠️ **Important:** Never share your private key with anyone! Ensure your system environment is **secure** before proceeding.

4️⃣ **Customize Parameters as Needed.**

5️⃣ **Start the Margin Maintenance Bot:**
```sh
npm run maintainer-dev
```
🔍 **Pro Tip:** Begin with `DRY_RUN=true` to simulate the bot’s execution **without making actual transactions**. This allows you to verify calculations and configurations before deployment.

---

## 🛠️ **Deploying to Production**
Once you have successfully tested AstraSwap Risk Control, you can deploy it to a live environment:

1️⃣ **Build the project:**
```sh
npm run build
```

2️⃣ **Create a Docker Image:**
```sh
docker build -t AstraSwap_margin_maintainer .
```

3️⃣ **Run the container:**
```sh
docker run -d AstraSwap_margin_maintainer
```

By running AstraSwap Risk Control in a **containerized environment**, you ensure **greater stability, security, and scalability**.

---

## 🎯 **Tunable Parameters**

AstraSwap Risk Control allows customization through various tunable parameters:

| **Option** | **Description** |
|------------|----------------------------------------------------------------|
| `FTOKEN_SCRIPT_HASH` | Hash of the fToken used for margin maintenance. |
| `COLLATERAL_SCRIPT_HASH` | Hash of the collateral asset being received. |
| `WEBHOOK_URL` | URL for **Discord webhook notifications**. [Guide](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks) |
| `MAINTAINER_NAME` | Name used in **webhook messages** to differentiate instances. |
| `MAINTENANCE_THRESHOLD` | Minimum margin maintenance quantity in fTokens. Transactions below this will be ignored. |
| `LOW_BALANCE_THRESHOLD` | If balance falls below this value, an alert will be sent to the webhook URL. |
| `AUTO_SWAP` | If `true`, collateral is automatically swapped into fTokens when balance exceeds `SWAP_THRESHOLD`. |
| `SWAP_THRESHOLD` | Minimum collateral balance required to trigger an automatic swap. |
| `VERIFY_WAIT_MILLIS` | Wait time for **transaction confirmations** (in milliseconds). |
| `SLEEP_MILLIS` | Duration between cycles (in milliseconds). Recommended: **15,000 ms** (~15s). |
| `DRY_RUN` | If `true`, the bot will **simulate** transactions without executing them. |

⚠️ **Caution:** Adjusting these parameters requires **expert knowledge of AstraSwap and EpicChain development**. Proceed with caution!

---

## 🛠️ **Debugging in VS Code**
If you are developing on **Visual Studio Code**, you can easily debug AstraSwap Risk Control:

1️⃣ **Add your private key** to the `.env` file:
```sh
PRIVATE_KEY=<YOUR_PRIVATE_KEY>
```

2️⃣ **Use breakpoints** to analyze execution and optimize performance.

3️⃣ **Monitor logs** for error messages and warnings.

---

## 💡 **Conclusion**
AstraSwap Risk Control provides an **automated, efficient, and secure** solution for managing **margin maintenance** in the AstraSwap ecosystem. By integrating with AstraSwap’s **on-chain and off-chain price feeds**, it ensures that Vaults remain **properly collateralized**, reducing the risk of **liquidations** and **market instability**.

🔹 **Fully Automated** – Eliminates manual intervention for risk control.
🔹 **Configurable** – Offers a range of tunable parameters for **customization**.
🔹 **Secure & Scalable** – Supports **containerized deployments** via Docker.
🔹 **Transparent Operations** – Logs and webhook alerts provide **real-time monitoring**.

---

## 🌍 **Join the AstraSwap Community**
Stay up to date with the latest developments and engage with other AstraSwap users!

💬 **Telegram:** [Join Now](#)
🐦 **Twitter/X:** [Follow Us](#)
📢 **Discord:** [Join Our Server](#)
📜 **GitHub:** [Explore the Code](#)

🚀 **AstraSwap - The Future of Decentralized Finance!** 🔥

