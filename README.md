# Oracle Session Management Scripts

Este repositório contém scripts SQL criados pela equipe de TI onde trabalho, com o objetivo de **identificar e encerrar sessões que geram bloqueios (locks)** em bancos de dados Oracle, especialmente em ambientes com múltiplas instâncias (RAC).

Estou disponibilizando este material com o intuito de compartilhar conhecimento e ajudar outros profissionais que enfrentam situações similares.

## 📌 Objetivo

- Identificar sessões que estão bloqueadas e quais sessões estão causando o bloqueio;
- Identificar objetos que estão travados;
- Gerar comandos automáticos para matar sessões específicas com base em seus identificadores;
- Ajudar na administração e no diagnóstico de problemas relacionados a concorrência e travamentos no banco.

---

## 📂 Conteúdo do Repositório

### 🔍 Identificação de Locks

Script para identificar sessões bloqueadas e bloqueadoras, com informações como:

- SID, SERIAL#, instância, usuário, tempo de execução, evento de espera;
- Comando `ALTER SYSTEM KILL SESSION` pronto para execução;
- Nome do objeto que está sendo travado.

> Arquivo: `identificar_locks.sql`

---

### ❌ Geração de comandos para matar sessões com locks

Script que gera automaticamente os comandos para encerrar sessões com objetos travados, incluindo:

- Nome do objeto travado;
- Informações da sessão (SID, SERIAL, INST_ID);
- Informações do processo (SPID), SQL atual e dados do usuário.

> Arquivo: `matar_sessoes_com_locks.sql`

---

## ⚠️ Avisos Importantes

- Execute os scripts sempre com **cautela**;
- Recomenda-se testar previamente em ambiente de homologação;
- Necessário ter privilégios adequados (como `ALTER SYSTEM`);
- Encerrar sessões incorretamente pode impactar usuários ou processos críticos.

---

## 🚀 Como usar

### Rodar a identificação de locks:

```sql
@identificar_locks.sql
