# 🧱 Projeto de Implantação: EcoBrick Solutions
**Documento de Planejamento de Automação e Infraestrutura**

---

## 1. Estudo de Caso: A Revolução da EcoBrick Solutions

A **EcoBrick Solutions** é uma indústria focada na fabricação de tijolos solo-cimento (ecológicos). O objetivo central da empresa é aliar alta produtividade industrial com o menor impacto ambiental possível.

###  Por que o Tijolo Ecológico?
Diferente da cerâmica tradicional, o tijolo ecológico não passa pelo processo de queima. Ele é curado hidraulicamente, o que elimina a emissão de gases do efeito estufa e o consumo de biomassa (lenha).

### Benefícios e Vantagens
* **Sustentabilidade:** Redução drástica na pegada de carbono ($CO_2$).
* **Isolamento:** Excelente desempenho térmico e acústico devido ao design modular.
* **Redução de Custos na Obra:** Economia de até 30% no custo final da construção devido ao sistema de encaixe que dispensa excesso de argamassa.
* **Instalações Facilitadas:** Shafts internos para passagens elétricas e hidráulicas sem quebra-quebra.

### Comparativo de Mercado
| Item | Tijolo Comum | Tijolo Ecológico |
| :--- | :--- | :--- |
| **Queima em Forno** | Sim | Não |
| **Resíduos na Obra** | Alto | Mínimo |
| **Custo do Milheiro** | R$ 800 - R$ 1.100 | R$ 1.200 - R$ 1.800 |
| **Economia Final (Obra)** | 0% | ~25% |

---

##  2. Levantamento Técnico de Infraestrutura

Para garantir a padronização granulométrica e a pressão exata na prensa, a planta exige uma rede de automação robusta.



### 2.1 Equipamentos de Automação e Comunicação

| Categoria | Equipamento | Função | Qtd |
| :--- | :--- | :--- | :--- |
| **Controladores** | CLP Industrial (Ex: S7-1200) | Cérebro da operação (Prensa e Esteira). | 02 |
| **Interface** | IHM 7" Touchscreen | Operação e monitoramento de alarmes. | 02 |
| **Rede** | Switch Industrial Gerenciável | Segmentação de tráfego de dados (VLANs). | 03 |
| **Sensores** | Sensores de Umidade/Pressão | Monitoramento da mistura em tempo real. | 10 |
| **Acionamento** | Inversores de Frequência | Controle suave dos motores de transporte. | 05 |
| **Caberamento** | Cabos Cat6A Blindados (STP) | Comunicação Ethernet Industrial. | 500m |
| **Servidor** | PC Industrial / SCADA | Supervisório e histórico de produção. | 01 |

---

##  3. Plano Orçamentário Estimado

O orçamento abaixo contempla equipamentos de nível industrial para garantir alta disponibilidade (uptime) e baixa manutenção.

> [!IMPORTANT]
> Os valores são referenciais baseados em preços médios de mercado para o ano de 2026.

| Descrição do Item | Valor Estimado (R$) |
| :--- | :--- |
| **Hardware de Automação e Sensores** | R$ 45.000,00 |
| **Infraestrutura de Rede e Cabeamento** | R$ 18.000,00 |
| **Licenciamento de Software (SCADA)** | R$ 12.000,00 |
| **Serviços de Engenharia e Configuração** | R$ 25.000,00 |
| **TOTAL DO INVESTIMENTO** | **R$ 100.000,00** |

---
# 🛒 Plano de Aquisição e Análise de Escalabilidade

---

## 📦 1. Detalhamento de Dispositivos e Conectividade (BOM)

Os equipamentos foram escolhidos pela sua alta confiabilidade em ambientes com partículas suspensas e calor. Abaixo, o mapeamento de onde cada item será instalado e como será interconectado.

| Item | Dispositivo | Onde conectar? (Interface) | Link de Referência | Valor Est. |
| :--- | :--- | :--- | :--- | :--- |
| **CLP** | Siemens S7-1200 | Central do Painel. Recebe os cabos dos sensores e envia comandos aos inversores via PROFINET. | [Loja Siemens](https://mall.industry.siemens.com/) | R$ 4.800 |
| **IHM** | Simatic KTP700 | Porta do Painel. Conectada ao Switch via cabo Ethernet para controle visual do operador. | [Loja Siemens](https://mall.industry.siemens.com/) | R$ 3.500 |
| **Switch** | Stratix 2000 | Trilho DIN no painel. Ponto central onde "nascem" os cabos para CLP, IHM e Servidor. | [Rockwell Automation](https://www.rockwellautomation.com/) | R$ 2.200 |
| **Inversor** | WEG CFW500 | Painel de Potência. Conectado ao motor da prensa e ao CLP para controle de velocidade. | [WEG Online](https://www.weg.net/institutional/BR/pt/) | R$ 2.100 |
| **Cabo** | Furukawa Cat6A | Interliga fisicamente o Switch a todos os dispositivos IP da rede industrial. | [Furukawa Solutions](https://www.furukawasolutions.com/) | R$ 12,00/m |

---

## 🔌 Guia de Conexão Física (Como conectar)

Abaixo descrevemos o fluxo de sinais para a montagem da infraestrutura:

### 1. Rede de Dados (Comunicação)
* **Topologia:** Conecte todos os cabos **RJ45 (Cat6A)** no **Switch Industrial**.
* **Nós de Rede:**
    * Porta 1 -> CLP (Comando)
    * Porta 2 -> IHM (Interface)
    * Porta 3 -> Servidor SCADA (Escritório via Fibra/Conversor)
    * Portas 4 e 5 -> Inversores de Frequência (via Modbus TCP ou Profinet)



### 2. Sinais de Campo (Sensores e Atuadores)
* **Entradas Digitais (DI):** Conecte os botões de emergência e sensores de fim de curso diretamente nas entradas do **CLP**.
* **Entradas Analógicas (AI):** Conecte os sensores de umidade (sinal 4-20mA) para que o CLP saiba o momento exato de adicionar água à mistura de solo-cimento.
* **Saídas (DO):** O CLP aciona as bobinas das válvulas hidráulicas da prensa.

### 3. Potência (Motores)
* **Saída do Inversor:** O cabo de potência deve sair do **Inversor WEG** diretamente para o motor da prensa hidráulica. 
* **Blindagem:** É mandatório aterrar a blindagem do cabo do motor em ambas as extremidades para evitar que o ruído do motor "trave" a rede de dados.

---

## 🛠️ Esquema de Montagem no Painel
> **Dica de Ouro:** Mantenha os cabos de dados (Ethernet) a pelo menos 10cm de distância dos cabos de potência (380V) dentro das canaletas. Se precisarem se cruzar, faça-o em um ângulo de 90° para minimizar a interferência.


---

## 🚀 2. Escalabilidade e Visão de Futuro

O projeto foi concebido para que a **EcoBrick Solutions** possa crescer sem a necessidade de substituir a infraestrutura central.

### 📈 Capacidade de Expansão
* **Hardware Modular:** O CLP Siemens S7-1200 permite a adição de módulos de expansão (Signal Boards) para novas prensas ou braços robóticos de paletização.
* **Rede Sobressalente:** Os switches foram dimensionados com 30% de portas livres para inclusão de novos nós (sensores IoT ou câmeras).
* **Software:** A licença SCADA escolhida suporta a adição de novos "tags" (variáveis) conforme a planta se expandir.

### 🏢 Integração Corporativa (TI/TA)
Para alinhar a produção ao escritório (Indústria 4.0), a solução prevê:
1. **OPC UA:** O CLP comunica-se via protocolo OPC UA, facilitando a leitura de dados diretamente por sistemas ERP (como SAP ou Totvs).
2. **Dashboard de Produção:** Integração com Power BI para que a diretoria visualize o custo por tijolo e o consumo de energia em tempo real.
3. **Manutenção Preditiva:** Sensores prontos para enviar dados de vibração dos motores para nuvem (Cloud Computing).

---

## 🛠️ 3. Adequação ao Ambiente Industrial
O ambiente de produção de tijolos é agressivo. Por isso, adotamos as seguintes premissas:

* **Grau de Proteção:** Painéis com certificação **IP65** (proteção total contra poeira e jatos de água).
* **Cabos Blindados:** Essenciais para neutralizar o ruído eletromagnético dos inversores de frequência que controlam os motores das prensas.
* **Temperatura:** Equipamentos certificados para operar em faixas de 0°C a 60°C, garantindo estabilidade mesmo em dias de calor intenso no galpão.

---

## 🏁 4. Cronograma Final de Go-Live



| Etapa | Responsável | Status |
| :--- | :--- | :--- |
| Aprovação de Orçamento | Gerência Financeira | 🟢 Concluído |
| Compra de Equipamentos | Compras / Suprimentos | 🟡 Em Andamento |
| Instalação de Infraestrutura | Equipe de Elétrica | ⚪ Aguardando |
| Programação e Testes | Engenharia de Automação | ⚪ Aguardando |
| **Treinamento Operacional** | RH / Operações | ⚪ Aguardando |

---
*Documento revisado em: Fevereiro de 2026*


SUBIR COMITT 3

# 📊 Relatório de Viabilidade Técnica e Econômica (VTE)

Este documento analisa o equilíbrio entre o investimento em automação (CAPEX) e os ganhos operacionais esperados (OPEX) para a unidade de tijolos ecológicos.

---

## 1. Análise de Custo-Benefício
O investimento de **R$ 100.000,00** não deve ser visto apenas como despesa, mas como uma transição de uma produção artesanal para uma **indústria de precisão**.

* **Redução de Desperdício:** Sensores de umidade e dosagem automatizada reduzem em **15%** a perda de cimento por traço incorreto.
* **Aumento de Produtividade:** A automação das esteiras e da prensa hidráulica permite um ciclo de produção constante, elevando a saída de 800 para **1.200 tijolos/hora**.
* **Qualidade Assegurada:** Menor índice de quebras pós-cura, resultando em menos devoluções e maior valor agregado ao produto final.

---

## 2. Estimativa de Retorno do Investimento (ROI)

Considerando a operação em dois turnos e a margem de lucro média por milheiro:

| Métrica | Valor Estimado |
| :--- | :--- |
| Ganho mensal por eficiência (matéria-prima) | R$ 4.500,00 |
| Ganho mensal por aumento de produtividade | R$ 8.000,00 |
| Redução mensal em manutenção reativa | R$ 1.500,00 |
| **Economia Total Mensal Estimada** | **R$ 14.000,00** |

> **Payback Estimado:** O investimento se paga em aproximadamente **7 a 8 meses** após o Go-Live.



---

## 3. Matriz de Riscos e Dependência de Fornecedores

| Risco | Impacto | Mitigação |
| :--- | :--- | :--- |
| **Obsolescência** | Médio | Uso de CLPs Siemens (S7-1200) com ciclo de vida longo e suporte global. |
| **Dependência Técnica** | Alto | Escolha de protocolos abertos (PROFINET) para não ficar "preso" a um único fabricante. |
| **Ambiente Agressivo** | Alto | Uso de painéis IP65 e cabos blindados contra poeira e vibração. |
| **Flutuação de Preços** | Baixo | Aquisição de insumos de fornecedores nacionais (WEG/Furukawa) para evitar câmbio. |

---

## 4. Possibilidade de Expansão Futura (Escalabilidade)
A infraestrutura foi projetada sob o conceito de **Modularidade Industrial**:
1.  **Horizontal:** O Switch e o CLP possuem slots para dobrar a capacidade de sensores se uma segunda linha de prensa for instalada.
2.  **Vertical:** A rede Ethernet Industrial instalada suporta a migração imediata para um sistema **MES (Manufacturing Execution System)** no futuro.

---

## 💡 Conclusão: Benefícios Estratégicos para o Negócio

A implementação da rede e automação posiciona a **EcoBrick Solutions** como líder tecnológica no setor de construção sustentável:

* **Dados para Decisão:** Relatórios gerados pelo SCADA permitem identificar gargalos em tempo real.
* **Padronização:** Todo tijolo produzido terá a mesma resistência mecânica, permitindo a obtenção de selos de qualidade (ABNT).
* **Sustentabilidade Real:** Monitoramento do consumo de energia e água, reforçando o DNA "Ecológico" da marca.

---


# 🗺️ Arquitetura da Solução Proposta

Abaixo, apresentamos a visualização estrutural da rede industrial e corporativa da **EcoBrick Solutions**.

---

## 5. Diagrama da Arquitetura de Rede

Este diagrama representa a hierarquia da planta, desde o sensoriamento de campo até o banco de dados corporativo.

### 📊 Representação Visual (Mermaid)

```mermaid
graph TD
    %% Nível Corporativo
    CORP[REDE CORPORATIVA] --> FW[Firewall / Roteador]
    
    %% Nível de Rede
    FW --> VLAN{REDE INDUSTRIAL - VLAN}
    
    %% Nível de Distribuição
    VLAN --> SW[Switch Industrial Gerenciável]
    
    %% Conexões do Switch
    SW --> CLP1[CLP 1 - Prensa 1]
    SW --> CLP2[CLP 2 - Prensa 2]
    SW --> IHM[IHM - Operação]
    SW --> SCADA[Servidor SCADA - Supervisório]
    
    %% Dispositivos de Campo Prensa 1
    subgraph Campo_Prensa_1 [Dispositivos Prensa 1]
        CLP1 --> S1[Sensores: Pressão/Umidade]
        CLP1 --> A1[Atuadores: Válvulas/Motores]
        CLP1 --> INV1[Inversor de Frequência]
    end
    
    %% Dispositivos de Campo Prensa 2
    subgraph Campo_Prensa_2 [Dispositivos Prensa 2]
        CLP2 --> S2[Sensores: Pressão/Umidade]
        CLP2 --> A2[Atuadores: Válvulas/Motores]
    end
    
    %% Gestão de Dados
    SCADA --> BD[(Banco de Dados / Histórico)]
    
    %% Expansão
    SW -.-> EXP[PORTAS LIVRES: Expansão Futura]
    
    %% Estilização
    style VLAN fill:#f9f,stroke:#333,stroke-width:2px
    style SW fill:#bbf,stroke:#333,stroke-width:2px
    style EXP stroke-dasharray: 5 5