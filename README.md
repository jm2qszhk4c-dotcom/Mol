import py3Dmol
from rdkit import Chem
from rdkit.Chem import AllChem
import os

‎# --- 1. تعریف و بهینه‌سازی مولکول‌ها ---

‎# اتانول (Ethanol): CCO
ethanol_smiles = "CCO"
mol_ethanol = Chem.MolFromSmiles(ethanol_smiles)
mol_ethanol = Chem.AddHs(mol_ethanol)
AllChem.EmbedMolecule(mol_ethanol, AllChem.ETKDG())
AllChem.MMFFOptimizeMolecule(mol_ethanol)
‎# متانول (Methanol): CO
methanol_smiles = "CO"
mol_methanol = Chem.MolFromSmiles(methanol_smiles)
mol_methanol = Chem.AddHs(mol_methanol)
AllChem.EmbedMolecule(mol_methanol, AllChem.ETKDG())
AllChem.MMFFOptimizeMolecule(mol_methanol)

‎# پروپان (Propane): CCC
propane_smiles = "CCC"
mol_propane = Chem.MolFromSmiles(propane_smiles)
mol_propane = Chem.AddHs(mol_propane)
AllChem.EmbedMolecule(mol_propane, AllChem.ETKDG())
AllChem.MMFFOptimizeMolecule(mol_propane)

‎# --- 2. ذخیره ساختارها در فرمت مولکولی (.mol) ---

with open("ethanol.mol", "w") as f:
  f.write(Chem.MolToMolBlock(mol_ethanol))

with open("methanol.mol", "w") as f:
    f.write(Chem.MolToMolBlock(mol_methanol))

with open("propane.mol", "w") as f:
    f.write(Chem.MolToMolBlock(mol_propane))

‎# --- 3. ایجاد نمایشگر py3Dmol (برای نمایش در خروجی نهایی رندر می‌کند) ---
view = py3Dmol.view(width=800, height=500)

view = py3Dmol.view(width=800, height=500)

view = py3Dmol.view(width=800, height=500)


‎# افزودن مدل اتانول برای نمایش در فایل HTML خروجی
view.addModel(open('ethanol.mol').read(), 'mol')
view.setStyle({'stick': {}, 'sphere': {'scale': 0.3}})
view.setBackgroundColor('white')
view.zoomTo()

view.addModel(open('methanol.mol').read(), 'mol')
view.setStyle({'stick': {}, 'sphere': {'scale': 0.3}})
view.setBackgroundColor('white')
view.zoomTo()

view.addModel(open('propane.mol').read(), 'mol')
view.setStyle({'stick': {}, 'sphere': {'scale': 0.3}})
view.setBackgroundColor('white')
view.zoomTo()


‎# ذخیره در فایل HTML
html_output = view.write_html()

with open("molecules_3d_final.html", "w") as f:
    f.write(html_output)

html_output = view.write_html()

with open("molecules_3d_final.html", "w") as f:
    f.write(html_output)



print("فایل‌های 'ethanol.mol'، 'methanol.mol' و 'propane.mol' با ساختارهای بهینه‌شده ایجاد شدند.")
print(".")  
