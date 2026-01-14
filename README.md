# 🏟️ Soccer Banner Segmentation - YOLO11

![Project Banner](https://img.shields.io/badge/YOLO11-Segmentation-blue?style=for-the-badge&logo=ultralytics) ![Python](https://img.shields.io/badge/Python-3.10+-yellow?style=for-the-badge&logo=python) ![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red?style=for-the-badge&logo=pytorch)

## 📋 Panoramica del Progetto

Questo progetto implementa una pipeline avanzata di **Computer Vision** per la segmentazione automatica dei banner pubblicitari nelle partite di calcio. L'obiettivo principale è identificare con precisione gli spazi pubblicitari a bordo campo per consentire applicazioni di **Realtà Aumentata**, come la sostituzione dinamica delle pubblicità (Virtual Advertising) o l'applicazione di effetti Chroma Key.

Il sistema utilizza l'architettura **YOLO11-seg** (State-of-the-Art) e segue un approccio di training **Two-Stage Transfer Learning** per massimizzare la precisione anche in presenza di occlusioni complesse (es. la rete della porta, giocatori).

---

## 🚀 Caratteristiche Principali

*   **⚡ Two-Stage Training**:
    *   **Expert Model**: Addestrato su un ampio dataset generalista (Kaggle) per apprendere le feature di base.
    *   **Specialist Model**: Fine-tuning su un dataset curato ad alta qualità (Roboflow) per gestire dettagli fini e occlusioni.
*   **🔄 Versioning Automatico**: Sistema intelligente per il salvataggio e il tracciamento delle versioni dei modelli (`v1`, `v2`, ...).
*   **🎬 Chroma Key Pipeline**: Moduli di post-processing per applicare effetti "Green Screen" direttamente sui banner rilevati nei video.
*   **📊 EDA Completa**: Notebook dedicati all'analisi esplorativa dei dati e al confronto delle annotazioni.

---

## 🛠️ Tecnologie Utilizzate

*   **Core AI**: [Ultralytics YOLO11](https://github.com/ultralytics/ultralytics) (Segmentation)
*   **Framework**: PyTorch, OpenCV
*   **Data Handling**: Pandas, NumPy, Roboflow API, Kaggle API
*   **Visualization**: Matplotlib, Seaborn

---

## 📂 Struttura del Progetto

```
.
├── SBS EDA.ipynb        # 📊 Preparazione dati e analisi esplorativa
├── SBS TRAINING.ipynb   # 🏋️ Pipeline di addestramento (Expert -> Specialist)
├── SBS INFERENCE.ipynb  # 🎬 Inferenza su video, Chroma Key e confronti
├── input/               # 📥 Cartella per i video di input
├── output/              # 📤 Risultati (video elaborati, grafici)
├── dataset/             # 🗂️ Dataset (Kaggle & Roboflow)
└── model/               # 💾 Pesi dei modelli salvati per versione
```

---

## ⚙️ Installazione e Configurazione

### 1. Prerequisiti
Assicurarsi di avere Python 3.8+ e le librerie necessarie.
```bash
pip install ultralytics opencv-python roboflow kaggle pyyaml matplotlib tqdm python-dotenv seaborn
```

### 2. Configurazione Environment
Il progetto richiede le chiavi API per scaricare i dataset. Crea un file `.env` nella root del progetto:

```env
KAGGLE_USERNAME=tuo_username
KAGGLE_KEY=tua_chiave
ROBOFLOW_KEY=tua_chiave
```

---

## 🖥️ Utilizzo

La pipeline è divisa in 3 fasi logiche:

### Fase 1: Data Preparation (`SBS EDA.ipynb`)
Esegui questo notebook per:
1. Scaricare automaticamente i dataset da Kaggle e Roboflow.
2. Effettuare lo split dei dati (70/20/10).
3. Analizzare la distribuzione delle annotazioni e generare grafici.

### Fase 2: Training (`SBS TRAINING.ipynb`)
Avvia il training per generare i modelli:
1. **Expert Training**: Addestra il modello base su ~1600 immagini.
2. **Specialist Fine-Tuning**: Raffina il modello su immagini ad alta risoluzione (1024px) con augmentations aggressive per gestire le reti delle porte.

### Fase 3: Inference (`SBS INFERENCE.ipynb`)
Usa i modelli addestrati per:
1. Caricare un video in `input/video_input.mp4`.
2. Eseguire la segmentazione e generare video con effetto Chroma Key.
3. Creare immagini di confronto "Expert vs Specialist".

---

## 📈 Risultati

La sezione seguente mostra le performance e gli output visivi del sistema.



---

## 👥 Autore

_Diego Scirocco_
