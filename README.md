🐾 Pet Drug Safety Predictor
A computational chemistry tool that predicts whether a drug or chemical compound is safe or toxic for dogs and cats, and identifies which organ system is at risk — using molecular fingerprinting and machine learning.
---
📌 What This Project Does
Every year, thousands of pets are accidentally poisoned by medications that are safe for humans (or other species). This tool allows users to input a molecule's SMILES string and instantly get a toxicity prediction for both dogs and cats, along with the organ most likely to be affected.
Example:
Ibuprofen → ☠️ Toxic to dogs (Kidney/GI) and cats (Kidney/GI)
Permethrin → ✅ Safe for dogs, ☠️ Toxic to cats (CNS)
Amoxicillin → ✅ Safe for both
---
🔬 How It Works (The Science)
This project applies cheminformatics techniques from computational chemistry:
SMILES Parsing — Molecules are represented as SMILES strings (Simplified Molecular Input Line Entry System), a standard notation used in drug discovery.
Molecular Fingerprinting — Each molecule is converted to a binary feature vector encoding:
30 functional groups (hydroxyl, carboxylic acid, nitro groups, halogens, etc.)
11 toxicophores (structural patterns known to cause biological harm)
5 physicochemical descriptors (atom count, aromaticity, ring count, etc.)
Random Forest Classification — Two models per animal:
Toxicity classifier: Predicts Safe vs. Toxic (95% accuracy)
Organ classifier: Predicts which organ system is at risk
Dataset: 40 curated drug compounds with known pet toxicity data sourced from veterinary toxicology literature (ASPCA, FDA CVM).
---
🗂️ Project 
---
⚙️ Setup Instructions
1. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/pet-drug-safety-predictor.git
cd pet-drug-safety-predictor
```
2. Install Dependencies
```bash
pip install -r requirements.txt
```
Requirements:
Python 3.8+
numpy
pandas
scikit-learn
No RDKit or external cheminformatics library required — molecular features are computed using a custom SMILES parser.
3. Train the Model
```bash
python src/train_model.py
```
This trains the classifiers and saves them to `/models/`. Takes ~5 seconds.
---
🚀 Usage
Predict by Drug Name
```bash
python src/predict.py --name "Ibuprofen"
python src/predict.py --name "Aspirin"
python src/predict.py --name "Amoxicillin"
```
Predict by SMILES String (for any custom molecule)
```bash
python src/predict.py --smiles "CC(C)Cc1ccc(cc1)C(C)C(=O)O" --name "Ibuprofen"
python src/predict.py --smiles "CCO" --name "Ethanol"
```
List All Compounds in the Dataset
```bash
python src/predict.py --list
```
Run Model Evaluation
```bash
python src/evaluate.py
```
---
📊 Model Performance
Animal	Accuracy	ROC-AUC	Recall (Toxic)
Dogs	95.0%	1.000	100%
Cats	95.0%	1.000	100%
The model achieves 100% recall on toxic compounds — meaning it never misses a truly toxic drug. This is the most critical metric for a safety tool.
---
🧪 Sample Output
```
═══════════════════════════════════════════════════════
  🐾  PET DRUG SAFETY PREDICTOR
═══════════════════════════════════════════════════════
  Drug   : Permethrin
  SMILES : COC(=O)C(C)=CC1CC(C1)C(=O)OCc1ccc(cc1)...
───────────────────────────────────────────────────────

  🐕  DOGS
     Status     : ✅ SAFE
     Confidence : 95.9%
     Organ Risk : None identified

  🐈  CATS
     Status     : ☠️  TOXIC
     Confidence : 66.7%
     Organ Risk : CNS

───────────────────────────────────────────────────────
  📋 Known Info : SAFE for dogs but HIGHLY TOXIC to cats
  ⚠️  Severity   : 🔴 High
═══════════════════════════════════════════════════════
```
---
⚠️ Disclaimer
This tool is for educational and research purposes only. It is a course project demonstrating computational chemistry principles. Never administer any medication to a pet without consulting a licensed veterinarian.
For actual pet poisoning emergencies, contact:
ASPCA Animal Poison Control Center: +1 (888) 426-4435
Pet Poison Helpline: +1 (855) 764-7661
---
📚 References
ASPCA Animal Poison Control Center — toxic substance database
FDA Center for Veterinary Medicine (CVM)
Daylight Theory Manual — SMILES notation
Breiman, L. (2001). Random Forests. Machine Learning, 45(1), 5–32.
Rogers, D. & Hahn, M. (2010). Extended-Connectivity Fingerprints. J. Chem. Inf. Model., 50(5), 742–754.
---
# computational_chemistry_project_-PET-DRUG-SAFETY-PREDICTOR-.....*My goal is:*
Many medicines that are safe for humans can be very dangerous for pets. For example, Ibuprofen can damage a dog's kidneys, and Paracetamol can kill a cat. Most pet owners don't know this.The goal is simple: help pet owners and vets quickly check if a chemical is dangerous before giving it to an animal.
👨‍🎓 Academic Context
Course: Computational Chemistry  
Project Type: Bring Your Own Project (BYOP)  
Institution: VIT  
Submitted: April 2026


