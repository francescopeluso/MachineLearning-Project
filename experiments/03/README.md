# Experiment 03 — U-Net con encoder ResNet18 pre-addestrato

Transfer learning: l'encoder della baseline è sostituito da una ResNet18 pre-addestrata su ImageNet (canale grayscale replicato ×3), decoder U-Net invariato. Fine-tuning completo con AdamW a learning rate ridotto (1e-4). Split, augmentation, loss e batch size identici agli esperimenti 01-02.

## Risultati principali

- Migliore Dice di validation con soglia 0,5: **0,6552** (epoca 8, early stopping all'epoca 16)
- Soglia selezionata sulla validation: **0,45**
- Dice di validation con soglia selezionata: **0,6554**
- Curva soglia–Dice quasi piatta (0,649–0,655 tra t=0,10 e t=0,90): probabilità ben calibrate, a differenza degli esperimenti 01 (t=0,15) e 02 (t=0,70)
- Memoria GPU in training: ~0,4 GiB (bonus < 5 GB rispettato)
- Test interno non eseguito: riservato alla valutazione finale del modello selezionato
