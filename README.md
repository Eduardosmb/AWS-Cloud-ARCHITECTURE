# AWS-Cloud-ARCHITECTURE

# Diagrama da Arquitetura

![Diagrama](diagrama.png)




# Jump Server

## 🎯 Visão Geral
O Jump Server atua como ponto único e seguro de entrada para acessar as outras instâncias do ambiente (backend e database). Funciona como uma ponte de acesso que:
- Centraliza e protege o acesso às instâncias
- Previne conexões diretas aos servidores críticos
- Registra todas as tentativas de acesso
- Aumenta a segurança do ambiente
  
## 📋 Recursos Implementados

### 🔐 Autenticação de Dois Fatores (2FA)
Sistema de autenticação dupla implementado com Google Authenticator. Ao realizar a conexão SSH são solicitados:
- Código de verificação do Google Authenticator
- Senha do grupo de acesso

### 👥 Restrições de Acesso
Controle de acesso através de grupos específicos:
- jumpserver-admins: Acesso administrativo
- jumpserver-users: Acesso padrão

### 📝 Logs e Auditoria
Sistema de monitoramento completo com:
- Registros detalhados de autenticação
- Sistema de auditoria
- Rotação automática de logs

### 🛡️ Segurança Adicional
- Firewall configurado (UFW)
- Restrições SSH
- Monitoramento de tentativas de acesso

## 📊 Relatório de Evidências

O sistema gera automaticamente relatórios de evidências no arquivo `evidencias.txt`, contendo todos os detalhes de configuração e logs do sistema, incluindo:
- Status dos serviços
- Grupos e permissões configuradas
- Registros de acesso
- Configurações de segurança ativas

O relatório de evidências pode ser acessado através dos seguintes comandos:

```bash
# Visualização completa do relatório
cat evidencias.txt
```
> **Nota**: O relatório é atualizado automaticamente para refletir o estado atual do sistema.


## Monitoramento com Zabbix

## 🎯 Visão Geral
Solução de monitoramento centralizado que fornece visibilidade em tempo real da infraestrutura. Monitora métricas críticas dos servidores através de agentes instalados nas instâncias.

## 📋 Arquitetura
- Zabbix Server centralizado (instância pública)
- Agentes instalados nas instâncias:
 - Backend (público)
 - Database (privado)

## 🛡️ Segurança Implementada
### Regras de Firewall
- Comunicação restrita entre Zabbix Server e agentes
- Portas específicas para monitoramento (10050)
- Acesso controlado por IP de origem

## 📊 Monitoramento
### Métricas Coletadas
- Performance do sistema
- Utilização de recursos
- Estado dos serviços
- Logs do sistema

### Grupos de Monitoramento
- Linux Servers: Métricas base do sistema
- Databases: Métricas específicas de banco

## 🔄 Alta Disponibilidade
- Inicialização automática dos agentes
- Recuperação pós-reinicialização
- Persistência das configurações

> **Nota**: Sistema configurado para monitoramento passivo, onde o Zabbix Server inicia as conexões com os agentes.


