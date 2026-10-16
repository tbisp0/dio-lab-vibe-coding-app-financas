# 💡 Resumo do Produto: App de Finanças Pessoais Conversacional

> **Conceito, Proposta de Valor e Diferenciais do MVP**  
> *Projeto desenvolvido no contexto do desafio DIO Vibe Coding com IA*

---

## 🧭 O que é o Aplicativo?
O **App de Finanças Pessoais Conversacional** é uma solução inteligente desenhada para **eliminar a fricção, a ansiedade e o abandono** do controle financeiro pessoal. Em vez de obrigar o usuário a preencher formulários burocráticos ou navegar por planilhas intimidadoras, o aplicativo funciona por meio de uma **conversa natural e acolhedora** com um Agente de IA — suportando **voz, texto e toques rápidos**.

---

## 🎯 Qual problema ele resolve?
Mais de 70% das pessoas desistem de aplicativos financeiros convencionais logo nas primeiras duas semanas por três motivos centrais:
1. **Entrada manual cansativa:** Formulários com muitos campos para cada cafezinho gasto.
2. **Linguagem bancária fria e jargões contábeis:** Dificuldade de compreensão por iniciantes e leigos.
3. **Falta de acessibilidade real:** Layouts densos, fontes pequenas e interfaces que ignoram limitações visuais, cognitivas ou motoras.

O nosso app resolve isso transformando o registro em um diálogo instantâneo de **menos de 12 segundos**, sem julgamentos e com suporte total a todos os perfis de usuários.

---

## ⚡ Como Funciona no Dia a Dia?

### 1. Registro Multimodal Instantâneo (< 12 segundos)
O usuário pode falar ou digitar naturalmente:
> *"Paguei 68 reais de luz hoje"* ou *"Almoço de 35 reais no cartão"*.

Também pode utilizar **pílulas de atalho de 1 toque** para despesas cotidianas frequentes baseadas no seu histórico.

### 2. Validação Visual com Liberdade Total
O Agente Financeiro interpreta a mensagem e responde imediatamente com um **Cartão Estruturado**:
* **Valor:** R$ 68,00
* **Categoria:** Moradia / Contas (classificada automaticamente entre 6 categorias fixas)
* **Ações em 1 toque:** Botões integrados `[Mudar categoria]` e `[Desfazer]`. O usuário nunca fica refém de uma interpretação errônea da IA.

### 3. Orientação Empática e Saldo Livre Semanal
Em vez de focar apenas no que já foi gasto, o app destaca quanto você ainda tem livre:
> *"Contas de casa em dia! Você ainda tem R$ 320,00 livres para o restante da semana."*

### 4. Metas Visuais e Recompensadoras
Aba dedicada ou painel lateral onde guardar dinheiro vira progresso tangível: barra de porcentagem visual, estimativa de conclusão e botão de aporte rápido.

---

## 🌟 Principais Diferenciais e Inovações

| Pilar | Como se Aplica no App | Benefício para o Usuário |
| :--- | :--- | :--- |
| **Conversacional Real** | Processamento de linguagem natural com saídas estruturadas (JSON Schema) via Gemini 2.5 Flash / GPT-4o-mini. | Registro ágil e intuitivo, sem parecer uma planilha. |
| **Design Universal (WCAG 2.2 AA)** | Alvos de toque $\ge$ 48x48px, alto contraste, suporte a leitores de tela (VoiceOver/TalkBack), fontes até 200% e cifras com `tabular-nums`. | Inclusão real para pessoas idosas, com baixa visão, tremores motores ou TDAH. |
| **Layout Adaptativo (Mobile & Tablet)** | Coluna única na zona do polegar no smartphone (< 768px) e **Split-View ao vivo** no tablet ($\ge$ 1024px). | No tablet, o chat atualiza o gráfico e as metas lado a lado em tempo real, ideal para planejamento no sofá em família. |
| **Prevenção de Erros (Nielsen)** | Confirmação preventiva para valores atípicos (ex.: *"Você quis dizer R$ 15 ou R$ 1.500 no café?"*). | Segurança psicológica contra digitações acidentais. |
| **Privacidade e LGPD** | Anonimização nativa de prompts enviados à IA (sem CPF, nome completo ou dados bancários). | Total conformidade e tranquilidade com os dados do usuário. |

---

## 📱 As 4 Telas Essenciais do MVP
1. **Onboarding Conversacional:** Boas-vindas amigáveis, renda aproximada e primeira meta configuradas em 2 perguntas rápidas com botões grandes.
2. **Chat do Agente Financeiro (Home):** O coração do app, com saldo livre sempre visível, histórico com cartões interativos e botão de voz destacado.
3. **Painel de Metas:** Progresso claro da meta principal, cofrinho digital e celebração de conquistas.
4. **Resumo Simples:** Entradas vs. Saídas vs. Poupado, acompanhado de gráfico de barras horizontais limpo das 5 maiores categorias.

---

*Para a especificação técnica detalhada, modelo de dados e backlog completo, consulte o [README.md](file:///c:/projetos/dio-lab-vibe-coding-app-financas/README.md).*
