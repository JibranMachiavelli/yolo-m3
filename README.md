# 🚗 M3 YOLOv11 - Detecção de Caracteres em Placas Veiculares

Sistema de reconhecimento automático de caracteres (OCR) em placas veiculares brasileiras usando YOLOv11.

## 📋 Descrição

Este projeto implementa um sistema completo de detecção e reconhecimento de caracteres alfanuméricos em placas de veículos utilizando a rede neural YOLOv11. O sistema é capaz de:

- ✅ Detectar 35 classes de caracteres (0-9 e A-Y)
- ✅ Processar imagens com múltiplos caracteres
- ✅ Avaliar performance com métricas detalhadas (mAP, Precisão, Recall, F1, IoU)
- ✅ Gerar matrizes de confusão e curvas de avaliação

## 🎯 Características

- **Modelo**: YOLOv11n (versão nano - rápida e eficiente)
- **Classes**: 35 (dígitos 0-9 + letras A-Y)
- **Dataset**: Dividido em 70% treino, 15% validação, 15% teste
- **Transfer Learning**: Modelo pré-treinado no COCO dataset
- **Métricas**: mAP, Precisão, Recall, F1-score, IoU, Matriz de Confusão

## 📦 Instalação

### Requisitos
- Python 3.8+
- pip

### Passo 1: Clonar o repositório

```bash
git clone https://github.com/JibranMachiavelli/yolo-m3.git
cd yolo-m3
```

### Passo 2: Criar ambiente virtual

```bash
python3 -m venv .venv
source .venv/bin/activate  # Linux/Mac
# ou
.venv\Scripts\activate  # Windows
```

### Passo 3: Instalar dependências

```bash
pip install ultralytics opencv-python scikit-learn matplotlib pyyaml numpy
```

## 🚀 Como Usar

### Opção 1: Avaliar Modelo Pré-treinado (Recomendado)

Se você já tem o modelo treinado (`runs_placas/yolo11_chars/weights/best.pt`):

```bash
source .venv/bin/activate
python avaliar.py
```

**Tempo**: ~5-15 minutos (depende do dataset de teste)

### Opção 2: Treinar do Zero

⚠️ **Atenção**: O treinamento pode levar várias horas em CPU!

```bash
source .venv/bin/activate
python main.py
```

**Tempo**: 2-8 horas em CPU, 30min-1h em GPU

## 📂 Estrutura do Projeto

```
yolo-m3/
├── main.py                 # Script de treinamento
├── avaliar.py             # Script de avaliação
├── README.md              # Este arquivo
├── placas_yolo/           # Dataset no formato YOLO
│   ├── images/           # Imagens (train/val/test)
│   ├── labels/           # Anotações .txt
│   └── placas.yaml       # Configuração do dataset
└── runs_placas/          # Resultados
    ├── yolo11_chars/     # Modelo treinado
    │   ├── weights/
    │   │   ├── best.pt  # Melhor modelo
    │   │   └── last.pt  # Última época
    │   ├── results.csv  # Métricas por época
    │   └── *.png        # Gráficos
    └── eval_test/        # Resultados da avaliação
        └── *.png        # Matrizes de confusão
```

## 📊 Resultados

O projeto gera automaticamente:

- **Métricas de Detecção**: mAP50-95, mAP50, Precisão, Recall, F1-score
- **Métricas por Classe**: Relatório detalhado para cada caractere
- **Visualizações**:
  - Matriz de Confusão
  - Curvas Precision-Recall
  - Curvas F1-score
  - Exemplos de predições

## 🎓 Aplicações

- 🚗 Controle de acesso (portarias, estacionamentos)
- 🚦 Fiscalização de trânsito automatizada
- 💰 Sistemas de pedágio eletrônico
- 🔍 Segurança pública (busca de veículos)
- 📊 Análise de fluxo de tráfego

## 🛠️ Tecnologias

- **Python 3.12**
- **Ultralytics YOLOv11** - Framework de detecção de objetos
- **OpenCV** - Processamento de imagens
- **PyTorch** - Backend de deep learning
- **Scikit-learn** - Métricas de avaliação
- **Matplotlib** - Visualização de resultados

## 📝 Formato dos Dados

### Anotações YOLO (.txt)

Cada imagem possui um arquivo `.txt` correspondente com o formato:

```
classe centro_x centro_y largura altura
```

Exemplo:
```
0 0.123 0.456 0.05 0.08
10 0.234 0.456 0.05 0.08
```

- **classe**: ID da classe (0-9 para dígitos, 10-34 para letras)
- **Coordenadas**: Normalizadas (0 a 1) relativas ao tamanho da imagem

## 🔧 Parâmetros de Treinamento

```python
epochs=25          # Número de épocas
imgsz=640          # Tamanho da imagem
batch=8            # Tamanho do batch
patience=10        # Early stopping
device="cpu"       # CPU ou "cuda" para GPU
```

## 📈 Métricas

- **mAP50-95**: Mean Average Precision com IoU de 0.5 a 0.95
- **mAP50**: Mean Average Precision com IoU de 0.5
- **Precisão**: Proporção de detecções corretas
- **Recall**: Proporção de objetos detectados
- **F1-score**: Média harmônica entre Precisão e Recall
- **IoU**: Intersection over Union (sobreposição das caixas)

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para:

1. Fazer um fork do projeto
2. Criar uma branch para sua feature (`git checkout -b feature/NovaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona NovaFeature'`)
4. Push para a branch (`git push origin feature/NovaFeature`)
5. Abrir um Pull Request

## 📄 Licença

Este projeto é de código aberto e está disponível para fins educacionais.

## 👥 Autores

- **Jibran Machiavelli** - [JibranMachiavelli](https://github.com/JibranMachiavelli)

## 🙏 Agradecimentos

- Ultralytics pela framework YOLOv11
- Comunidade open-source de Computer Vision
- Professores e colegas do curso

---

⭐ Se este projeto foi útil para você, considere dar uma estrela no repositório!