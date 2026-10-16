# PRD Completo: Aplicativo de Finanças Pessoais Conversacional

> **Snippet para Vibe Coding & Especificação de Produto**  
> **Data de Emissão:** 16 de outubro de 2026  
> **Versão:** 2.0 (Design Universal WCAG 2.2 AA, Heurísticas de UX de Nielsen e Layout Adaptativo Mobile/Tablet)

---

## Resumo Executivo: O que é o App de Finanças Pessoais?

O **App de Finanças Pessoais Conversacional** é uma solução criada para acabar com o abandono do controle financeiro, substituindo formulários burocráticos e planilhas cansativas por uma **experiência fluida de diálogo com inteligência artificial**.

* **Registro em Segundos (< 12s):** O usuário apenas diz ou digita frases como *"Paguei 68 reais de luz hoje"* ou clica em atalhos inteligentes de 1 toque.
* **Validação Imediata com Liberdade:** A IA categoriza automaticamente entre 6 categorias fixas e exibe um cartão interativo com botões diretos de `[Mudar categoria]` e `[Desfazer]`.
* **Orientação Positiva sem Julgamentos:** Apresenta sempre o *Saldo Livre da Semana* e dicas de economia contextualizadas, sem jargões bancários.
* **Acessibilidade Universal (WCAG 2.2 AA):** Projetado para pessoas com deficiência visual, idosos, tremores motores ou TDAH (botões $\ge$ 48x48px, alto contraste e comandos por voz).
* **Experiência Multitela (Mobile & Tablet):** Operação ergonômica com uma mão no smartphone e modo **Split-View ao vivo no tablet**, onde o chat atualiza gráficos e metas em tempo real lado a lado.

> *Para uma leitura rápida e focada em negócios e produto, veja também o [RESUMO.md](file:///c:/projetos/dio-lab-vibe-coding-app-financas/RESUMO.md).*

---

## Uma Breve Reflexão sobre o Processo

> *Registro dos aprendizados, validações e desafios reais enfrentados durante a prototipagem com IA no Emergent.*  
> *Documento dedicado disponível em [REFLEXAO.md](file:///c:/projetos/dio-lab-vibe-coding-app-financas/REFLEXAO.md).*

### 1. O que funcionou bem?
* **O PRD como Âncora Cognitiva:** A inclusão prévia do PRD Snippet completo acelerou todo o processo no Emergent. A IA não alucinou interfaces genéricas; em vez disso, conduziu uma entrevista técnica assertiva (escolha do Gemini 3 Flash, login Google gerenciado, Web Speech API nativa e FastAPI + MongoDB com atualização ao vivo).
* **Entendimento de Diretrizes de Síntese:** A instrução extra *"Não complique"* foi perfeitamente assimilada, mantendo o escopo focado em soluções leves e diretas.
* **Geração Fiel de UI/UX:** A landing page (*"Conversa Financeira"*) e a tela de onboarding (*Passo 1 de 2: "Olá, Tarcisio!"*) foram criadas com fidelidade impressionante às heurísticas de Nielsen e design universal, incluindo botões grandes de 48px, pílulas de renda e simulação de cartões com `[Desfazer]`.

| Landing Page Gerada | Onboarding Conversacional (Passo 1) |
| :---: | :---: |
| ![Landing Page](assets/img/landing-page-emergent.png) | ![Onboarding](assets/img/onboarding-conversacional-emergent.png) |

### 2. O que não funcionou como o esperado?
* **Bug de Runtime no Frontend (`destroy is not a function`):** Apesar de todo o scaffolding ter sido gerado com sucesso (`server.py`, `useVoice.js`, `AuthCallback.jsx`), ao executar a aplicação no navegador ocorreu um erro clássico de React (`destroy is not a function` em `bundle.js`). Esse erro ocorre quando a função de retorno de um `useEffect` (comumente associada ao hook de áudio/Web Speech API) retorna uma Promise ou valor inválido em vez de uma função de cleanup.
* **Esgotamento de Créditos da Plataforma:** Antes que fosse possível enviar o stack trace de volta ao agente autônomo para depuração e correção do código, a cota de créditos gratuitos da sessão se esgotou, interrompendo o ciclo final de deploy.

![Runtime Error](assets/img/runtime-error-emergent.png)

### 3. O que aprendeu sobre conversar com IAs?
1. **Qualidade do Briefing:** Quanto mais rico e fundamentado for o PRD (com personas, restrições e regras visuais), mais assertivas e coerentes são as decisões arquiteturais tomadas pela IA.
2. **Desenvolvimento em Fatias Finas (*Thin Slices*):** Pedir todo o ecossistema (banco, backend, auth, áudio e UI) de uma só vez satura tokens e créditos. O fluxo ideal é iterar modularmente: UI estática $\rightarrow$ fluxo de chat $\rightarrow$ hooks de voz $\rightarrow$ integração backend.
3. **O Desenvolvedor como Diretor Técnico:** O Vibe Coding não substitui o conhecimento de engenharia; ele eleva o papel humano para o de arquiteto e revisor de qualidade, capaz de identificar problemas de ciclo de vida de componentes (como no `useEffect`) e conduzir a IA cirurgicamente.
4. **Poder das Restrições Negativas:** Comandos curtos de restrição como *"Não complique"* atuam como salvaguardas essenciais contra sobre-engenharia da IA.

---

## 1. Visão Geral, Proposta de Valor e Métricas de Sucesso

### Proposta de Valor e Job-to-be-Done (JTBD)
O aplicativo elimina a fricção e o abandono do controle financeiro pessoal ao transformar o registro de gastos e o planejamento de metas em uma conversa natural, acessível por texto, voz ou toques rápidos. Ele atende pessoas iniciantes — incluindo usuários com pouca familiaridade digital, idosos ou pessoas com limitações visuais e motoras — que desejam organizar o próprio dinheiro sem lidar com planilhas ou formulários complexos.

### Personas e Perfis de Uso
* **Iniciante Ansioso (Mobile First):** Jovem adulto ou trabalhador autônomo que usa o smartphone no transporte público com apenas uma mão, desiste de apps tradicionais na segunda semana e precisa registrar gastos em menos de 10 segundos.
* **Planejador Visual / Familiar (Usuário de Tablet):** Pessoa ou casal que prefere revisar as contas no sofá ou na mesa usando um tablet (iPad ou Android) no fim do dia ou fim de semana, aproveitando a tela maior para conversar com o Agente enquanto visualiza gráficos e metas lado a lado.
* **Usuário com Necessidades de Acessibilidade:** Pessoa com baixa visão, daltonismo, dislexia, tremores motores ou TDAH que precisa de fontes ampliáveis, alto contraste, leitura em voz alta, comandos por voz e baixa carga cognitiva.

### Métricas de Sucesso do MVP (KPIs)
* **Taxa de Ativação (D1):** Percentual de cadastrados que definem 1 meta e registram o 1º gasto no mesmo dia (Meta: $\ge$ 65%).
* **Tempo de Registro (Time-to-Log):** Tempo médio entre abrir o app e confirmar um gasto via chat ou voz (Meta: < 12 segundos).
* **Precisão de Classificação da IA:** Transações em que o usuário aceita a categoria sugerida sem precisar editar (Meta: $\ge$ 85%).
* **Retenção Semanal (D7 / D30):** Usuários que registram ao menos 3 transações por semana após 7 e 30 dias (Meta: D7 $\ge$ 40% / D30 $\ge$ 25%).

---

## 2. Jornada Essencial (Happy Path) e Arquitetura das Principais Telas

### Fluxo Principal em 5 Etapas
1. **Onboarding Guiado e Acessível:** Login social com 1 clique (Google/Apple) e duas perguntas no chat com botões grandes de toque rápido ou voz (*"Qual é sua renda mensal aproximada?"* e *"Qual é sua primeira meta financeira?"*), detectando preferências de fonte ampliada e alto contraste do aparelho.
2. **Entrada Multimodal de Gasto:** O usuário digita, dita por voz ou toca em um atalho inteligente dizendo *"Paguei 68 reais de luz hoje"*.
3. **Validação Visual Imediata:** O Agente Financeiro exibe um Cartão de Confirmação estruturado dentro do chat (`Valor: R$ 68,00` | `Categoria: Moradia / Contas` | `Data: Hoje`) com opção de desfazer ou alterar a categoria com 1 toque.
4. **Orientação Educativa sem Julgamento:** O Agente atualiza o saldo livre da semana e envia uma dica empática e acionável (*"Contas de casa em dia! Você ainda tem R$ 320 livres para o restante da semana."*).
5. **Visão Consolidada e Acompanhamento de Metas:** O usuário consulta seu progresso visual por meio de barras de metas e gráficos simplificados (em aba dedicada no celular ou no painel lateral ao vivo no tablet).

### Arquitetura das 4 Telas do MVP

#### Tela 1: Onboarding Conversacional
* **Objetivo:** Configurar renda, primeira meta e tom de voz sem formulários.
* **Componentes em ordem:**
  1. Cabeçalho minimalista com indicador *Passo 1 de 2* e botão de acessibilidade;
  2. Bolha de boas-vindas do Agente;
  3. Grade de botões de resposta rápida (*Quick Replies*) com faixas de renda e metas sugeridas;
  4. Barra inferior de entrada de texto/voz.

#### Tela 2: Chat do Agente Financeiro (Home)
* **Objetivo:** Registrar gastos, tirar dúvidas e receber recomendações.
* **Componentes em ordem:**
  1. Cabeçalho fixo com *Saldo Livre da Semana* e botão de ocultar valores (modo privacidade);
  2. Histórico de conversa com bolhas de diálogo, Cartões de Transação Confirmada e Cartões de Dica de Economia;
  3. Carrossel horizontal de sugestões rápidas acima do teclado (*"Gastei no mercado"*, *"Quanto posso gastar hoje?"*, *"Desfazer último"*);
  4. Barra de comando inferior com campo de texto, botão de microfone em destaque (48x48px) e botão de envio.

#### Tela 3: Painel de Metas
* **Objetivo:** Transformar economia em progresso visual recompensador.
* **Componentes em ordem:**
  1. Cabeçalho com resumo total poupado no mês;
  2. Cartão de Destaque da Meta Principal (título, ícone, barra de progresso percentual, valor atual vs. alvo e estimativa de conclusão);
  3. Botão primário de ação rápida (`+ Guardar dinheiro nesta meta`);
  4. Lista de metas secundárias e botão para criar nova meta no chat.

#### Tela 4: Resumo Simples (Relatórios)
* **Objetivo:** Mostrar a saúde financeira mensal sem sobrecarga visual.
* **Componentes em ordem:**
  1. Seletor simples de período (*Esta Semana* / *Este Mês* / *Mês Passado*);
  2. Cartão de Balanço Enxuto (*Entradas* vs. *Saídas* vs. *Reservado para Metas*);
  3. Gráfico de barras horizontais com as 5 categorias principais (ícone, nome, valor em reais e percentual arredondado);
  4. Cartão de Destaque do Agente resumindo em uma frase a principal mudança de hábito do mês.

---

## 3. Design Universal (WCAG 2.2 AA) e Heurísticas de UX (Nielsen)

### Os 4 Pilares de Design Universal no Produto
* **Perceptível (Visão e Audição):** Nenhum indicador financeiro depende exclusivamente de cor. Valores positivos, negativos e alertas combinam cor + ícone semântico + prefixo textual (`+ R$ 500,00` com seta para cima; `- R$ 45,00` com ícone de sacola; `! Atenção` com triângulo). Compatibilidade total com VoiceOver (iOS/iPadOS) e TalkBack (Android).
* **Operável (Motor e Físico):** Todos os botões, chips e cartões possuem área mínima de toque de **48x48px** com espaçamento mínimo de **8px**. Registro por voz permite uso 100% sem digitação.
* **Compreensível (Cognitivo e Educativo):** Linguagem livre de jargões contábeis e limite máximo de **6 categorias fixas** no MVP para evitar paralisia de escolha.
* **Robusto (Multidispositivo e Assistivo):** Suporte nativo a redimensionamento dinâmico de fontes até 200% sem quebrar o layout e navegação completa via teclado externo no tablet.

### Auditoria Preventiva por Heurísticas de Nielsen
1. **Visibilidade do Status do Sistema (Severidade: Crítico):** Sempre renderizar um Cartão de Transação com selo *"Salvo em Alimentação"* e atualizar o topo de *Saldo Livre* com microanimação suave e atributo `aria-live="polite"`.
2. **Correspondência entre o Sistema e o Mundo Real (Severidade: Grave):** Substituir termos bancários por fala acessível (*"Anotei R$ 35,00 em Lazer. Você ainda tem R$ 115,00 livres para curtir este mês!"*).
3. **Controle e Liberdade do Usuário (Severidade: Crítico):** Incluir dentro de cada Cartão de Transação dois botões diretos: `[Mudar categoria]` e `[Desfazer]` com ação em 1 toque.
4. **Consistência e Padrões (Severidade: Médio):** Fixar 6 categorias imutáveis com cores e ícones padronizados: Essenciais/Moradia (Casa), Alimentação (Garfo), Transporte (Carro/Ônibus), Lazer (Estrela), Saúde/Bem-estar (Coração) e Metas/Futuro (Cofrinho).
5. **Prevenção de Erros (Severidade: Crítico):** Quando um valor fugir do padrão da categoria (ex.: *"1500 no café"*), exibir confirmação preventiva antes de salvar (*"Você quis dizer R$ 15,00 ou R$ 1.500,00 no café?"*).
6. **Reconhecimento em vez de Memorização (Severidade: Grave):** Nunca exibir tela em branco pura; manter 3 a 4 pílulas de ação sugerida acima do campo de texto.
7. **Flexibilidade e Eficiência de Uso (Severidade: Médio):** Criar chips de 1 toque baseados no histórico recorrente do usuário (ex.: *"Almoço ~R$ 30"*).
8. **Estética e Design Minimalista (Severidade: Grave):** Arredondar porcentagens nos gráficos (14% em vez de 14,38%) e usar barras horizontais limpas.
9. **Recuperação de Erros (Severidade: Grave):** Em frases ambíguas (*"Paguei 50 pro João"*), responder com pergunta guiada e botões de categoria; em modo offline, salvar na fila local e sincronizar automaticamente.
10. **Ajuda e Documentação (Severidade: Cosmético):** Botão discreto *"Por que estou vendo essa dica?"* nos cartões do Agente com explicação educativa de 2 linhas.

---

## 4. Design Adaptativo e Especificações Técnicas de Interface (Mobile & Tablet)

### Comportamento por Dispositivo e Breakpoints
* **Smartphone (< 768px):** Barra Inferior (*Bottom Navigation*) com 3 abas (Chat, Metas, Resumo) na zona do polegar (*Thumb Zone*). Coluna única (100% da largura) e edição via *Bottom Sheets*.
* **Tablet em Modo Retrato (768px - 1023px):** Trilho Lateral Esquerdo (*Navigation Rail*) fixo com 72px de largura. Coluna central de chat limitada a 680px para conforto de leitura, acompanhada de painel superior fixo com as 2 principais metas e resumo semanal.
* **Tablet em Modo Paisagem e Desktop ($\ge$ 1024px):** Trilho Lateral ou Sidebar (80px a 220px) + Arquitetura Split-View (Visão Dividida Ao Vivo em 2 Painéis):
  * **Painel Esquerdo (50% da área útil):** Chat ativo com o Agente Financeiro.
  * **Painel Direito (50% da área útil):** Painel vivo com Resumo Simples e Painel de Metas empilhados, atualizados em tempo real a cada mensagem enviada no chat.
* **Adaptações Específicas de Tablet:** Suporte a Multitarefa (*Split View / Slide Over* do iPadOS e Android) usando CSS Container Queries para alternar automaticamente para coluna única quando a janela for dividida com o app do banco; suporte a escrita com Apple Pencil / S Pen (*Scribble*) e atalhos de teclado físico (`Enter` envia, `Shift+Enter` quebra linha, `Cmd/Ctrl+K` foca no registro rápido).

### Especificações do Design System
* **Grid e Alvos de Toque:** Múltiplos de 8px (padding de 16px no mobile, 24px no tablet); alvos de toque mínimos de **48x48px**.
* **Paleta de Cores WCAG AA/AAA:**
  * Superfície Clara: `#F8FAFC` / Escura: `#0F172A`
  * Primária: Verde-Esmeralda `#047857` (contraste 5.4:1)
  * Texto Principal: `#1E293B` (contraste 14.8:1)
  * Alerta: Âmbar `#B45309` sobre `#FEF3C7`
  * Erro: Vermelho-Rubi `#B91C1C` sobre `#FEE2E2`
* **Tipografia:** Inter ou Plus Jakarta Sans em unidades `rem` (corpo `1rem`, valores de cartão `1.25rem`, saldo principal `1.75rem-2rem`) com propriedade obrigatória `font-variant-numeric: tabular-nums`.

---

## 5. Modelo de Dados Enxuto e Arquitetura de Recursos

### Entidades Principais
* `User`: `id`, `nome`, `email`, `renda_mensal`, `dia_fechamento_mes`, `preferencias_ui` (JSON: `tamanho_fonte`, `alto_contraste`, `modo_privacidade`, `layout_tablet_preferido`).
* `CategoryBudget`: `id`, `user_id`, `categoria_slug` (`moradia`, `alimentacao`, `transporte`, `lazer`, `saude`, `outros`), `limite_mensal`, `cor_hex`, `icone_id`.
* `Transaction`: `id`, `user_id`, `category_id`, `valor_centavos` (inteiro), `tipo` (`despesa`/`receita`), `texto_original`, `confianca_ia` (`0.0` a `1.0`), `status` (`confirmado`/`pendente_revisao`), `data_transacao`.
* `Goal`: `id`, `user_id`, `titulo`, `valor_alvo_centavos`, `valor_atual_centavos`, `prazo_meta`, `prioridade`.
* `AgentConversation`: `id`, `user_id`, `role` (`user`/`assistant`/`system_card`), `conteudo`, `transaction_id_vinculada`, `criado_em`.

### Stack Técnica e Conformidade (LGPD)
* **Front-end:** Next.js (React) ou Flutter configurado como PWA com Tailwind CSS e componentes acessíveis (Radix UI / React Aria).
* **Back-end e Realtime:** Supabase (PostgreSQL + Auth + Realtime) para sincronização instantânea entre smartphone e tablet.
* **IA:** API Gemini 2.5 Flash ou GPT-4o-mini com Structured Outputs (JSON Schema) retornando dados da transação, resposta empática e estado do cartão.
* **Privacidade (LGPD):** Anonimização dos prompts enviados à IA (sem nome completo, CPF ou e-mail) e opções nativas de exportar dados e excluir conta.

---

## 6. Backlog de Implementação Acionável (MVP vs. V2)

### Escopo do MVP (Semanas 1 a 4)
1. **[UI/Arquitetura]** Configurar estrutura PWA responsiva com coluna única no mobile (< 768px), Navigation Rail no tablet retrato (768px-1023px) e Split-View ao vivo no tablet paisagem ($\ge$ 1024px).
2. **[Acessibilidade]** Implementar tokens de cores WCAG AA, suporte a Dynamic Type (`rem`), `tabular-nums` para cifras, atributos `aria-live` no chat e modo privacidade.
3. **[Onboarding]** Criar fluxo inicial conversacional de 2 passos com chips de toque rápido (48x48px) para renda estimada e primeira meta.
4. **[Core IA e Chat]** Desenvolver endpoint NLP com Structured Outputs que classifica gastos nas 6 categorias fixas, detecta valores atípicos e retorna Cartão de Transação com botões `[Mudar categoria]` e `[Desfazer]`.
5. **[Voz Nativa]** Habilitar entrada de voz via Web Speech API / ditado nativo no botão de microfone do chat.
6. **[Metas e Relatórios]** Construir barra de progresso de Metas e gráfico de barras horizontais acessíveis (cor + ícone + texto) sincronizados via Realtime.
7. **[Agente Financeiro]** Configurar gatilhos de dicas educativas (alerta ao atingir 80% do orçamento da categoria e celebração de avanço na meta).

### Escopo da V2 (Evolução Pós-Validação)
1. **[Omnichannel]** Integrar bot oficial no WhatsApp e Telegram sincronizado com o painel do app e tablet.
2. **[Visão Computacional]** Leitura de fotos de cupons fiscais e comprovantes Pix enviados no chat.
3. **[Modo Casal/Família no Tablet]** Orçamento compartilhado para revisão conjunta no modo paisagem do tablet.
4. **[Open Finance]** Importação automática opcional de extratos e notificações bancárias.

---

## 7. Plano de Validação Inicial e Descoberta de Produto

### Matriz CSD
* **Certezas:** Formulários longos causam abandono na 1ª semana; telas de tablet que apenas esticam o layout mobile desperdiçam espaço útil.
* **Suposições:** Os botões `[Desfazer]` e `[Mudar categoria]` eliminam a frustração com erros da IA; usuários de tablet valorizam ver o gráfico atualizar ao vivo ao lado do chat.
* **Dúvidas:** Usuários preferem registrar por voz ou por chips de atalho + texto curto? Qual é a frequência ideal de dicas do Agente sem gerar fadiga?

### Roteiro de Pesquisa e Teste de Usabilidade
* **Perfil:** 6 a 8 iniciantes (incluindo 2 pessoas 50+ ou com necessidades de acessibilidade e 2 usuários de tablet).
* **Perguntas de Comportamento Passado:**
  * *"Me mostre como você tentou anotar seus gastos da última vez e o que deu mais trabalho?"*
  * *"Em qual horário e aparelho você costuma revisar suas contas?"*
* **Tarefas Práticas no Protótipo:**
  1. Registrar *"Paguei 120 reais na farmácia"* e corrigir uma classificação propositalmente errada usando o botão `[Mudar categoria]` em menos de 5 segundos;
  2. Olhar o painel Split-View por 5 segundos e responder quanto ainda pode gastar na semana.

### Testes Rápidos de Demanda e Go-to-Market
* **Experimento Mágico de Oz (7 Dias):** Grupo individual no WhatsApp com 5 a 10 voluntários enviando gastos reais e recebendo cartões padronizados e resumo visual no 3º e 7º dia.
* **Protótipo Navegável V0/Lovable:** Validação direta de toque e leitura em smartphone e tablet real.
* **Posicionamento:** *"Controle seu dinheiro conversando: registre gastos em segundos no celular e planeje suas metas com clareza total no tablet — sem planilhas, sem jargões e feito para todos."*
