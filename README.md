# Blockchain-Based Blue Carbon Registry and MRV System

## 📌 Project Overview
This project is a decentralized, verifiable Monitoring, Reporting, and Verification (MRV) system for Blue Carbon ecosystem restoration. It ensures transparency, accuracy, and carbon credit generation using blockchain technology.

The system enables NGOs, communities, verifiers, and the public to track plantation/restoration efforts with immutable records, tokenized carbon credits, and a transparent registry.

---

## 👥 User-Side Experience

### 🌱 NGO / Community / Coastal Panchayat (Field User)
1. Opens the mobile/web app.
2. Fills out a form: project name, GPS location (auto-captured), tree species, number of saplings, area covered, uploads photo/video/drone data.
3. Upon submission:
   - Gets a **Submission ID** (status: Pending Verification).
   - Optionally connects wallet (MetaMask) for receiving carbon credits.

**From their POV:** A simple app to record plantation efforts.

---

### ✅ Verifier (Scientist, NGO Head, Government Officer)
1. Logs into Admin Dashboard.
2. Reviews pending submissions with details and media.
3. After validation, clicks **Approve**.
4. System issues **Carbon Credits (tokens)** to NGO’s wallet.

**From their POV:** A dashboard to validate and release credits.

---

### 🌍 Public / Buyers (Optional in MVP)
1. Accesses Explorer Page.
2. Views projects, GPS-marked maps, and issued credits.
3. (Future scope) Can purchase credits using stablecoins.

**From their POV:** A transparent registry of carbon sequestration.

---

## ⚙️ Backend Flow

### Step 1: Submission
- Field user submits data via form.
- Backend API:
  - Saves data in **Database (Postgres/MongoDB)**.
  - Uploads media to **IPFS (Pinata/Infura)**.
  - Stores IPFS hash in DB (status: Pending).

**Result:** NGO sees submission under Pending.

---

### Step 2: Verification
- Verifier reviews dashboard entries with IPFS links.
- On approval:
  - Backend calls **Registry Smart Contract**.
  - Writes metadata + IPFS hash to blockchain.
  - Mints **ERC20 Carbon Credits** to uploader’s wallet.
- Updates DB (status: Approved + txHash).

**Result:** NGO sees Approved + tokens in wallet.

---

### Step 3: Public Transparency
- Public can query:
  - **DB** for browsing projects.
  - **Blockchain** for immutable verification.
  - **IPFS** for raw evidence.

**Result:** Full MRV transparency, tamper-proof.

---

## 🔄 Workflow Example
1. NGO "GreenOcean" plants mangroves in Gujarat (2000 saplings, 10 acres, GPS + drone image).
2. System stores media on IPFS → DB entry Pending.
3. Verifier reviews → Approves.
4. Blockchain saves record + mints 500 **BlueCarbonTokens (BCARB)**.
5. Explorer shows project details + proof on IPFS.

---

## 🛠 Technical Architecture

| Component        | Role |
|------------------|------|
| **Frontend (React/React Native)** | Data collection, wallet login, record display |
| **Backend (Node.js)** | API, IPFS upload, DB storage, smart contract calls |
| **Database (Postgres/MongoDB)** | Store metadata (projects, users, records, txHash) |
| **IPFS** | Tamper-proof storage of raw evidence (photos, drone footage) |
| **Blockchain** | Immutable registry, smart contracts, tokenization |
| **Smart Contracts** | Registry (submissions + approvals), ERC20 Tokens (credits) |

---

## 📖 Simplified Analogy
- **IPFS** = Dropbox, but tamper-proof.  
- **Blockchain Registry** = Government Land Records, but public & immutable.  
- **Carbon Tokens** = Virtual Certificates, backed by verified data.  
- **Admin Dashboard** = Clerk’s Office, approving claims & issuing certificates.  

---

## 🚀 Hackathon Demo Flow
- NGO submits → Pending → Approval by verifier.  
- Backend: DB + IPFS + Blockchain → Tokens minted.  
- Explorer: Transparency + verification.  

---

## 📌 Future Scope
- Token marketplace for carbon credit trading.  
- Integration with stablecoins.  
- AI/ML for automated satellite/drone verification.  

---

## 📜 License
This project is developed for **SIH Hackathon** and is open for future enhancements.

