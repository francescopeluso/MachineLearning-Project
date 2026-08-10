# Experiment 01 — U-Net from scratch

Prima baseline con U-Net monocanale addestrata da zero, immagini ridimensionate a 512×512 e loss BCE + Dice.

## Risultati principali

- Migliore Dice di validation con soglia 0,5: **0,6415** (epoca 20)
- Soglia selezionata sulla validation: **0,15**
- Dice di validation con soglia selezionata: **0,6462**
- Dice sul test interno: **0,6157**
- Loss sul test interno: **0,2014**

I risultati e i grafici della run già conclusa sono stati recuperati dagli output incorporati nel notebook. Il checkpoint non era stato serializzato durante quella prima esecuzione: per salvarlo senza ripetere il training, eseguire la cella `Archivio dell'esperimento` mentre il modello è ancora presente nel kernel.
