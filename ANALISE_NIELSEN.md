# Análise de Usabilidade - Heurísticas de Nielsen

## Projeto: Aplicativo de Receitas e Planejamento de Refeições

---

## 📊 RESUMO EXECUTIVO

O projeto está em **fase inicial de desenvolvimento** com um design visual limpo e estrutura básica funcional. Porém, apresenta **lacunas significativas** em termos de usabilidade e conformidade com as Heurísticas de Nielsen.

**Score Estimado: 5/10** ⚠️

---

## 🎯 ANÁLISE POR HEURÍSTICA

### 1️⃣ VISIBILIDADE DO STATUS DO SISTEMA
**Status: ❌ CRÍTICO - Precisa ser implementado**

#### Problemas Identificados:
- ❌ Nenhum feedback visual para ações do usuário (cliques em botões)
- ❌ Sem indicador de carregamento em transições de página
- ❌ Sem confirmação visual ao adicionar receitas à agenda
- ❌ Sem indicador de progresso ao preencher formulários
- ❌ Links ativos não mostram estado atual (ex: footer não destaca página ativa)

#### Recomendações:
```html
<!-- Adicionar estado visual aos elementos interativos -->
<!-- 1. Destaque a página ativa no footer -->
<footer>
  <ul>
    <li><a href="index.html" class="ativo"><!-- página atual --></a></li>
  </ul>
</footer>

<!-- 2. Adicionar feedback em botões -->
.btn:hover { background: #e8f5e9; }
.btn:active { transform: scale(0.95); }

<!-- 3. Toast/notificação para ações -->
<div class="notificacao" role="alert">✓ Receita adicionada à agenda!</div>
```

---

### 2️⃣ CORRESPONDÊNCIA ENTRE SISTEMA E MUNDO REAL
**Status: ✅ BOM - Implementado parcialmente**

#### Pontos Positivos:
- ✅ Linguagem em português (apropriada para público brasileiro)
- ✅ Ícones familiar: casa, lupa, agenda, pessoas
- ✅ Conceitos familiares: receitas, dispensa, agenda de refeições

#### Problemas:
- ❌ Abreviações confusas: "Q" para Quarta (difícil de entender)
- ❌ Nomenclatura inconsistente: "despensa" vs "dispensa"
- ❌ Ícones de interação não óbvios (ex: números "12" em posts sem contexto)
- ⚠️ "Dias desativados" na semana não explicam por quê

#### Recomendações:
```html
<!-- Usar dias completos ou abreviações claras -->
<li><abbr title="Segunda">Seg</abbr></li>

<!-- Explicar elementos não-óbvios -->
<li><a href="#" title="12 comentários">
  <img src="img/mensagem_post.png" alt="Comentários">12
</a></li>

<!-- Tooltip para ações -->
<button title="Adicionar à dispensa">+</button>
```

---

### 3️⃣ CONTROLE E LIBERDADE DO USUÁRIO
**Status: ⚠️ MÉDIO - Parcialmente implementado**

#### Problemas Identificados:
- ❌ Nenhum botão "Cancelar" ou "Voltar" consistente (apenas em calendário)
- ⚠️ Seta de voltar inconsistente entre páginas
- ❌ Sem confirmação antes de ações destrutivas (remover receita, limpar dispensa)
- ❌ Sem opção de "Desfazer" ou "Editar" após ação concluída
- ❌ Busca aparentemente não-funcional (link vazio)
- ❌ Usuário não consegue "escapar" facilmente (sem botão X em modais)

#### Recomendações:
```html
<!-- 1. Botões de ação consistentes -->
<div class="acoes">
  <button class="btn-cancelar">Cancelar</button>
  <button class="btn-confirmar">Confirmar</button>
</div>

<!-- 2. Confirmação antes de remover -->
<button onclick="confirmarRemocao('Tem certeza que deseja remover?')">
  Remover
</button>

<!-- 3. Sistema de desfazer -->
<div class="undo-toast">
  Receita removida
  <button>Desfazer</button>
</div>

<!-- 4. Botão fechar em diálogos -->
<div class="modal">
  <button class="fechar" aria-label="Fechar">&times;</button>
</div>
```

---

### 4️⃣ CONSISTÊNCIA E PADRÕES
**Status: ⚠️ MÉDIO - Inconsistências encontradas**

#### Problemas:
- ⚠️ **Headers com padrões diferentes**: `header_simples`, `header_pesquisa`, `header_dispensa`
  - Alguns têm seta voltar, outros não
  - Posicionamento da seta varia
- ⚠️ **Botões com estilos inconsistentes**:
  - Alguns com borda, alguns sem
  - Tamanhos diferentes (.btn_confirmar é circular, outros não)
- ❌ **Navegação inconsistente**: Footer sempre presente, mas menu lateral em algumas páginas não
- ⚠️ **Cores não padronizadas**: 
  - Estados ativos: #ffe08a (amarelo), #e8f5e9 (verde) - por quê?
  - Qual cor representa qual estado?
- ❌ **Nomenclatura de classes**:
  - `semana_bolinhas`, `lista_dias_mes`, `lista_refeicoes` - padrão inconsistente

#### Recomendações:
```css
/* Design System padronizado */

/* 1. Estados de botão unificados */
.btn {
  padding: 0.5rem 1rem;
  border: 0.1rem solid #222;
  border-radius: 0.35rem;
  background: #fff;
  cursor: pointer;
}

.btn:hover { background: #f0f0f0; }
.btn:active { background: #e0e0e0; }
.btn.primario { background: #4CAF50; color: #fff; }
.btn.primario:hover { background: #45a049; }

/* 2. Estados de componente */
.ativo { border-bottom: 0.3rem solid #222; }
.desativado { color: #ccc; cursor: not-allowed; }
.selecionado { background: #ffe08a; }
.destaque { background: #e8f5e9; }

/* 3. Header unificado com variantes */
.header {
  display: flex;
  align-items: center;
  border-bottom: 0.1rem solid #222;
  padding: 0.5rem 0.75rem;
}

.header.com-voltar { position: relative; }
.header .voltar { position: absolute; left: 0.5rem; }
```

---

### 5️⃣ PREVENÇÃO DE ERROS
**Status: ❌ CRÍTICO - Não implementado**

#### Problemas:
- ❌ Nenhuma validação de entrada visível
- ❌ Nenhuma mensagem de erro ou aviso
- ❌ Ações irreversíveis sem confirmação (remover items da dispensa)
- ❌ Usuário pode agendar refeição em dia passado sem aviso
- ❌ Sem verificação se dispensa tem ingredientes suficientes
- ❌ Busca não funciona mas não há mensagem de erro

#### Recomendações:
```html
<!-- 1. Validação em tempo real -->
<input type="text" 
       placeholder="Digite para buscar..." 
       oninput="validarBusca(this.value)"
       required>
<span class="erro" id="erro-busca"></span>

<!-- 2. Alertas preventivos -->
<div class="alerta-preventivo" role="alert">
  ⚠️ Você está agendando para uma data no passado
  <button>Entendi, continuar mesmo assim</button>
</div>

<!-- 3. Confirmação antes de ação irreversível -->
<button onclick="confirmarRemocao()">
  Remover da dispensa
</button>

<!-- 4. Indicador de campos obrigatórios -->
<label>Nome da receita <span class="obrigatorio">*</span></label>

<!-- 5. Mensagens de erro claras -->
<div class="erro-mensagem">
  ❌ Nenhuma receita encontrada com "asfasdf"
  <p>Dica: Tente buscar por ingredientes principais</p>
</div>
```

---

### 6️⃣ RECONHECIMENTO EM VEZ DE RECALL
**Status: ✅ BOM - Implementado bem**

#### Pontos Positivos:
- ✅ Menu visual com ícones no footer
- ✅ Calendário mostra data visualmente
- ✅ Receitas exibem imagens
- ✅ Dia "hoje" destacado em verde

#### Problemas:
- ⚠️ Ícones pequenos no footer podem ser confusos (ex: "pratos" é vago)
- ❌ Sem breadcrumb mostrando localização no app
- ❌ Sem "você está aqui" durante navegação
- ❌ Histórico de ações não visível
- ❌ Favoritos/receitas salvas não têm indicador visual claro

#### Recomendações:
```html
<!-- 1. Breadcrumb -->
<nav aria-label="breadcrumb">
  <a href="index.html">Início</a> > 
  <a href="receita_a.html">Macarronada</a> > 
  <span>Modo de Preparo</span>
</nav>

<!-- 2. Indicador de página ativa -->
<footer>
  <ul>
    <li><a href="index.html" class="ativo" aria-current="page">
      <img src="img/casa.png" alt="Início">
    </a></li>
  </ul>
</footer>

<!-- 3. Ícone de favorito com estado -->
<button class="favoritar" aria-pressed="false">
  <img src="img/estrela_vazia.png" alt="Favoritar">
</button>

<!-- 4. Tooltip descritivo nos ícones -->
<a href="#" title="Ver todas as receitas">
  <img src="img/pratos.png" alt="Receitas">
</a>
```

---

### 7️⃣ FLEXIBILIDADE E EFICIÊNCIA DE USO
**Status: ❌ CRÍTICO - Não implementado**

#### Problemas:
- ❌ Nenhum atalho de teclado (ex: Enter para confirmar)
- ❌ Sem modo "favoritos" para acesso rápido
- ❌ Sem filtros/busca avançada
- ❌ Sem histórico de receitas visualizadas
- ❌ Sem sugestões baseadas em uso anterior
- ❌ Interface idêntica para novatos e usuários experientes

#### Recomendações:
```html
<!-- 1. Atalhos de teclado -->
<script>
document.addEventListener('keydown', (e) => {
  if (e.key === 'Enter' && e.ctrlKey) {
    // Confirmar ação
  }
  if (e.key === '/') {
    // Abrir busca
  }
});
</script>

<!-- 2. Seção de favoritos rápidos -->
<section class="favoritos-rapidos">
  <h2>Seus favoritos</h2>
  <ul>
    <li><a href="receita_a.html">Macarronada ⭐</a></li>
  </ul>
</section>

<!-- 3. Busca avançada -->
<form class="busca-avancada">
  <input type="text" placeholder="Nome da receita">
  <select>
    <option value="">Tipo: Todos</option>
    <option>Sobremesa</option>
  </select>
  <select>
    <option value="">Tempo: Qualquer um</option>
    <option>Até 15 min</option>
  </select>
</form>

<!-- 4. Modo compacto para usuários avançados -->
<button class="modo-compacto">Ver modo compacto</button>
```

---

### 8️⃣ DESIGN ESTÉTICO E MINIMALISTA
**Status: ✅ BOM - Bem implementado**

#### Pontos Positivos:
- ✅ Design limpo e sem poluição visual
- ✅ Espaçamento adequado
- ✅ Tipografia legível (Nunito + Playwrite Ireland)
- ✅ Paleta de cores coerente
- ✅ Máximo 26rem de largura (mobile-first)
- ✅ Sem banners de publicidade ou pop-ups desnecessários

#### Problemas:
- ⚠️ Algumas páginas podem estar vazias (ex: aba_de_pesquisa)
- ⚠️ Grade de ingredientes (dispensa) pode ficar muita vazia
- ⚠️ Cards de receita podem ser muito espaçados

#### Recomendações:
```css
/* Melhorar experiência quando vazio */
.vazio {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 60vh;
  color: #999;
  gap: 1rem;
}

.vazio-icone {
  font-size: 4rem;
  opacity: 0.3;
}

.vazio-texto {
  text-align: center;
  font-size: 0.95rem;
}

/* Call to action suave */
.cta-suave {
  background: #f9f9f9;
  border: 0.1rem dashed #ccc;
  border-radius: 0.35rem;
  padding: 1rem;
  text-align: center;
}
```

---

### 9️⃣ AJUDA E DOCUMENTAÇÃO
**Status: ❌ CRÍTICO - Não implementado**

#### Problemas:
- ❌ Nenhuma seção de "Ajuda" ou FAQ
- ❌ Sem tooltips explicativos
- ❌ Sem onboarding para novos usuários
- ❌ Sem documentação sobre funcionalidades
- ❌ Sem atalhos de teclado documentados
- ❌ Sem glossário de termos (ex: "dispensa" vs "pantry")

#### Recomendações:
```html
<!-- 1. Ícone de ajuda -->
<button class="ajuda-icone" aria-label="Abrir ajuda" title="Pressione ? para ajuda">?</button>

<!-- 2. Modal de ajuda contextual -->
<div class="modal-ajuda" id="ajuda-dispensa">
  <h2>Como usar a Dispensa</h2>
  <p>A dispensa mostra os ingredientes que você tem em casa.</p>
  <ol>
    <li>Clique em + para adicionar ingredientes</li>
    <li>Selecione de nossas sugestões ou escreva seu ingrediente</li>
    <li>Marque como usado ao finalizar uma receita</li>
  </ol>
  <button>Entendi</button>
</div>

<!-- 3. Tour guiado para primeiro acesso -->
<div class="tour-overlay" id="tour-1">
  <div class="tour-pointer">
    <h3>Bem-vindo! 👋</h3>
    <p>Aqui você encontra as receitas da semana</p>
    <button>Próximo</button>
  </div>
</div>

<!-- 4. Atalhos visíveis -->
<div class="atalhos">
  <p><kbd>/</kbd> - Buscar</p>
  <p><kbd>?</kbd> - Ajuda</p>
  <p><kbd>Esc</kbd> - Fechar</p>
</div>

<!-- 5. FAQ integrada -->
<details>
  <summary>O que é a "Dispensa"?</summary>
  <p>A dispensa é um espaço onde você registra os ingredientes que possui...</p>
</details>
```

---

### 🔟 RECUPERAÇÃO DE ERROS
**Status: ⚠️ MÉDIO - Parcialmente implementado**

#### Problemas:
- ⚠️ Aviso de "Ingredientes faltando" existe (bom!)
- ❌ Sem mensagem de erro clara quando busca falha
- ❌ Sem sugestão de alternativas quando ingrediente não encontrado
- ❌ Links quebrados mostram página em branco
- ❌ Sem fallback de imagens (se imagem não carregar)
- ❌ Sem recuperação se usuário sair do app acidentalmente

#### Recomendações:
```html
<!-- 1. Mensagem de erro amigável -->
<div class="erro-pagina">
  <h1>❌ Oops! Página não encontrada</h1>
  <p>Parece que essa página não existe mais.</p>
  <a href="index.html" class="btn">Voltar ao início</a>
</div>

<!-- 2. Fallback de imagem -->
<img src="receita.jpg" 
     alt="Macarronada"
     onerror="this.src='img/placeholder.png'">

<!-- 3. Mensagem para busca sem resultado -->
<div class="sem-resultado">
  <p>Nenhuma receita encontrada com "xyz"</p>
  <p>💡 Dicas:</p>
  <ul>
    <li>Verifique a ortografia</li>
    <li>Tente buscar por ingredientes</li>
    <li><a href="#">Ver todas as receitas</a></li>
  </ul>
</div>

<!-- 4. Sugestão de alternativa -->
<p>Não encontramos "tomate romano". 
Talvez você queira: 
<a href="#">Tomate italiano</a> ou 
<a href="#">Tomate cereja</a>
</p>

<!-- 5. Recuperação de sessão -->
<script>
// Salvar estado da aplicação
localStorage.setItem('ultimaPagina', 'receita_a.html');

// Se voltou do cache, redirecionar
if (performance.navigation.type === 1) {
  window.location.href = localStorage.getItem('ultimaPagina');
}
</script>
```

---

## 📋 RESUMO DAS IMPLEMENTAÇÕES NECESSÁRIAS

| Heurística | Status | Prioridade | Esforço |
|-----------|--------|-----------|--------|
| 1. Visibilidade Status | ❌ Crítico | ALTA | Médio |
| 2. Correspondência Real | ✅ Bom | BAIXA | Baixo |
| 3. Controle Usuário | ⚠️ Médio | ALTA | Médio |
| 4. Consistência | ⚠️ Médio | ALTA | Alto |
| 5. Prevenção Erros | ❌ Crítico | ALTA | Alto |
| 6. Reconhecimento | ✅ Bom | BAIXA | Baixo |
| 7. Flexibilidade | ❌ Crítico | MÉDIA | Alto |
| 8. Design Minimalista | ✅ Bom | BAIXA | Baixo |
| 9. Ajuda Documentação | ❌ Crítico | MÉDIA | Médio |
| 10. Recuperação Erros | ⚠️ Médio | MÉDIA | Médio |

---

## 🎯 PLANO DE AÇÃO (Prioridades)

### 🔴 FASE 1 - CRÍTICA (Fazer primeiro)
1. **Feedback visual de ações** (Heurística 1)
   - Toast/notificações
   - Estados de hover/active em botões
   - Página ativa no footer

2. **Consistência de padrões** (Heurística 4)
   - Padronizar headers
   - Unificar estilos de botão
   - Sistema de cores claro

3. **Prevenção de erros** (Heurística 5)
   - Confirmações antes de ação destrutiva
   - Validação visível
   - Mensagens de erro

### 🟡 FASE 2 - IMPORTANTE
4. **Controle do usuário** (Heurística 3)
   - Botão cancelar consistente
   - Sistema de desfazer
   - Escapar de diálogos

5. **Documentação e Ajuda** (Heurística 9)
   - Onboarding
   - Tooltips
   - FAQ

### 🟢 FASE 3 - MELHORIA
6. **Flexibilidade** (Heurística 7)
   - Atalhos de teclado
   - Busca avançada
   - Favoritos rápidos

---

## 💡 CHECKLIST DE IMPLEMENTAÇÃO

### Imediato (Próximas 2 sprints)
- [ ] Adicionar toasts de notificação
- [ ] Criar sistema de cores padronizado (design tokens)
- [ ] Unificar estilos de header e botões
- [ ] Adicionar confirmação de ação destrutiva
- [ ] Implementar indicador de página ativa

### Curto prazo (1 mês)
- [ ] Criar onboarding para novos usuários
- [ ] Adicionar tooltips em elementos confusos
- [ ] Implementar breadcrumb
- [ ] Melhorar mensagens de erro
- [ ] Adicionar estados vazios com CTA

### Médio prazo (2-3 meses)
- [ ] Busca avançada com filtros
- [ ] Sistema de atalhos de teclado
- [ ] Tour guiado
- [ ] FAQ integrada
- [ ] Histórico de ações com desfazer

---

## 📚 REFERÊNCIAS

- [Nielsen's 10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/)
- [Designing for Mobile Apps](https://www.nngroup.com/articles/designing-mobile-apps/)
- [Error Prevention Best Practices](https://www.nngroup.com/articles/error-prevention/)

---

**Última atualização:** 14/05/2026
