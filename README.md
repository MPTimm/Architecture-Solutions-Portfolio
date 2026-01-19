# Architecture-Solutions-Portfolio

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

    style Data_Center_Local fill:#f9f,stroke:#333,stroke-width:2px
    style Cloud fill:#bbf,stroke:#333,stroke-width:2px
