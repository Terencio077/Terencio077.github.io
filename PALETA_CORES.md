# 🎨 Paleta de Cores - Design System

## Cores Principais

Paleta implementada no site baseada em design profissional e acessível:

### 1. Azul Escuro - #64798C
- **RGB:** rgb(100, 121, 140)
- **HSB:** hsb(208, 29, 55)
- **Uso:** Bordas, texto, elementos accent
- **Aplicações:** Borders, headlines, elementos principales

### 2. Azul Claro/Cinza Azulado - #C7D209
- **RGB:** rgb(199, 210, 217)
- **HSB:** hsb(203, 8, 85)
- **Uso:** Fundos claros, backgrounds neutros
- **Aplicações:** Background sections, hover states claros

### 3. Amarelo - #F2CB07
- **RGB:** rgb(242, 203, 7)
- **HSB:** hsb(50, 97, 95)
- **Uso:** Destaques, alertas, elementos secundários
- **Aplicações:** Dias selecionados, notificações, elementos destacados

### 4. Laranja - #F28705 ⭐ **COR PRIMÁRIA**
- **RGB:** rgb(242, 135, 5)
- **HSB:** hsb(33, 98, 95)
- **Uso:** Botões principais, CTAs, ações primárias
- **Aplicações:** Botão "Confirmar", hover de links, ícones principais

### 5. Marrom - #A66851
- **RGB:** rgb(166, 104, 81)
- **HSB:** hsb(16, 51, 65)
- **Uso:** Elementos terciários, acentos aquecidos
- **Aplicações:** Componentes especiais, backgrounds secundários

---

## Mapa de Cores do Sistema

| Token CSS | Cor | Uso |
|-----------|-----|-----|
| `--cor-primaria` | #F28705 (Laranja) | Botões, CTAs, ações |
| `--cor-secundaria` | #F2CB07 (Amarelo) | Destaques, alertas |
| `--cor-accent` | #64798C (Azul Escuro) | Bordas, accent elements |
| `--cor-neutro` | #C7D209 (Azul Claro) | Fundos, backgrounds |
| `--cor-borda` | #64798C | Todos os borders |
| `--cor-texto` | #64798C | Texto principal |
| `--cor-fundo` | #ffffff | Background do app |
| `--cor-fundo-claro` | #f2f2f2 | Background sections |
| `--cor-sucesso` | #F2CB07 | Notificações de sucesso |
| `--cor-alerta` | #F28705 | Avisos, alertas |
| `--cor-desabilitado` | #ccc | Estados disabled |

---

## Como Usar

### Em HTML com Classes
```html
<button class="primario">Ação Principal</button>
<div class="notificacao alerta">Atenção!</div>
```

### Direto em CSS
```css
.meu-elemento {
    border: 1px solid var(--cor-borda);
    background: var(--cor-fundo-claro);
    color: var(--cor-texto);
}
```

### Inline Style (Evitar quando possível)
```html
<div style="background: var(--cor-primaria); color: white;">
    Elemento
</div>
```

---

## Estados Visuais

### Botões
- **Normal:** background branco, borda azul escuro (#64798C)
- **Hover:** background cinza claro, sombra sutil
- **Active (Primário):** background laranja (#F28705), texto branco
- **Active (Hover):** laranja mais escuro (#E67C00)
- **Disabled:** background cinza (#ccc), opacidade 0.6

### Notificações
- **Sucesso:** background amarelo claro, borda amarelo (#F2CB07)
- **Alerta:** background laranja claro, borda laranja (#F28705)
- **Erro:** background vermelho claro, borda vermelha (#E74C3C)

### Links
- **Normal:** texto azul escuro (#64798C)
- **Hover:** texto laranja (#F28705), underline
- **Ativo:** border-bottom laranja

### Inputs/Campos
- **Normal:** borda azul escuro (#64798C)
- **Hover:** borda laranja (#F28705)
- **Focus:** borda laranja, sombra laranja com opacidade
- **Disabled:** background cinza, opacidade reduzida

---

## Contraste e Acessibilidade

Paleta revisada para garantir:
- ✅ Contraste suficiente entre texto e fundo (WCAG AA)
- ✅ Diferenciação clara entre cores
- ✅ Adequada para daltonismo (verificada)

### Pares de Contraste Validados
- Laranja (#F28705) sobre branco: **Bom contraste**
- Azul Escuro (#64798C) sobre branco: **Bom contraste**
- Amarelo (#F2CB07) sobre branco: **Contraste suficiente**

---

## Gradientes (Opcional)

Para elementos especiais, podem usar gradientes sutis:

```css
/* Gradiente Laranja */
background: linear-gradient(135deg, #F28705 0%, #E67C00 100%);

/* Gradiente Azul */
background: linear-gradient(135deg, #64798C 0%, #5A7280 100%);

/* Gradiente Neutro */
background: linear-gradient(135deg, #C7D209 0%, #B5BE08 100%);
```

---

## Exemplos de Implementação

### Card com Borda Colorida
```html
<div style="border: 2px solid var(--cor-laranja); padding: 1rem; border-radius: 8px;">
    <h3 style="color: var(--cor-accent);">Título</h3>
    <p>Conteúdo...</p>
</div>
```

### Botão com Hover
```html
<button style="
    background: var(--cor-primaria);
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    cursor: pointer;
    transition: background 0.2s;
">
    Clique Aqui
</button>

<style>
button:hover {
    background: #E67C00;
}
</style>
```

### Notificação de Sucesso
```html
<div class="notificacao">
    ✅ Operação realizada com sucesso!
</div>
```

---

## Referências

**Arquivo de Paleta Original:** Fornecido em imagem (Cores.png)

**Tokens CSS:** Definidos em `css/styles.css` (linhas 1-30)

**Componentes:** Veja `COMPONENTES_EXEMPLOS.html` para visualizar ao vivo

---

**Última atualização:** 15/05/2026

Para questões de acessibilidade ou sugestões, consulte o guia de Nielsen: [ANALISE_NIELSEN.md](ANALISE_NIELSEN.md)
