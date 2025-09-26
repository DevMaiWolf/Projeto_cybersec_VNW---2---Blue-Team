# Projeto_cybersec_VNW---2---Blue-Team
Projeto 2 - VNW - CyberSec - Consultoria Blue Team - Mai Wolf S/A

<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/c0dfbf53-4519-4d87-8f32-67a1b201f116" />

# Proposta de Estratégia de Defesa Cibernética para Mai Wolf S/A

**Cliente:** Mai Wolf S/A 

**Setor:** E-commerce

**Elaborado por:** Maiara Viegas – Analista de Segurança  - Blue Team

**Data:** 23/09/2025  

---

##  Sumário

1. [Sumário Executivo](#1-sumário-executivo)  
2. [Objetivo](#2-objetivo)  
3. [Escopo](#3-escopo)  
4. [Metodologia](#4-metodologia)  
5. [Diagrama de Arquitetura](#5-diagrama-de-arquitetura)  
6. [Evidências/Diagnóstico](#6-evidências/diagnóstico)
7. [Proposta Técnica](#7-proposta-técnica)  
8. [Conclusão](#8-conclusão)  

---

## 1. Sumário Executivo
Este documento apresenta uma proposta de estratégia de segurança cibernética para a Mai Wolf S/A, focada em mitigar os riscos de ataques web e de autenticação, conforme os incidentes recentes. A abordagem se baseia no princípio de Defesa em Profundidade, priorizando soluções de alto impacto e baixo custo que se alinham com o orçamento e o tamanho da equipe.

A solução inicial foca em três pilares: proteção do perímetro web, visibilidade centralizada e procedimentos de resposta a incidentes. Um Web Application Firewall (WAF) será implementado para deter ataques como SQLi e XSS. Para resolver a questão dos logs espalhados, um sistema de coleta de logs (log shipper) será configurado para centralizar eventos em um SIEM simples, permitindo a criação de alertas essenciais.

O plano de ação, estruturado em um roadmap de 3 meses, prioriza as "vitórias rápidas" (quick wins) nos primeiros 30 dias. O objetivo é proporcionar uma melhoria imediata na postura de segurança e na capacidade de detecção, movendo a Mai Wolf S/A de uma posição reativa para uma mais proativa.

---
## 2. Objetivo
O objetivo é propor e estruturar uma estratégia de segurança cibernética pragmática para a Mai Wolf S/A, com foco na proteção de seus serviços de e-commerce e na melhoria da capacidade de detecção e resposta a incidentes, considerando as limitações de orçamento e de equipe.

---
## 3. Escopo
A consultoria se limita à proposição de planos e recomendações estratégicas, sem a realização de atividades de implementação direta. O escopo abrange:

    Arquitetura de defesa: Recomendação de camadas de proteção essenciais.

    Plano de monitoramento: Definição de fontes de log, alertas e métricas.

    Plano de resposta a incidentes: Estrutura de resposta baseada em um modelo simplificado do NIST.

    Recomendações priorizadas: Ações de alto impacto e baixo custo.

    Roadmap: Cronograma de 3 meses com foco em quick wins.

---
## 4. Metodologia
A metodologia adotada é a de consultoria ágil e focada em resultados, seguindo os passos:

    Diagnóstico: Análise dos incidentes e da arquitetura existente.

    Desenho da solução: Proposição de uma arquitetura de defesa em camadas simples e eficiente.

    Priorização (80/20): Identificação das ações que resolvem a maioria dos riscos com o menor esforço.

    Plano de ação: Criação de um roadmap detalhado com fases e responsáveis.



## 5. Diagrama da Arquitetura de Defesa em Camadas (Mermaid)
---<img width="647" height="641" alt="mermaide" src="https://github.com/user-attachments/assets/d75ad949-4498-4eb2-93b6-d47605cc88bf" />

---
## 6. Evidências/Diagnóstico
    Incidentes de Segurança: O briefing menciona tentativas de SQLi e XSS em aplicativos, e brute-force na rota /login. Isso indica que a camada de aplicação e a camada de identidade são os alvos mais visados no momento. A ausência de um WAF deixa o site vulnerável a esses ataques automatizados.

    Ausência de SIEM: Os logs estão espalhados, o que torna a detecção de ameaças complexa e reativa. Não é possível correlacionar um ataque de SQLi com um login com sucesso ou com atividades incomuns, como por exemplo, um pico de tentativas de acesso. A visibilidade é o principal gargalo.

    Backups Sem Validação: Embora existam backups, a falta de testes de restauração é um risco crítico. Em caso de ataque, como um ransomware ou corrupção de dados, não há garantia de que a recuperação será bem-sucedida, impactando diretamente na disponibilidade.

---
## 7. Proposta Técnica
Com base no princípio 80/20, as seguintes recomendações são priorizadas para um impacto máximo com esforço mínimo:

7.1. Plano de Ação - Quick Wins (30 dias)

    Ação 1: Implementar WAF/CDN: Adotar uma solução como Cloudflare (plano gratuito ou Pro) que oferece um WAF, proteção DDoS básica e aceleração. Isso mitigará instantaneamente os ataques de SQLi e XSS.

    Ação 2: Centralizar logs: Configurar um agente de coleta de logs (como o Filebeat) em cada instância para enviar logs de Nginx, Node.js e PostgreSQL para um servidor centralizado.

    Ação 3: SIEM mínimo viável: Usar uma solução SIEM de código aberto, como o ELK Stack ou o Graylog, para receber os logs.

    Ação 4: Alertas essenciais: Criar as primeiras regras de alerta no SIEM para:

        * Múltiplas tentativas de login com falha em um minuto (mitiga brute-force).

        * Bloqueio de requisições pelo WAF.

    Ação 5: Teste de backup: Realizar o primeiro teste de restauração de um backup de dados do PostgreSQL em um ambiente de teste.

7.2. Plano de Monitoramento/SIEM

Fontes de log essenciais:

    Nginx: Logs de acesso (access.log), com informações sobre IPs, user-agents, e requisições HTTP.

    Node.js: Logs de aplicação (erros, tentativas de login, atividades de usuário).

    PostgreSQL: Logs de banco de dados (erros de consulta, tentativas de acesso).

Regras de alerta e correlação:

    Nginx | Tentativa_Login_Falha: Se access.log mostra mais de 10 requisições POST /login de um mesmo IP em 60 segundos com status 401 Unauthorized.

    WAF | SQLi_Detectado: Se o log do WAF indica uma requisição bloqueada por uma regra de injeção de SQL.

KPIs/Métricas de monitoramento:

    MTTD (Mean Time to Detect): Monitorar se os alertas estão sendo gerados em tempo hábil.

    MTTR (Mean Time to Respond): Medir o tempo que a equipe leva para iniciar a contenção após o alerta.

7.3. Plano de resposta a incidentes (NIST Simplificado)

O plano de resposta será simplificado e focado nas três fases mais críticas para a Mai Wolf S/A.

1. Detecção e análise:

    Procedimento: A equipe de Ops é notificada por e-mail ou Slack a partir de um alerta do SIEM.

    Ação: O colaborador de Ops verifica o alerta no SIEM e notifica os desenvolvedores se for necessário.

2. Contenção:

    Procedimento: Ação imediata para limitar o dano.

    Runbook de Exemplo:

        Incidente: Alerta de brute-force.

        Ações de Contenção:

            * Confirmar o alerta e o IP malicioso no SIEM.

            * Adicionar o IP à lista de bloqueio do firewall ou do WAF.

            * Notificar o time de devs sobre o incidente.

3. Recuperação:

    Procedimento: Ação para restaurar os serviços ao estado normal.

    Runbook de Exemplo:

        Incidente: Dados corrompidos por um ataque.

        Ações de Recuperação:

          *  Isolar o servidor de banco de dados.

          *  Executar o procedimento de restauração de backup em um ambiente de teste.

          *  Após validação, restaurar o banco de dados de produção.


---

## 8. Conclusão
A Mai Wolf S/A enfrenta desafios de segurança comuns a e-commerces em crescimento. A proposta de implementar um WAF, centralizar logs em um SIEM e estabelecer um plano de IR simplificado oferece um caminho claro para mitigar os riscos mais urgentes. A abordagem priorizada, focada em quick wins, permitirá que a empresa fortaleça sua segurança de forma incremental e sustentável, garantindo a proteção de seus clientes e de seus negócios.

---


