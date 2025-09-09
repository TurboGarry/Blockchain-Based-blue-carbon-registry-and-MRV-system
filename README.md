Project Walkthrough:  
let’s walk through how the project will work from two perspectives: 
 
1. User-side (NGO/community, verifier, admin, public viewer) 
 
2. Backend-side (API, blockchain, IPFS, DB, smart contracts) 
This way you’ll see both workflow (user journey) and system flow (backend). 
1. User-Side Experience (how it works 
for different actors) 
(a) NGO / Community / Coastal Panchayat (Field User) 
1. They open the mobile/web app. 
2. They fill out a form: project name, GPS location (auto-captured), tree species, number 
of saplings, area covered, upload a photo/video (or drone data). 
3. When they submit: 
o They get a “Submission ID” and see it under Pending Verification. 
o Optionally, they can connect their wallet (MetaMask) so they can later receive 
carbon credits. 
 
From their POV: Easy app to record what they planted. They don’t see blockchain, 
IPFS, or backend complexity. 
(b) Verifier (NCCR scientist, NGO head, government officer) 
1. Logs into Admin Dashboard. 
2. Sees a list of Pending Submissions (with photos, location map, project details). 
3. After field validation (or visual check in demo), clicks Approve. 
4. The system automatically issues Carbon Credits (tokens) to the NGO’s wallet. 
 
From their POV: A dashboard that allows them to check, approve, and release credits. 
(c) Public / Buyers (optional in MVP) 
1. Anyone can open the Explorer Page. 
2. They can see projects, GPS-marked maps, and which credits were issued. 
3. If extended, they could buy credits with stablecoins. 
 
From their POV: A transparent registry of carbon sequestration. 
2. Backend Flow (what happens behind 
the scenes) 
Now let’s see what happens technically when a field user uploads and a verifier approves. 
Step 1: Submission 
 Field user uploads data from mobile form. 
 Backend API: 
o Saves raw form data in Database (Postgres/Mongo). 
o Uploads photos/videos to IPFS via Pinata/Infura. 
o Stores IPFS hash in DB. 
o Marks status as Pending. 
 
Result: NGO sees their submission under Pending. 
Step 2: Verification 
 Verifier opens dashboard → sees DB entries with IPFS links. 
 When they click Approve: 
o Backend calls the Registry Smart Contract on blockchain. 
o Function: approveRecord(recordId) 
o Writes IPFS hash + metadata (tons of CO₂ captured, verifier ID) to the 
contract. 
o Registry contract then mints ERC20 Carbon Credits to the uploader’s wallet. 
 DB entry updated → status Approved, txHash stored. 
 
Result: NGO sees Approved + credits in wallet. 
Step 3: Public Transparency 
 Anyone can query: 
o DB (for fast browsing of projects). 
o Blockchain (for immutable verification of approved records). 
o IPFS (to see raw evidence). 
Result: Full MRV transparency (no data tampering possible). 
Full Workflow Example (Story) 
1.   
2.   
NGO "GreenOcean" plants mangroves in Gujarat. 
o Uploads: 2000 saplings, 10 acres, GPS + drone image. 
System: 
o Stores image on IPFS → returns hash Qm123abc. 
o Saves record in DB with status: Pending. 
3. ✅ Verifier "NCCR Officer" reviews dashboard. 
o Sees “2000 mangroves, Gujarat, photo proof”. 
o Clicks Approve. 
4.   
5.   
Blockchain: 
o Registry contract saves recordId=1, ipfsHash=Qm123abc, tons=500. 
o Token contract mints 500 BlueCarbonTokens (BCARB) to NGO’s wallet. 
Explorer: 
o Shows “Project GreenOcean, Approved, 500 Credits Issued”. 
o Public can click and view the IPFS photo as proof. 
Technical Split (Backend 
Responsibilities) 
Component 
Frontend (React/React 
Native) 
Backend (Node.js) 
Database 
IPFS 
Blockchain 
Smart Contracts 
Role 
Collects data, displays records, wallet login 
API, IPFS upload, DB storage, calls smart contracts 
Stores metadata (projects, users, record status, txHash) 
Stores raw evidence (photos, drone footage) 
Immutable registry, smart contracts, tokenization 
Registry (record submissions + approvals), ERC20 Token 
(credits) 
Simplified Analogy 
 IPFS = Dropbox, but tamper-proof. 
 Blockchain Registry = Government Land Records Office, but public and 
immutable. 
 Carbon Tokens = Virtual Certificates, backed by verified data. 
 Admin Dashboard = Government Clerk’s Office, approving claims and issuing 
certificates. 
For hackathon demo: 
 User side: NGO submits → gets pending → sees approval. 
 Backend side: DB + IPFS + blockchain contracts + tokens minted. 
 This cycle is enough to “wow” judges.
