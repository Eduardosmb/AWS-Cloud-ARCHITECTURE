# AWS-Cloud-ARCHITECTURE

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


