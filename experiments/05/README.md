# Experiment 05 — Fine-tuning a due stadi su crop nativi

Inizializzazione dai pesi dell'esperimento 03 (miglior modello sulle immagini ridimensionate), poi training su crop 512×512 nativi (stessa pipeline dell'exp 04) per 10 epoche con lr 1e-5 e early stopping (pazienza 4). Prima run con cache del dataset in RAM.

## Risultati principali

- Migliore Dice di validation con soglia 0,5: **0,5921** (epoca 10 — l'ultima, curva ancora in crescita)
- Soglia selezionata: **0,35** → Dice **0,5938** (nativo: 0,5965)
- Early stopping mai intervenuto

## Esito: ipotesi non confermata nella forma implementata

Il fine-tuning breve a lr molto basso adatta il modello ai crop nativi (da 0,458 a 0,5921) ma troppo lentamente: né l'exp 04 (0,6093) né l'exp 03 (0,6552) vengono raggiunti. Tutti i training su crop (exp 04 e 05) sono terminati con curve ancora crescenti → la copertura ridotta richiede budget molto maggiori.

Nota chiave: i pesi dell'exp 03 valutati a tasselli partono sotto 0,46 → il modello resize non opera a risoluzione nativa. Se Kaggle valuta a piena risoluzione, i candidati migliori sono exp 04 (nativo 0,6130) ed exp 05 (0,5965), non exp 03.
