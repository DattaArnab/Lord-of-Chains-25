# Medical Supply Chain Deployment Guide

## Available Deployment Scripts

### 1. Basic Deployment (`MedicalSupplyChain.js`)
- Deploys the main contract without role setup
- Use for production deployments where you'll assign roles manually later

### 2. Advanced Deployment (`MedicalSupplyChainAdvanced.js`)
- Includes commented role setup
- Uncomment and modify addresses as needed
- Good for custom role assignments

### 3. Test Deployment (`MedicalSupplyChainTest.js`)
- Pre-configured with test addresses
- Automatically assigns roles during deployment
- Perfect for local development and testing

## Deployment Commands

### Local Development (Hardhat Network)
```bash
# Start local node (in separate terminal)
npm run node

# Deploy basic contract
npm run deploy:local

# Deploy with test roles pre-configured
npm run deploy:test
```

### Testnet Deployment (Sepolia)
```bash
# Make sure your .env file has API_URL and PRIVATE_KEY configured
npm run deploy:sepolia
```

### Manual Deployment Commands
```bash
# Basic deployment
npx hardhat ignition deploy ./ignition/modules/MedicalSupplyChain.js --network hardhat

# Test deployment with roles
npx hardhat ignition deploy ./ignition/modules/MedicalSupplyChainTest.js --network hardhat

# Sepolia deployment
npx hardhat ignition deploy ./ignition/modules/MedicalSupplyChain.js --network sepolia
```

## After Deployment

1. **Save the contract address** - You'll need it for your frontend
2. **Update your React app** - Replace the contract address in `Cert.json`
3. **Generate ABI** - Copy the ABI from `artifacts/contracts/PrescriptionInsuranceManager.sol/PrescriptionAndInsuranceManager.json`

## Role Management

After deployment, the contract deployer becomes the admin and can:
- Grant manufacturer roles: `grantMfg(address)`
- Grant intermediary roles: `grantInt(address)`  
- Grant pharmacist roles: `grantPhar(address)`
- Grant insurer roles: `grantIns(address)`
- Grant doctor roles: `grantDoc(address)`

Patients can register themselves using `grantPat(address)`

## Test Addresses (for local development)
- Manufacturer: `0x70997970C51812dc3A010C7d01b50e0d17dc79C8`
- Intermediary: `0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC`
- Pharmacist: `0x90F79bf6EB2c4f870365E785982E1f101E93b906`
- Insurer: `0x15d34AAf54267DB7D7c367839AAf71A00a2C6A65`
- Doctor: `0x9965507D1a55bcC2695C58ba16FB37d819B0A4dc`
