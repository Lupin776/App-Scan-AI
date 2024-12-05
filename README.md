# Scan.IA - README

Este é o repositório do projeto **Scan.IA**, um aplicativo inteligente que utiliza técnicas de inteligência artificial para identificar logos de empresas em imagens. O sistema foi construído utilizando dois métodos de aprendizado de máquina, **K-means** e **SVM (Support Vector Machine)**, para realizar a tarefa de reconhecimento de logos com alta precisão.

### Tecnologias Usadas

1. **K-means Clustering**
2. **Support Vector Machine (SVM)**

## K-means

**K-means** é um algoritmo de aprendizado não supervisionado utilizado para agrupar dados em diferentes clusters (grupos). O objetivo do K-means é dividir um conjunto de dados em *k* grupos com base em características similares, minimizando a variabilidade dentro de cada cluster. O método é utilizado no Scan.IA para pré-processamento das imagens e segmentação, ou seja, identificar as regiões da imagem que possuem características visuais semelhantes, antes de realizar a detecção de logos.

### Como Funciona o K-means:
1. **Inicialização**: O algoritmo começa com a seleção aleatória de *k* centroides (pontos centrais).
2. **Atribuição de pontos aos centroides**: Cada ponto de dados (no caso, pixels ou regiões de uma imagem) é atribuído ao centroide mais próximo.
3. **Atualização dos centroides**: Os centroides são recalculados com base nos pontos atribuídos a eles.
4. **Iteração**: O processo de atribuição e atualização continua até que os centroides não mudem mais, ou até um número máximo de iterações ser alcançado.

No contexto do Scan.IA, o **K-means** é utilizado para ajudar na segmentação das imagens. Ele agrupa as áreas de interesse (como formas ou cores características de um logo), facilitando a posterior identificação dos logos por outras técnicas, como o SVM.

### Vantagens do K-means:
- Simplicidade e eficiência.
- Capacidade de lidar com grandes volumes de dados.
- Útil para tarefas de agrupamento e pré-processamento de imagens.

### Desvantagens do K-means:
- Necessidade de definir o número de clusters (k) de antemão.
- Sensível à inicialização dos centroides.
- Pode ter dificuldades em detectar clusters de forma não esférica.

---

## Support Vector Machine (SVM)

**SVM** é um algoritmo de aprendizado supervisionado utilizado para classificação e regressão. No Scan.IA, a técnica **SVM** é aplicada para classificar as regiões da imagem, identificando se elas contêm ou não logos de empresas. O SVM tenta encontrar uma linha ou hiperplano (em dimensões superiores) que melhor separe as classes de dados (neste caso, logos e não-logos).

### Como Funciona o SVM:
1. **Transformação dos Dados**: As imagens são extraídas e transformadas em um conjunto de características (features), como cores, formas e bordas.
2. **Escolha do Hiperplano Ótimo**: O SVM busca o hiperplano que maximiza a margem entre as duas classes, separando-as da maneira mais eficiente possível. No caso de imagens de logos, ele tenta separar a classe "logo" da classe "não-logo".
3. **Classificação**: Quando uma nova imagem é fornecida, o SVM a classifica em uma das classes com base no aprendizado realizado.

No Scan.IA, o **SVM** é treinado usando um conjunto de dados de imagens rotuladas (com logos e sem logos) para aprender a identificar logos em novas imagens. Quando uma imagem é carregada, o modelo classifica as regiões da imagem que podem conter logos.

### Vantagens do SVM:
- Alta precisão na classificação, mesmo em problemas complexos.
- Eficaz em espaços de alta dimensão (como características extraídas de imagens).
- Pode ser usado tanto para classificação linear quanto não linear.

### Desvantagens do SVM:
- O treinamento pode ser demorado para grandes conjuntos de dados.
- Sensível à escolha dos parâmetros e ao pré-processamento dos dados.
- Requer um bom conjunto de dados rotulados para treinamento.

---

## Como o Scan.IA usa o K-means e o SVM

No Scan.IA, as duas técnicas de aprendizado de máquina são usadas em conjunto para otimizar a detecção de logos em imagens:

1. **K-means** realiza a segmentação da imagem, identificando áreas com padrões visuais semelhantes que podem conter logos.
2. **SVM** é utilizado para classificar essas áreas, determinando se elas representam um logo de alguma marca.

Dessa forma, o Scan.IA consegue identificar logos com alta precisão e em tempo real, mesmo em imagens que podem estar distorcidas ou com variações no ângulo.
Este projeto é apenas uma implementação inicial e pode ser expandido com mais funcionalidades, como treinamento com novos logos, integração com APIs externas para reconhecimento em tempo real, e muito mais.
