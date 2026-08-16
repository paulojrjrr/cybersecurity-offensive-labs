# 🏢 Auditoria de Segurança Corporativa & Planejamento de Escopo


<p align="center">
  <img src="https://img.shields.io/badge/AUTOR-PAULO%20JUNIOR-blue?style=for-the-badge&logo=github" alt="Autor">
  <img src="https://img.shields.io/badge/Fase-Regras%20de%20Engajamento-red?style=for-the-badge&logo=target" alt="Escopo">
  <img src="https://img.shields.io/badge/Ambiente-Datacenter%20%26%20LAN-blue?style=for-the-badge&logo=cisco" alt="Ambiente">
  <img src="https://img.shields.io/badge/Conformidade-GRC%20%2F%20Pentest-orange?style=for-the-badge" alt="Conformidade">
</p>

---

## 🎯 Objetivos do Laboratório

Obtendo acordo sobre as regras de engajamento que se aplicam a um teste de penetração ou auditoria de segurança é o primeiro passo em qualquer engajamento com um cliente. É importante dedicar tempo para assegurar que tanto a sua empresa quanto o cliente tenham uma compreensão clara dos termos e do escopo do engajamento de teste.

* **Escopo Técnico:** Crie um escopo de teste de penetração e um documento de plano que atenda aos requisitos para serviços de teste de penetração que foram coletados do cliente.
  
* **Governança:** Determine os elementos das regras de engajamento.

---

## 🗺️ Cenário & Topologia de Rede

O mapeamento estrutural dos ativos da empresa distribui-se através dos seguintes segmentos lógicos [0.1.1]:

### 🌐 LAN (Rede Corporativa Interna)
* 🔹 Admin
* 🔹 Finanças
* 🔹 Tecnologia da Informação
* 🔹 Armazém
* 🔹 Serviço de Atendimento ao Consumidor
* 🔹 Envio

### 🔒 DMZ (Zona Desmilitarizada)
* 🔹 Servidor Linux (DNS Externo)

### 🗄️ Centro de Dados (Datacenter Houston)
* 🔹 Administrador
* 🔹 Gestão
* 🔹 Suporte da Amazon
* 🔹 Operações
* 🔹 Logística
* 🔹 Servidor SQL


---

## 📊 Tabelas de Endereçamento Oficial

### 🗄️ 1. Centro de Processamento de Dados (Houston)

| Servidores | VLAN | Endereço IP | Sub-redes |
| :--- | :---: | :--- | :--- |
| **Administração** | 2-5 | `172.24.1.0/24` | (4) 255.255.255.192 |
| **Suporte da Amazon** | 10 - 25 | `172.25.0.0/16` | (11) 255.255.252.0 |
| **Operações** | 50 - 55 | `172.26.0.0/21` | (5) 255.255.255.0 |
| **Logística** | 80 – 85 | `172.27.0.0/21` | (5) 255.255.255.0 |
| **Gestão** | 100 - 110 | `172.30.0.0/16` | vários, conforme necessário |

### 🖥️ 2. Rede LAN Corporativa

| Departamento | VLAN | Endereço IP | Máscara de sub-rede |
| :--- | :---: | :--- | :--- |
| **Administração** | 120 | `172.16.1.0` | 255.255.255.0 |
| **Finanças** | 130 | `172.16.4.0` | 255.255.255.0 |
| **Tecnologia da Informação** | 140 | `172.16.8.0` | 255.255.255.0 |
| **Armazém** | 150 | `172.16.12.0` | 255.255.255.0 |
| **Serviço de Atendimento ao Consumidor** | 160 | `172.16.16.0` | 255.255.255.0 |
| **Envio** | 170 | `172.16.20.0` | 255.255.255.0 |

---

## 🎙️ Transcrição da Entrevista Coleta de Requisitos

**CEO:** Bem-vindo ao Nexus Plaza. Convidamos vocês aqui para iniciar nosso compromisso e discutir o que estamos esperando desta auditoria de segurança. Estamos ansiosos para garantir que nossa infraestrutura de segurança atenda ou exceda as salvaguardas necessárias. Vou entregar isso ao nosso diretor de TI para descrever nosso ambiente de rede.

**Diretor de TI**: Como você sabe, somos principalmente uma empresa de varejo online. Nossos sites de comércio eletrônico voltados para clientes estão hospedados na Amazon, mas todas as nossas comunicações, armazenamento e envio de serviços de TI são tratadas internamente. Operamos um datacenter local em Houston que suporta nossas instalações de fabricação e armazenamento. Atualmente, há 25 servidores segregados em três clusters: administração, operações e logística. Além disso, operamos um cluster que fornece suporte para nossa vitrine Amazon. O acesso remoto a esses sistemas é através de SSL ou IPsec VPN. Usamos dois ISPs para nos conectar à internet, mas um é usado principalmente para comunicações com a Amazon para suportar pedidos, estoque e contato com o cliente em tempo real.

**CEO**: Um de nossos concorrentes recentemente foi atingido por um ataque de ransomware que teve como alvo seu sistema de estoque de produção. Eles perderam um número significativo de pedidos de clientes por não conseguirem separar e enviar o estoque em tempo hábil. Estamos preocupados que nosso sistema de armazém e envio possa ter vulnerabilidades que poderiam nos paralisar da mesma forma se uma brecha ocorrer. Quando você depende da entrega rápida aos clientes, qualquer atraso é um desastre.

**Diretor de TI**: Os sistemas que suportam nosso armazenamento e envio estão localizados em dois clusters no datacenter: operações e logística. O acesso interno a esses sistemas é restrito aos funcionários da administração do armazém, ao pessoal de TI e aos funcionários de controle do estoque. Nosso sistema de controle de estoque é suportado por um banco de dados Microsoft SQL Server. Como você pode ver no diagrama, o banco de dados SQL está alojado em uma SAN separada com conexões com os sistemas de armazém e produção. Nosso negócio depende do nosso acesso à Amazon; portanto, nenhum teste deve invadir os clusters do datacenter que contêm os dados de armazenamento da Amazon e o estoque. Eles são identificados no diagrama.

**CEO**: Queremos que teste os controles de segurança para assegurar que um atacante que consiga obter acesso a uma conta de usuário final e computador dentro do armazém não possa obter acesso de administrador a nenhum dos servidores ou acessar o banco de dados de inventário de produção. Também queremos ter certeza de que o software e os sistemas operacionais estão atualizados e não há vulnerabilidades conhecidas presentes em nossos aplicativos.

**Diretor** de TI: forneceremos a você acesso interno através de uma VLAN isolada no departamento de TI a partir do qual você poderá realizar os seus testes. Existe um firewall com IDS integrado separando as redes do datacenter da LAN corporativa, incluindo o departamento de TI. Dentro do datacenter, cada servidor possui um firewall local habilitado. O DNS interno é fornecido através dos serviços do Microsoft Active Directory, e o DNS externo é um servidor Linux localizado em uma DMZ separada. O acesso externo aos clusters de operações e logística é limitado aos funcionários que conectam através de VPN. Nenhum acesso HTTP é permitido nesses clusters. Os servidores nesses dois clusters não têm acesso à Internet, exceto para obter atualizações automáticas do software.

**CEO**: Como os sistemas que queremos que você teste são sistemas de produção, esperamos limitar as interrupções causadas pelos testes ao máximo. Forneceremos a você acesso a um sistema Microsoft SQL Server em desenvolvimento configurado de forma idêntica ao sistema de produção com um espelho do banco de dados.

**Diretor** de TI: Sim, quero reforçar a necessidade de manter as interrupções ao máximo. Forneceremos a você um tempo limite durante nossa janela normal de manutenção agendada para realizar testes de carga e simulações de ataque de negação de serviço. Nossa janela de manutenção agendada está entre 2:00 e 6:00 da manhã de sexta, sábado e domingo. Outros testes não perturbadores podem ser executados durante o horário comercial normal.

**CEO**: Estamos limitando o número de funcionários de TI que estão cientes do teste. Apenas a equipe de TI responsável diretamente pelo monitoramento dos sistemas de operações e logística será notificada sobre quando o teste ocorrerá. Forneceremos uma lista de endereços de e-mail do armazém e da equipe de operações, uma vez que estamos preocupados que a maioria das violações de dados e ataques de ransomware comece com um ataque de engenharia social bem-sucedido. Os usuários finais não estarão cientes de que o teste está ocorrendo. Esperamos que o compromisso comece duas semanas após a assinatura do contrato e da NDA. Esperaremos o relatório final dentro de 60 dias.

Seus contatos principais para esse compromisso são o diretor de TI, o gerente do armazém e o gerente de operações. Agende um relatório de atualização semanal e uma teleconferência para informá-los do progresso dos testes e dos resultados provisórios.




---

# 📝 Planilha de Escopo (Scope Worksheet)

Abaixo estão detalhadas as diretrizes de escopo técnico obtidas a partir da análise dos requisitos do cliente:

### 1. Quais são as maiores preocupações de segurança do cliente?
* 🎯 Os sistemas de estoque e envio podem estar sujeitos a ataques de ransomware, fazendo com que os negócios não consigam cumprir e despachar as ordens dos clientes em tempo hábil.

### 2. Quais clusters de servidores específicos, intervalos de endereços de rede ou aplicativos devem ser testados?
* 🖥️ **Clusters:** Servidores nos clusters de Operação e Logística.
* 🌐 **Intervalos de IP:** Redes `172.26.0.0/21` e `172.27.0.0/21`.
* 💾 **Aplicações:** Serviços e bancos de dados do Microsoft SQL Server.

### 3. Que clusters de servidores específicos, intervalos de endereços de rede ou aplicativos devem ser explicitamente NÃO testados?
* 🚫 Clusters de servidores de Administração.
* 🚫 Infraestrutura de suporte da Amazon.
* 🚫 Intervalos de endereços IP da rede LAN geral.

### 4. O teste será realizado em um ambiente de produção ou em um ambiente de teste?
* ⚙️ A maioria dos testes será realizada diretamente em sistemas de **Produção**.
* 🛠️ Somente os testes considerados intrusivos ou de carga contra o SQL Server serão feitos no ambiente de **Desenvolvimento** (espelho).

### 5. O teste de intrusão incluirá testes de rede internos? Nesse caso, como o acesso será obtido?
* 🔌 **Sim.** O teste incluirá auditoria na rede interna e o acesso técnico será fornecido pela equipe do cliente através de uma **VLAN isolada**.

### 6. Os sistemas cliente/usuário final estão incluídos no escopo? Se sim, quantos clientes poderão ser utilizados?
* ✖️ **Não.** Os sistemas de usuário final (estações de trabalho dos funcionários) estão completamente fora do escopo.

### 7. A engenharia social é permitida? Se sim, é limitado?
* 📧 **Sim.** A engenharia social é permitida, porém está estritamente limitada à utilização de uma lista específica de endereços de e-mail fornecida pela gerência.

### 8. A negação de serviço e outros ataques disruptivos são permitidos? Nesse caso, há limites para quando testes disruptivos podem ser realizados?
* 💥 **Sim.** Ataques disruptivos e testes de estresse são permitidos, desde que realizados estritamente durante o intervalo de tempo agendado nas janelas de manutenção normais da empresa.

### 9. Há dispositivos em vigor que podem impactar os resultados de um teste de penetração? Se sim, quais são eles?
* 🛡️ **Sim.** Existem defesas ativas na rede que podem detectar ou mitigar as atividades, incluindo firewalls de perímetro e sistemas de detecção de intrusão (IDS).

### 10. Testar o acesso sem fio faz parte dessa avaliação?
* 📶 **Não.** A análise de redes sem fio (Wireless) está fora do escopo deste engajamento.

### 11. Os serviços Web estão incluídos no escopo de testes?
* 🌐 **Não.** Serviços e aplicações Web externas não fazem parte dos alvos homologados.

### 12. Os funcionários estão cientes do teste e do tempo durante o qual isso ocorrerá?
* 🤫 **Não.** Apenas os gerentes selecionados e a equipe sênior de TI possuem conhecimento sobre o período e a execução do teste. Trata-se de uma simulação simulada às cegas para os operadores.

### 13. Onde o data center do cliente está fisicamente localizado?
* 📍 O data center da corporação está localizado fisicamente na cidade de **Houston**.

markdown

## ⚖️ Parte 2: Determine as Regras de Engajamento

### Etapa 1: Revise as informações na Planilha de Escopo

Abaixo está a consolidação dos parâmetros operacionais obtidos através da análise conjunta da transcrição da entrevista e dos requisitos técnicos mapeados na Planilha de Escopo.

| 🧩 Elemento das Regras de Engajamento | 📊 Valor Homologado |
| :--- | :--- |
| ⏳ **Cronograma de Testes** | Iniciar em duas semanas, reportar em 60 dias |
| 📍 **Local dos Testes** | Instalação de Houston |
| ⏰ **Janelas de tempo para testes (horas do dia)** | Testes não invasivos durante o horário comercial. Testes invasivos durante as horas das 2:00 às 6:00 de sexta-feira a domingo |
| 📞 **Método de comunicação preferencial** | Relatórios ou teleconferências |
| 🛡️ **Controles de segurança que poderiam potencialmente detectar ou prevenir testes** | Firewalls e IDS implementados |
| 🔒 **Tratamento de dados confidenciais** | NDA assinado |
| 💻 **Endereços IP ou redes a partir dos quais o teste será originado** | VLAN do departamento de TI interno |
| 🚫 **Tipos de testes permitidos ou proibidos** | Teste limitado a operações e servidores de logística. Testes SQL limitados ao ambiente de desenvolvimento. Engenharia social limitada aos endereços de email fornecidos. |
| 📇 **Contatos do cliente** | Gerente de Armazéns, Diretor de TI, Gerente de Operações. |

---
🔒 *Nota: Repositório educacional desenvolvido para fins acadêmicos e conformidade profissional.*
