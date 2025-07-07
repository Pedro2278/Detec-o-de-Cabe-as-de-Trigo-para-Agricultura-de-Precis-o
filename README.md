# 🌾 Detecção de Cabeças de Trigo com YOLOv3

Este projeto tem como objetivo aplicar técnicas de visão computacional para detectar automaticamente espigas de trigo em imagens reais de plantações, utilizando o modelo YOLOv3. A proposta contribui com a agricultura de precisão, otimizando a contagem e monitoramento de lavouras.

## 📌 Objetivo

Automatizar a detecção de espigas de trigo com alta precisão e velocidade, usando deep learning, e avaliar o desempenho do modelo em imagens com objetos pequenos e densamente agrupados.

---

## 🛠️ Ferramentas Utilizadas

- **YOLOv3**: Modelo de detecção de objetos em tempo real.
- **Python**: Linguagem de programação principal.
- **Google Colab**: Ambiente de treinamento com suporte a GPU (A100).
- **Google Drive**: Armazenamento do dataset e integração com o Colab.
- **OpenCV**: Leitura e visualização das imagens e bounding boxes.
- **Matplotlib**: Geração de gráficos para análise visual.
- **Dataset:** [Global Wheat Head Detection](https://www.kaggle.com/competitions/global-wheat-detection/data)

---

## 🗂️ Estrutura do Projeto

├── yolov3.yaml # Arquitetura do modelo YOLOv3
├── data.yaml # Configuração do dataset (treino, validação, classes)
├── train.py # Código de treinamento
├── visualize_labels.py # Visualização das bounding boxes
├── README.md # Documentação do projeto
├── runs/detect/ # Resultados do treinamento
└── notebooks/ # Notebooks complementares (gráficos e análise)
---

## 📁 Dataset

Utilizamos o dataset **Global Wheat Head Detection**, composto por milhares de imagens com anotações em formato YOLO. Cada imagem contém espigas de trigo marcadas com coordenadas normalizadas, o que permite treinar o modelo de detecção de forma supervisionada.

---

## 🔄 Pré-processamento

- Redimensionamento das imagens para **640x640 pixels**
- Conversão das anotações para o formato YOLO (`.txt`)
- Separação do conjunto de dados: **80% para treino**, **20% para validação**
- Visualização inicial das caixas (bounding boxes) para validação visual

---

## ⚙️ Treinamento

```python
model = YOLO('yolov3.yaml')

model.train(
    data='data.yaml',
    epochs=20,
    imgsz=640,
    batch=16,
    name='wheat_yolov3',
    project='runs/detect'
)
```

- Épocas: 20
- Tamanho da imagem: 640×640
- Batch size: 16
- Taxa de aprendizado: Padrão do otimizador Adam
- Ambiente: Google Colab com GPU A100

## 📊 Resultados

| **Métrica**       | **Valor Aproximado Final** |
|-------------------|----------------------------|
| Box Loss          | ↓ 1.4                      |
| Precision         | ↑ 0.95                     |
| Recall            | ↑ 0.92                     |
| mAP@0.5           | ↑ 0.98                     |
| mAP@0.5:0.95      | ↑ 0.60                     |

**Gráfico de desempenho durante o treinamento:**

![Desempenho YOLOv3](./figuras/desempenho_treinamento.png)

🧠 Conclusão
O modelo YOLOv3 foi eficaz para detectar cabeças de trigo, mesmo em imagens com objetos pequenos e agrupados. O uso da resolução 640x640 contribuiu para a precisão das detecções. As métricas obtidas demonstram que a solução tem potencial para aplicações reais na agricultura.

📌 Trabalhos Futuros
- Testar versões mais recentes como YOLOv5 ou YOLOv8
- Melhorar o pré-processamento com aumentos de dados (data augmentation)
- Otimizar o pós-processamento para reduzir falsos positivos
- Explorar aplicações embarcadas para drones ou dispositivos agrícolas

🙋‍♂️ Autores
Pedro Henrique Vogado Maia

Licença Acadêmica
## 📝 Licença

Este projeto foi desenvolvido exclusivamente para fins acadêmicos e educacionais.

É permitido:
- Usar, estudar e modificar o código para fins de aprendizado e pesquisa.
- Compartilhar o projeto com atribuição de autoria.

Não é permitido:
- Utilizar este projeto para fins comerciais ou lucrativos sem autorização prévia.
- Distribuir versões modificadas sem citar a fonte original.

© 2025 - Pedro Henrique Vogado Maia. Todos os direitos reservados.
