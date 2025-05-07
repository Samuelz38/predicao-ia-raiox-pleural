# predicao-ia-raiox-pleural
Repositório de IA para Mineração de Dados focado na previsão de derrame pleural em raios-X. Utiliza IA para auxiliar no diagnóstico médico através da análise de imagens radiográficas.
Claro! Aqui está um texto para o `README.md` no GitHub, bem estruturado e pronto para uso no seu repositório do projeto:

---

# 🧠 Detecção de Derrame Pleural com Redes Neurais Convolucionais (CNN)

Este projeto tem como objetivo desenvolver um modelo de aprendizado profundo para prever a presença de **derrame pleural** em imagens de raio-X de tórax, utilizando uma **Rede Neural Convolucional (CNN)**. O conjunto de dados segue o formato YOLOv8, contendo imagens e rótulos para cada exemplo.

## 📁 Estrutura do Projeto

```
plueral effusion/
├── train/
│   ├── images/
│   └── labels/
├── valid/
│   ├── images/
│   └── labels/
└── test/
    ├── images/
    └── labels/
```

Cada diretório contém:

* `images/`: imagens em formato `.jpg`
* `labels/`: arquivos `.txt` com o formato YOLO (classe x\_center y\_center width height)

## 📌 Especificações

* Total de imagens: 200
* Divisão:

  * Treinamento: 140 imagens
  * Validação: 40 imagens
  * Teste: 20 imagens
* Dimensão original das imagens: `1024x1024`
* Sem pré-processamento ou aumento de dados aplicado inicialmente.

---

## ⚙️ Tecnologias Utilizadas

* Python 3
* Google Colab
* PyTorch
* Torchvision
* PIL (Pillow)
* FPDF (para geração de PDFs)

---

## 🧾 Etapas do Pipeline

### 1. Montagem do Google Drive

Acesso ao diretório de dados:

```python
from google.colab import drive
drive.mount('/content/drive')
```

### 2. Criação de Dataset Personalizado

Classe `PleuralEffusionDataset` lê as imagens e extrai o rótulo (classe) da primeira linha do `.txt`.

### 3. Transforms

As imagens são redimensionadas para 224x224 e convertidas em tensores.

### 4. Modelo CNN

Modelo simples com:

* 2 camadas convolucionais
* 1 camada oculta densa
* Camada final com 2 saídas (classificação binária)

### 5. Treinamento

Treinamento com `CrossEntropyLoss` e `Adam` por 10 épocas.

### 6. Avaliação

Cálculo da acurácia no conjunto de teste com `torch.no_grad()`.

---

## 📊 Resultados Esperados

* **Acurácia** do modelo no conjunto de teste (depende da configuração)
* **Modelo base** para futuros aprimoramentos, como:

  * Uso de dados aumentados
  * Normalização
  * Transfer learning (ResNet, EfficientNet etc.)

---

## 📚 Referências

* Dataset gerado via Roboflow e exportado no formato YOLOv8
* Documentação YOLO: [https://docs.ultralytics.com](https://docs.ultralytics.com)
* PyTorch Docs: [https://pytorch.org/docs/stable/index.html](https://pytorch.org/docs/stable/index.html)
* Link Data Base: (https://universe.roboflow.com/pleural-effusion-chest-xray/pleural-effusion-chest-x-ray/dataset/1)

---

## ✅ Próximos Passos

* [ ] Aplicar aumento de dados (Data Augmentation)
* [ ] Testar modelos pré-treinados (ex: ResNet)
* [ ] Melhorar pré-processamento das imagens
* [ ] Exportar modelo treinado para uso clínico (ex: em apps)

