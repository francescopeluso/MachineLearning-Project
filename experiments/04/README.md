# Experiment 04 — Training su patch ad alta risoluzione

Stesso modello dell'esperimento 03 (U-Net con encoder ResNet18 pre-addestrato), ma il training avviene su crop casuali 512×512 alla risoluzione nativa 2048×2048 (80% contenenti filamento). Validation e test con inferenza a tasselli 4×4 e ricomposizione a piena risoluzione; Dice calcolato sia a 512×512 (confrontabile con gli esperimenti 01-03) sia alla risoluzione nativa. Eseguito su Google Colab (CUDA).

## Risultati principali

- Migliore Dice di validation con soglia 0,5: **0,6093** (epoca 20 — nessun early stopping, modello ancora in miglioramento)
- Soglia selezionata sulla validation: **0,20**
- Dice di validation con soglia selezionata: **0,6127** (nativo: 0,6130)
- Dice sul test interno: **0,6022** (nativo: 0,6039) — eseguito manualmente con `RUN_FINAL_TEST = True`

## Esito: ipotesi NON confermata

Circa −4,5 punti Dice rispetto all'esperimento 03. La causa indicata dalle curve è la **copertura del dataset**: un crop per immagine per epoca = 1/16 dei pixel visti a parità di epoche; il best epoch è l'ultima e le curve stavano ancora salendo → modello sotto-allenato. Effetto secondario: il campionamento 80/20 sposta la soglia ottimale a 0,20.

Contromisura proposta: fine-tuning a due stadi (pesi exp 03 → poche epoche su crop nativi a lr ridotto).
