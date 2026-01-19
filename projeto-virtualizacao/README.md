## Visão Geral

### Objetivo da Solução

Flexibilizar a mobilidade de workloads para fins de segurança dos dados.

### Justificativa dos Componentes

Hypervisor: Fundação para gerar instâncias de máquinas virtuais.
    
Servidores físicos: Reaproveitamento de hardware legado com adição de novo equipamento focando em possibilidade de replicação das máquinas virtuais.
    
### Benefício Financeiro

Redução de probabilidade da ocorrência de desastres cujo impacto financeiro pode vir a ser de magnitude imensurável.

Diagrama:

```mermaid
graph LR
    subgraph Infraestrutura_Legada [Infraestrutura Legada]
      Srv1[Server Legado]
    end

    subgraph Infraestrutura_Modernizada [Infraestrutura Modernizada]
        subgraph Hypervisor
            subgraph Cluster
                Srv3[Server Legado] --- Srv2[Server adicional]
            end
        end
      VM1[VM1] e1@ ==> Hypervisor
      VM2[VM2] e2@ ==> Hypervisor
      VM3[VM3] e3@ ==> Hypervisor
      VM4[VM4] e4@ ==> Hypervisor

      e1@{ animate: true }
      e2@{ animate: true }
      e3@{ animate: true }
      e4@{ animate: true }
    end

    Infraestrutura_Legada --> Infraestrutura_Modernizada

style Infraestrutura_Legada fill:#A9A9A9,stroke:#333,stroke-width:2px
style Infraestrutura_Modernizada fill:#FFFAFA,stroke:#333,stroke-width:2px, color: black
style Hypervisor fill:#00FF7F, stroke:#333, stroke-width:2px, color:black
style Cluster fill:#4682B4, stroke:#333, stroke-width:2px, color:white
