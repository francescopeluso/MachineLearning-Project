# Experiments

Ogni sottocartella contiene configurazione, split, metriche, grafici e checkpoint di un singolo esperimento.

Prima di avviare una nuova configurazione, modificare `EXPERIMENT_ID` nel notebook usando un numero progressivo a due cifre: `01`, `02`, `03`, ecc.

I checkpoint PyTorch (`*.pt`) vengono salvati localmente ma sono esclusi da Git tramite `.gitignore`.
