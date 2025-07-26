# ⚽ Blockchain-Based Football Ranking System (Solana + React)

A fully decentralized sports ranking platform for football (soccer), powered by the Solana blockchain. It uses smart contracts (Anchor in Rust) to compute ELO-based rankings, oracles (Switchboard or Chainlink) to fetch real-world match results, and a React frontend to display leaderboards, analytics, and player stats.

---

## 🌐 Live Demo

> [🔗 your-frontend-link.vercel.app](https://your-frontend-link.vercel.app)  
> *(Replace this with your actual deployed URL after Vercel deployment)*

---

## 🚀 Tech Stack

| Layer            | Tech                                   |
|------------------|----------------------------------------|
| Frontend         | React (with Next.js or Vite), Tailwind |
| Blockchain       | Solana + Anchor (Rust smart contracts) |
| Data Oracle      | Switchboard (Solana-native) or Chainlink |
| Smart Contracts  | ELO Rating Logic, Team Accounts        |
| Hosting          | Vercel / Netlify                       |

---

## 📦 Features

- ⚽ **Live Football Rankings** using the ELO rating system
- 🔗 **Decentralized & Immutable** smart contract logic on Solana
- 📈 **Leaderboards** & rating analytics displayed via React frontend
- 📡 **Oracles** fetch real-world match results (API → blockchain)
- 🧾 **Audit-Ready** on-chain storage of all match outcomes
- 🧙‍♂️ **Wallet Integration** for authorized ranking submissions

---

## 📂 Folder Structure

project-root/
│
├── app/ # React app (frontend)
│ ├── components/
│ ├── pages/ # Next.js routing
│ ├── utils/ # Solana/Anchor helpers
│ └── public/
│
├── programs/ # Anchor (Rust) smart contracts
│ ├── src/
│ └── Cargo.toml
│
├── migrations/ # Anchor deployment scripts
│
├── target/ # Anchor build artifacts
│
├── README.md
└── Anchor.toml

## 🧠 Ranking Algorithm (ELO)

Implemented on-chain via Anchor.  
```text
R_new = R_old + K * (S_actual - S_expected)

S_actual = 1 for win, 0.5 for draw, 0 for loss

S_expected = 1 / (1 + 10^((R_opp - R_self)/400))

Initial ratings start at 1500. Draws and underdog wins are handled fairly.

🔐 Solana Smart Contracts (Anchor)
Key Programs:

initialize_team(name) – Registers a team with a default rating

update_ranking(team_a, team_b, outcome) – Updates ELO ratings based on match result

All contract state is stored on-chain in team accounts. Verified transactions ensure ranking legitimacy.

📡 Oracle Data Integration
Choose one:

✅ Switchboard (Solana-native)
Create an Oracle Queue

Define REST endpoint (e.g. Sportmonks)

Feed parsed scores into your smart contract

✅ Chainlink (cross-chain)
Use Chainlink External Adapter

Fetch data from Sportmonks or API-Football

Chainlink node pushes scores to Solana program

📸 Frontend Screenshots
Add screenshots of your leaderboard, team ratings, match inputs, etc.

🛠 Setup Instructions
Prerequisites
Node.js, Yarn/NPM

Solana CLI (solana --version)

Anchor CLI (anchor --version)

Rust toolchain (rustup)

Phantom or Sollet wallet

1. Clone the repo
bash
Copy
Edit
git clone https://github.com/your-username/football-ranking-chain.git
cd football-ranking-chain

2. Install dependencies
bash
Copy
Edit
cd app
npm install

3. Configure Solana
bash
Copy
Edit
solana config set --url devnet
solana airdrop 2
anchor build
anchor deploy
Update the program ID in your frontend .env.local.

4. Run the app
bash
Copy
Edit
cd app
npm run dev
🚀 Deployment (Vercel)
Push frontend to GitHub

Connect repo to https://vercel.com

Add environment variables:

NEXT_PUBLIC_PROGRAM_ID

NEXT_PUBLIC_SOLANA_NETWORK (e.g. https://api.devnet.solana.com)

Deploy and copy the public link

🧪 Testing
Write Anchor unit tests in /tests/. Run with:

bash
Copy
Edit
anchor test
For frontend, use React Testing Library and Jest.

🧠 TODO
 Add team stats history tracking

 Enable user wallet voting for MVP players

 NFT minting for top players

 Multi-league support

📚 References
Solana Anchor Book

Switchboard Docs

Chainlink Sports Feeds

Sportmonks Soccer API

GeeksForGeeks – ELO Rating

SOAR Leaderboard SDK

🧑‍💻 Author
Akshat Chauhan
📧 akshat@example.com
🌐 LinkedIn
🌍 Portfolio

🏁 License
MIT License. Feel free to fork, contribute, and build your own blockchain apps 🚀