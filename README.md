# Azure Cloud - Guia Prático e Anotações

## 📚 Introdução

Este repositório contém minhas anotações e aprendizados sobre a Microsoft Azure, focando principalmente na criação e gerenciamento de máquinas virtuais. As informações aqui documentadas servem como referência pessoal e recurso para estudos futuros.

## 🔧 Criando uma Máquina Virtual no Azure

### Passo a passo resumido

1. **Acesso ao Portal**: Entre no [portal do Azure](https://portal.azure.com)
2. **Localizar o serviço**:
   - Digite "máquinas virtuais" na pesquisa
   - Selecione "Máquinas virtuais" em Serviços
3. **Criar a VM**:
   - Clique em "Criar" e selecione "Máquina virtual do Azure"
   - Preencha o nome da VM (ex: myVM)
   - Escolha a imagem (ex: Windows Server 2022 Datacenter)
4. **Configurações de Acesso**:
   - Configure um nome de usuário administrador (ex: azureuser)
   - Defina uma senha forte (mínimo 12 caracteres)
5. **Configuração de Rede**:
   - Em "Regras de porta de entrada", selecione "Permitir portas selecionadas"
   - Selecione as portas necessárias (RDP-3389 para acesso remoto, HTTP-80 para web)
6. **Revisão e Criação**:
   - Revise as configurações
   - Clique em "Criar"

### Conectando-se à VM

1. Após a criação, vá para o recurso da VM
2. Selecione "Conectar > RDP"
3. Baixe o arquivo RDP
4. Abra o arquivo e conecte-se usando as credenciais:
   - Usuário: `localhost\nome_do_usuario` (ex: localhost\azureuser)
   - Senha: a que você definiu na criação

### Instalando o Servidor Web (IIS)

```powershell
# Execute este comando no PowerShell da VM
Install-WindowsFeature -name Web-Server -IncludeManagementTools
```

## 💡 Dicas e Boas Práticas

### Gestão de Custos

- **Desligamento Automático**: Configure para que a VM desligue automaticamente em horários sem uso
  1. Na seção "Operações" da VM, selecione "Desligamento automático"
  2. Ative a opção e defina um horário adequado
  3. Salve a configuração

- **Limpeza de Recursos**: Quando não precisar mais dos recursos
  1. Acesse o Grupo de Recursos associado à VM
  2. Selecione "Excluir grupo de recursos"
  3. Confirme a exclusão digitando o nome do grupo

- **Monitoramento de Custos**: Utilize as ferramentas de Gerenciamento de Custos do Azure
  1. Acesse "Gerenciamento de Custos + Cobrança" no portal Azure
  2. Utilize "Análise de Custo" para visualizar gastos por serviço, região ou recurso
  3. Configure orçamentos e alertas para ser notificado sobre anomalias de gastos
  4. Revise regularmente as recomendações do Assistente para otimização de custos

- **Otimização de Recursos**:
  1. Redimensione VMs subutilizadas (CPU < 5% e tráfego de rede < 7MB por 4+ dias)
  2. Utilize Instâncias Reservadas para cargas de trabalho estáveis e previsíveis
  3. Aproveite o Benefício Híbrido do Azure para licenças existentes
  4. Considere o Plano de Economia do Azure para compromissos de longo prazo

### Segurança

- **Restrição de Portas**: Apenas abra as portas estritamente necessárias
- **Senhas Fortes**: Use senhas complexas (12+ caracteres, combinando maiúsculas, minúsculas, números e símbolos)
- **Atualizações**: Mantenha o sistema operacional da VM sempre atualizado
- **NSG (Network Security Group)**: Configure regras de segurança de rede específicas

### Desempenho

- Escolha o tamanho da VM adequado às suas necessidades (memória, CPU, disco)
- Utilize discos SSD para melhor desempenho em cargas de trabalho que exigem alta E/S
- Configure o armazenamento em camadas para dados acessados com menos frequência

## 🌐 Conceitos Importantes do Azure

### Regiões e Zonas de Disponibilidade

- **Regiões**: Áreas geográficas que contêm datacenters
- **Zonas de Disponibilidade**: Locais fisicamente separados dentro de uma região
- **Pares de Regiões**: Regiões emparelhadas para recuperação de desastres

### Modelo de Responsabilidade Compartilhada

- A Microsoft é responsável pela infraestrutura física, rede e hospedagem
- O cliente é responsável pelos dados, identidades, aplicativos e configurações

### Resource Manager e Grupos de Recursos

- **Azure Resource Manager (ARM)**: Camada de gerenciamento para criação, atualização e exclusão de recursos
- **Grupos de Recursos**: Contêineres lógicos para recursos relacionados
- **Tags**: Úteis para organização, governança e rastreamento de custos

## 🚀 Principais Serviços do Azure

### Computação

- **Máquinas Virtuais**: Infraestrutura como serviço (IaaS) para controle total sobre o ambiente
- **Azure App Service**: Plataforma como serviço (PaaS) para hospedar aplicativos web e APIs
- **Azure Kubernetes Service**: Orquestração de contêineres gerenciada
- **Azure Functions**: Computação sem servidor para execução de código orientado a eventos
- **Azure Container Instances**: Executar contêineres sob demanda sem gerenciar servidores

### Armazenamento

- **Azure Blob Storage**: Armazenamento de objetos para dados não estruturados
- **Azure Files**: Compartilhamentos de arquivos totalmente gerenciados na nuvem
- **Azure Table Storage**: Armazenamento de chave-valor NoSQL para dados semiestruturados
- **Azure Queue Storage**: Armazenamento de mensagens para comunicação confiável entre componentes

### Bancos de Dados

- **Azure SQL Database**: Banco de dados relacional totalmente gerenciado
- **Azure Cosmos DB**: Banco de dados multimodelo distribuído globalmente
- **Azure Database for MySQL/PostgreSQL**: Versões gerenciadas de bancos de dados open source
- **Azure Cache for Redis**: Cache na memória para melhorar o desempenho de aplicativos

### Rede

- **Azure Virtual Network**: Redes privadas isoladas na nuvem
- **Azure Load Balancer**: Distribui tráfego para aumentar disponibilidade
- **Azure Application Gateway**: Balanceador de carga para aplicativos web
- **Azure CDN**: Rede de distribuição de conteúdo para entrega global de conteúdo
- **Azure DDoS Protection**: Proteção contra ataques de negação de serviço

### IA e Machine Learning

- **Azure AI Services**: APIs pré-construídas para capacidades de IA
- **Azure Machine Learning**: Plataforma para desenvolvimento de modelos de ML
- **Azure OpenAI Service**: Modelos de IA generativa para aplicativos inteligentes

### DevOps e Monitoramento

- **Azure DevOps**: Conjunto de ferramentas para desenvolvimento colaborativo
- **GitHub Actions**: Automação de CI/CD integrada ao GitHub
- **Azure Monitor**: Coleta, análise e resposta a dados de telemetria
- **Application Insights**: Monitoramento e diagnóstico de aplicativos

## 🔐 Certificações e Segurança no Azure

### Principais Certificações

- **Nível Fundamental**: 
  - AZ-900 (Azure Fundamentals): Conhecimentos básicos sobre conceitos de nuvem e serviços Azure
  - SC-900 (Security, Compliance, and Identity Fundamentals): Fundamentos de segurança e conformidade

- **Nível Associado (Intermediário)**:
  - AZ-104 (Azure Administrator): Implementação, gerenciamento e monitoramento do ambiente Azure
  - AZ-204 (Azure Developer): Desenvolvimento de soluções usando serviços Azure
  - AZ-500 (Azure Security Engineer): Implementação de controles de segurança e manutenção da postura de segurança

- **Nível Expert**:
  - AZ-305 (Azure Solutions Architect): Design de soluções de infraestrutura completas

### Conformidade e Segurança

O Azure oferece mais de 100 certificações de conformidade, incluindo:
- ISO 27001, 27018
- SOC 1, 2, 3
- PCI DSS
- HIPAA/HITECH
- GDPR
- FedRAMP

Para implementar segurança, utilize:
- Azure Security Center: Gerenciamento unificado de segurança
- Azure Policy: Definição e imposição de políticas de governança
- Blueprints de Segurança: Ambientes pré-configurados para conformidade regulatória

## 📝 Anotações Pessoais e Observações

- O tempo de provisionamento de uma VM varia conforme a imagem e região escolhidas
- Para ambientes de produção, considere redundância com zonas de disponibilidade
- O UTC (Tempo Universal Coordenado) é o padrão para fusos horários - lembre-se de configurar o correto para sua região
- Para cargas de trabalho específicas, consulte as VMs otimizadas (computação, memória, armazenamento)
- Para desenvolvimento/teste, considere "Dev/Test" para preços reduzidos

## 🚀 Próximos Passos e Recursos

- [Documentação oficial da Azure](https://docs.microsoft.com/pt-br/azure/)
- [Treinamentos gratuitos no Microsoft Learn](https://docs.microsoft.com/pt-br/learn/azure/)
- [Azure Architecture Center](https://docs.microsoft.com/pt-br/azure/architecture/)
- [Calculadora de Preços](https://azure.microsoft.com/pt-br/pricing/calculator/)

---

*Este guia é baseado em experiências pessoais e na documentação oficial da Microsoft. As recomendações e procedimentos podem variar conforme atualizações da plataforma.*

*Última atualização: Maio/2025*
