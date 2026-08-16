

# 📑 Acordo de Teste de Penetração (Pentesting Agreement)

<p align="center">
  <img src="https://img.shields.io/badge/AUTOR-PAULO%20JUNIOR-blue?style=for-the-badge&logo=github" alt="Autor">
  <img src="https://img.shields.io/badge/Ambiente-Segurança%20Ofensiva-red?style=for-the-badge&logo=kalilinux" alt="Segurança Ofensiva">
  <img src="https://img.shields.io/badge/Documento-Contrato%20Técnico-blue?style=for-the-badge&logo=readme" alt="Contrato Técnico">
  <img src="https://img.shields.io/badge/Status-Homologado-success?style=for-the-badge" alt="Status">
</p>

---

## 🎯 Objetivos do Laboratório
Este repositório documenta a criação e estruturação de um **Acordo de Teste de Penetração** (contrato legalmente vinculante). O documento estabelece os parâmetros, responsabilidades, limites legais e termos financeiros para a execução de uma auditoria de segurança ofensiva simulada.

---

## 🤝 Acordo de Teste de Penetração

### 🏢 Partes do Contrato



**[CONTRATANTE]**
- **Razão Social:** [RAZÃO_SOCIAL_DO_CLIENTE]
- **CNPJ:** [CNPJ_DO_CLIENTE]
- **Sede:** [ENDEREÇO_COMPLETO_DO_CLIENTE]
- **Representante Jurídico:** [NOME_DO_RESPONSÁVEL_TÉCNICO] - [CARGO]

**[CONTRATADO]**
- **Nome/Empresa:** [NOME_DA_SUA_EMPRESA_OU_SEU_NOME]
- **CNPJ/CPF:** [SEU_CNPJ_OU_CPF]
- **Sede:** [SEU_ENDEREÇO_PROFISSIONAL]


---

### 🎯  Escopo do Trabalho e Responsabilidades

<details>
<summary><b>🛡️ Obrigações do CONTRATADO (Testador de Penetração)</b></summary>

1. **Restrição de Escopo:** Realizar testes de intrusão exclusivamente nos ativos autorizados por escrito (ex: IPs `192.168.1.0/24` e subdomínio `*.cliente.com.br`).
  
2. **Metodologia Profissional:** Utilizar apenas metodologias de mercado reconhecidas, como OWASP, OSSTMM e PTES.
   
3. **Alerta de Risco Crítico:** Interromper imediatamente qualquer teste e notificar o cliente caso identifique uma vulnerabilidade crítica que ameace a estabilidade do ambiente (ex: RCE ou vazamento de dados ativo).
   
4. **Entregáveis:** Fornecer um relatório técnico detalhado e um sumário executivo contendo as falhas encontradas, o nível de risco (CVSS) e os planos de remediação recomendados.
   
5. **Sigilo de Dados:** Manter sigilo absoluto sobre toda e qualquer informação obtida durante a execução do serviço.
</details>

<details>
<summary><b>💼 Obrigações da CONTRATANTE (Cliente)</b></summary>

1. **Consentimento Formal:** Fornecer autorização formal por escrito (Carta de Autorização) assinada pela diretoria antes do início dos testes.
   
2. **Legitimidade dos Ativos:** Garantir que possui os direitos legais sobre toda a infraestrutura, redes e aplicações que serão testadas.
   
3. **Alinhamento Interno:** Notificar sua equipe interna de TI/SOC sobre o período dos testes para evitar o bloqueio acidental das ferramentas do testador, ou definir o teste como "Black Box" às cegas, assumindo os riscos de alertas gerados.
   
4. **Plano de Contingência:** Manter backups atualizados e funcionais de todos os sistemas que estarão no escopo do teste.
   
5. **Canal de Emergência:** Responder prontamente aos canais de comunicação de emergência caso o testador precise relatar um incidente crítico.
    
</details>

---

### 📅  Cronograma de Execução

| Fase | Descrição Técnica | Período Estimado |
| :--- | :--- | :--- |
| **Fase 1** | **Alinhamento e Reconhecimento:** Reunião de Kick-off, assinatura do NDA e coleta de informações passivas. | Dias 1 a 2 |
| **Fase 2** | **Varredura e Análise:** Mapeamento de portas, serviços e descoberta de vulnerabilidades. | Dias 3 a 5 |
| **Fase 3** | **Exploração e Pós-Exploração:** Tentativas de intrusão controlada e movimentação lateral (Horário comercial: 09h às 18h). | Dias 6 a 10 |
| **Fase 4** | **Relatório e Entrega:** Consolidação técnica dos resultados encontrados e envio do relatório final. | Dias 11 a 13 |
| **Fase 5** | **Re-teste:** Validação das correções aplicadas pelo cliente (limite de 1 dia de teste). | Até 30 dias pós-entrega |

---

### 💳  Taxas, Faturamento e Detalhes de Pagamento

* 💰 **Valor Total do Projeto:** R$ 15.000,00 (Quinze mil reais).
  
* 📑 **Condições de Faturamento:** 50% de sinal pago no ato da assinatura deste instrumento e 50% pagos em até 5 dias úteis após a entrega e apresentação do Relatório Final.
  
* ⚠️ **Custos Extras:** Quaisquer licenças de softwares específicos solicitados pelo cliente ou despesas de deslocamento físico (caso o pentest exija presença local) serão faturadas à parte, mediante aprovação prévia de orçamento.

---

### ❌  Rescisão Contratual

1. **Mútuo Acordo:** Mediante aviso prévio por escrito de 5 dias de antecedência por qualquer uma das partes.
   
2. **Justa Causa Imediata:** Se o testador atacar ativos fora do escopo homologado ou se o cliente não comprovar a propriedade legal dos sistemas testados.
   
3. **Inadimplemento:** Caso ocorra atraso no pagamento do sinal por mais de 10 dias úteis, suspendendo os testes automaticamente.
   
4. **Multa Rescisória:** Em caso de rescisão imotivada por parte do cliente após o início dos testes, este pagará o valor proporcional às fases já executadas, acrescido de uma multa de 10% sobre o saldo remanescente.

---

## 🚀 Cláusulas Adicionais Recomendadas

Estas cláusulas complementam a segurança jurídica do contrato em cenários reais do mercado de segurança ofensiva:

1. 🔒 **NDA (Non-Disclosure Agreement):** Garante por lei que nenhum dado, código, segredo comercial ou vulnerabilidade do cliente seja exposto ao público ou a concorrentes pelo testador.
   
2. ⚖️ **Indenização e Limitação de Responsabilidade:** Define um teto financeiro máximo que o testador pode responder legalmente caso um teste cause uma queda acidental no sistema do cliente (geralmente limitado ao valor total do contrato).
   
3. 💡 **Cláusula de Propriedade Intelectual:** Define que o relatório final pertence ao cliente, mas as metodologias, ferramentas próprias e scripts customizados criados pelo testador continuam sendo propriedade intelectual do profissional de segurança.
   
4. 🏛️ **Jurisdição / Foro de Eleição:** Define a comarca legal onde qualquer disputa judicial sobre o contrato deverá ser resolvida de maneira formal.

---
⚠️ **Nota de Isenção de Responsabilidade Acadêmica:** *Este documento serve estritamente como entrega laboratorial prática para fins educacionais em cibersegurança, não substituindo a consultoria de um advogado especializado para emissão de contratos comerciais reais.*

