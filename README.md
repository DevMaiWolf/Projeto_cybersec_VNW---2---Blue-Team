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
6. [Proposta Técnica](#6-proposta-técnica)  
7. [Recomendações de Segurança](#7-recomendações-de-segurança)  
8. [Plano de Ação (modelo 80/20)](#8-plano-de-ação-modelo-8020)  
9. [Conclusão](#9-conclusão)  

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

---
## 5. Diagrama da Arquitetura de Defesa em Camadas (Mermaid)
<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/" />

---
## 6. Proposta Técnica


---
## 7. Conclusão
A Mai Wolf S/A enfrenta desafios de segurança comuns a e-commerces em crescimento. A proposta de implementar um WAF, centralizar logs em um SIEM e estabelecer um plano de IR simplificado oferece um caminho claro para mitigar os riscos mais urgentes. A abordagem priorizada, focada em quick wins, permitirá que a empresa fortaleça sua segurança de forma incremental e sustentável, garantindo a proteção de seus clientes e de seus negócios.

---


