# Facility Location Problem (FLP)

## 1. Definindo o Contexto
Imagine que estamos gerenciando uma empresa de e-commerce que quer melhorar a eficiência de entrega abrindo novos centros de distribuição em uma cidade. O objetivo é atender à demanda de 20 clientes, espalhados pela cidade, com 4 possíveis localizações para os centros de distribuição. Cada centro tem um custo fixo de instalação e uma capacidade máxima de atendimento.

## 2. Objetivo do Problema
Minimizar o custo total da operação, composto por:
   - **Custo Fixo**: Custo para construir e operar um centro de distribuição em uma determinada localização.
   - **Custo de Transporte**: Custo para transportar mercadorias do centro de distribuição para os clientes, baseado na distância entre eles.

## 3. Entradas do Problema
   - **Localizações candidatas**: Existem quatro localizações possíveis onde podemos instalar centros de distribuição. Cada uma tem um custo fixo e uma capacidade máxima:
     - Localização A: Custo Fixo = 50, Capacidade = 189
     - Localização B: Custo Fixo = 40, Capacidade = 159
     - Localização C: Custo Fixo = 70, Capacidade = 159
     - Localização D: Custo Fixo = 60, Capacidade = 129
   - **Demanda dos clientes**: Temos 20 clientes, cada um com uma demanda específica de mercadorias.
   - **Distâncias**: A distância entre cada cliente e cada localização candidata de centro de distribuição, que define o custo de transporte.

## 4. Variáveis de Decisão
   - $ \x_i $: Variável binária que indica se um centro de distribuição $ i $ será aberto (1 se aberto, 0 se fechado).
   - $ \y_{ij} $: Quantidade de mercadorias transportadas do centro $ i $ para o cliente $ j $.

## 5. Função Objetivo
Queremos minimizar o custo total, que é a soma dos custos fixos de instalação e dos custos de transporte:

$$
\text{Minimizar} \quad \sum_{i} F_i x_i + \sum_{i}\sum_{j} C_{ij} y_{ij}
$$

Onde:
   - $ F_i $ é o custo fixo de instalar o centro $ i $.
   - $ C_{ij} $ é o custo de transporte entre o centro $ i $ e o cliente $ j $, baseado na distância.

## 6. Restrições
1. **Cobertura de demanda**: Toda a demanda dos clientes deve ser atendida:

$$
\sum_{i} y_{ij} \geq D_j \quad \forall j
$$

Onde $ D_j $ é a demanda do cliente $ j $.

2. **Capacidade dos centros**: A quantidade total de mercadorias enviada de um centro $ i $ para todos os clientes $ j $ não pode exceder a capacidade $ K_i $ do centro $ i $:

$$
\sum_{j} y_{ij} \leq K_i x_i \quad \forall i
$$

3. **Variáveis binárias**: $ x_i $ deve ser 0 ou 1, indicando se um centro é aberto ou não.

## 7. Ferramentas e Solução
Este problema pode ser resolvido usando diferentes ferramentas de otimização, como **PuLP** ou **OR-Tools** em Python, que permitem formular e resolver problemas de programação linear inteira.

## 8. Exemplo Concreto
A empresa deseja abrir um número mínimo de centros de distribuição para cobrir a demanda total de 20 clientes. Com as capacidades ajustadas para cada localização, vamos usar a otimização para escolher quais centros abrir e como alocar a demanda dos clientes entre eles, minimizando o custo total.
