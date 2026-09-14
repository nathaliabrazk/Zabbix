
# Zabbix

# 🔐 Estudos sobre Zabbix

---

## 💡 O que é o Zabbix?

O **Zabbix** é uma solução de nível enterprise, de código aberto e com suporte a monitoração distribuída.

O **Zabbix** é um software que monitora vários parâmetros da rede, dos servidores e da saúde dos serviços. Utiliza-se de um mecanismo flexível de notificação que permite configurar alertas por e-mail para praticamente qualquer evento. As notificações permitem que se reaja rapidamente à problemas no ambiente. O Zabbix oferece excelentes recursos de relatórios e visualização de dados armazenados. Isso faz com que o Zabbix seja a ferramenta ideal para planejamento de capacidade.

O **Zabbix** suporta tanto "pooling" quanto "trapping". Os relatórios e estatísticas do Zabbix, e seus parâmetros de configuração, estão acessíveis através de interface web. O uso de uma interface web garante que você possa avaliar o estado de sua rede e a saúde de seus servidores a partir de qualquer local. Quando corretamente configurado o Zabbix pode desempenhar papel importante na infraestrutura de monitoramento de TI. Estas características se aplicam tanto a pequenas organizações com poucos servidores quanto para grandes empresas, com milhares de servidores.

---

## 🌱 Origem do Zabbix

**Criador:** Alexei Vladishev, que hoje atua como fundador e CEO da empresa.

**Origem:** O software começou a ser desenvolvido em 1998 quando Vladishev trabalhava como administrador de sistemas em um banco e precisava automatizar tarefas de monitoramento.

**Lançamento público:** O código foi aberto ao público sob a licença GPL em 2001, com a primeira versão estável (1.0) lançada em 2004.Manutenção: Atualmente, o software é desenvolvido, mantido e suportado pela Zabbix SIA, sediada em Riga, na Letônia

## 💎 Benefícios do Zabbix

**Custo-benefício (Open Source):** A ferramenta é gratuita e de código aberto, sem taxas de licença por volume de uso.

**Monitoramento Completo:** Acompanha servidores, máquinas virtuais, rede, nuvem, bancos de dados e dispositivos IoT em uma única tela.

**Detecção Automática (Auto-discovery):** Identifica novos dispositivos conectados à rede de forma automática e aplica padrões de monitoramento.

**Alertas Inteligentes:** Envia notificações imediatas por e-mail, SMS ou chat quando o sistema detecta falhas ou comportamentos anômalos.

**Escalabilidade:** Permite monitorar desde pequenos ambientes até grandes redes corporativas distribuídas com o uso de proxies.

**Painéis Personalizados:** Cria gráficos e relatórios visuais em tempo real sobre o desempenho da infraestrutura.

**Integração com sistemas de help desk e gestão de incidentes:** Funciona de forma automatizada para transformar alertas técnicos em chamados práticos.

**Como o processo funciona na práticaDetecção da Falha:** O Zabbix monitora servidores, redes ou aplicações. Quando um limite é ultrapassado, uma trigger (gatilho) muda de estado e gera um evento/incidente.


**Comunicação via Webhook:** O método padrão e mais moderno utiliza Webhooks nativos do Zabbix executando códigos em JavaScript. O Zabbix faz uma requisição HTTP para a API do sistema de help desk, enviando dados cruciais como nome do host, IP, descrição do erro e nível de severidade. 

**Criação do Chamado:** O software de help desk recebe os dados via API e abre o ticket automaticamente, preenchendo categoria, prioridade e atribuindo ao grupo de suporte correto. 

**Atualização e Fechamento Binário (Two-Way):** Se o problema piorar ou receber novos comentários, o Zabbix pode atualizar o chamado.Quando o serviço é restabelecido e o Zabbix detecta a normalização (Recovery), ele envia um novo comando via API para encerrar ou finalizar o chamado automaticamente sem intervenção humana.

**Sem limites artificiais:** Diferente de ferramentas comerciais que cobram por número de hosts ou métricas coletadas, no Zabbix você monitora o quanto sua infraestrutura aguentar. 

---

## 🧱Compontentes da arquitetura do Zabbix

**Zabbix server**
É o componente central que coleta e gerencia os dados para o monitoramento sem agentes e de agentes. Em caso de anormalidades, são emitidos alertas.

**Zabbix Proxy**
É um processo que recebe e coleta dados do monitoramento e envia ao Zabbix Server. Os dados recebidos são armazenados temporariamente e transferidos ao Zabbix Server. Sua utilização é opcional, porém  é muito benéfica, por que distribui a carga de monitoração normalmente atribuída ao Zabbix Server.

Com esse recurso é possível:

Monitorar em zonas DMZ ou em zonas que ficam por trás de firewalls.
Monitorar de forma interna toda a infraestrutura e serviços de sua empresa.
Tornar o monitoramento mais efetivo.
Diminuir a carga do Zabbix server.


**Zabbix agent -**
Ao instalar o agente em seu servidor, o software faz o monitoramento de atributos como CPU, RAM, internet e ROM. Além disso permite coletar métricas personalizadas com o uso de scripts ou programas externos. Veja aqui como é feita a instalação do agente.

---

## 🆕Novidades Zabbix
**Suporte ao ClickHouse -**  ClickHouse pode ser usado como banco de dados de backend do Zabbix para armazenar o histórico de valores de item.

**Tipo de dado JSON -** O Zabbix agora oferece suporte a JSON como um tipo de dado para valores de item.

Anteriormente, valores JSON eram coletados por itens de texto e armazenados como strings com um limite de 64 KB. Agora, o Zabbix pode armazenar valores JSON nativamente com um limite de 128 MiB e também rejeitar valores JSON inválidos (por exemplo, contendo chaves sem aspas, vírgulas finais ou colchetes incompatíveis).

O tipo de dado JSON é suportado por todos os tipos de item e protótipo de item, exceto Calculated, e está disponível na exportação de dados em tempo real e em connectors. Valores JSON podem ser armazenados em todos os bancos de dados suportados e no Elasticsearch. Se você estiver usando TimescaleDB, consulte as notas de atualização.

Observe que itens com o tipo de dado JSON não podem ser usados em triggers; no entanto, você pode extrair campos JSON com itens dependentes que tenham um tipo de dado não JSON e usá-los em triggers.

Itens que retornam uma string JSON (net.if.discovery, vfs.file.get, etc.) ainda são itens de texto; no entanto, você pode alterá-los para JSON, se necessário.

**O Zabbix MCP (Model Context Protocol)** Surge como um divisor de águas na governança de TI. Ele permite que modelos de linguagem grandes (LLMs) e agentes de IA se conectem de forma nativa ao ecossistema de monitoramento, transformando dados operacionais brutos em insights e ações automatizadas em tempo real.O Model Context Protocol (MCP) é um padrão aberto desenvolvido pela Anthropic para conectar IAs a fontes de dados e ferramentas externas de maneira segura e padronizada. Ao introduzir um servidor MCP no Zabbix, a IA deixa de ser apenas uma interface de chat e passa a ser um operador ativo do seu ambiente.
