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