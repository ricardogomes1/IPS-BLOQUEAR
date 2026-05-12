🛡️ Firewall Shield - Estratégia de Bloqueio Nuclear
Este repositório/documento contém as listas de bloqueio otimizadas para o pfSense, focadas em eliminar ruído de scanners globais e ataques direcionados a serviços de banco de dados (Oracle, SQL, MySQL, Postgres) e Terminal Server (RDP/SSH).

🚀 Estrutura das Listas
1. ESTRANGEIROS_NUCLEAR
Alvo: Infraestrutura de Cloud (AWS, Azure, GCP, DigitalOcean), continentes inteiros (Ásia, África, Leste Europeu) e redes de botnets.

Métrica: Bloqueio de aproximadamente 1.2 bilhão de IPs.

Otimização: Uso de supernetting (blocos /8 a /5) para garantir performance máxima na CPU do firewall.

2. BR_HOSTILE_INFRA
Alvo: Data centers nacionais, provedores de hosting com alto índice de abuso e máquinas zumbis em redes regionais.

Diferencial: Oracle Cloud Safe. Não bloqueia as faixas da Oracle SP/Vinhedo para garantir a conectividade dos clientes.

Precisão: Uso de máscaras /24 em operadoras residenciais para neutralizar o ataque sem gerar "fogo amigo".

⚙️ Como Implementar no pfSense
Aliases:

Crie um Alias tipo Network(s) para cada lista.

Cole os IPs/CIDRs fornecidos.

Regras de Firewall (WAN):

TOP (Prioridade 1): Whitelist (IPs de Suporte e Oracle Cloud SP). Ação: Pass.

Prioridade 2: Regra de bloqueio usando o Alias ESTRANGEIROS_NUCLEAR. Ação: Block.

Prioridade 3: Regra de bloqueio usando o Alias BR_HOSTILE_INFRA. Ação: Reject (opcional para facilitar troubleshoot nacional).

Prioridade 4: Suas regras de NAT / Port Forward.

⚠️ Notas de Manutenção
Logs: Se o Suricata/Snort parar de alertar, a lista está funcionando (o tráfego é descartado antes da inspeção profunda).

Troubleshooting: Se um serviço legítimo falhar, verifique Status > System Logs > Firewall. Se o IP for legítimo, mova-o para a Whitelist.

Update: Revisar os logs semanalmente para identificar novos "sobreviventes" que cruzaram o muro.

Status atual: 🛡️ Nível Jedi Ativo.
