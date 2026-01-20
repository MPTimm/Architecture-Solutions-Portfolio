## Visão Geral

### Objetivo da Solução

Prover uma estratégia de 3-2-1 de Backup (3 cópias, 2 mídias, 1 fora do site) utilizando a nuvem como repositório externo e site de contingência.

### Justificativa dos Componentes

Object Storage: Escolhido pela alta durabilidade ($99.999999999\%$) e custo reduzido em comparação ao storage físico.
    
VPN/Link: Garante que o tráfego de dados sensíveis do banco de dados não transite de forma exposta na internet pública.
    
Instâncias de Recuperação: Estão configuradas mas desligadas (modelo On-Demand), gerando custo apenas em caso de testes ou desastres reais.

### Benefício Financeiro

Redução de CAPEX (compra de fitas e drives físicos) para um modelo de OPEX (pague pelo que armazenar), facilitando a expansão conforme o volume de dados do cliente cresce.

Diagrama:

```mermaid
graph LR
    subgraph Data_Center_Local [Data Center On-Premise]
        App[Aplicação Legada] --> DB[(Banco de Dados SQL)]
        DB --> BKP[Agente de Backup Local]
    end
 subgraph Conectividade
        BKP -- "VPN / Link Dedicado" --> Cloud
    end

subgraph Cloud [Provedor de Nuvem]
        Cloud_Store[(Object Storage)]
        Compute[Instâncias de Recuperação]
    end

style Data_Center_Local fill:#07b570,stroke:#333,stroke-width:2px
style Cloud fill:#bbf,stroke:#333,stroke-width:2px, color: black

