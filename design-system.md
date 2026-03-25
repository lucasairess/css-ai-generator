# 🎨 Design System — Gerador de CSS com IA (DevClub)

Sistema de design tokenizado para o projeto. Todos os tokens são implementados como **CSS Custom Properties** (variáveis CSS), permitindo manutenção centralizada e consistência visual.

---

## 🪙 Tokens — Referência Completa

### 🎨 Cores (Color Tokens)

```css
:root {
  /* ── Primitivos ── */
  --color-black:        #09090b;   /* Zinc 950 — fundo global */
  --color-surface:      #141419;   /* Superfície de cards/inputs */
  --color-border:       #27272a;   /* Zinc 800 — bordas sutis */
  --color-text-primary: #fafafa;   /* Zinc 50 — títulos */
  --color-text-body:    #e4e4e7;   /* Zinc 200 — corpo */
  --color-text-muted:   #71717a;   /* Zinc 500 — texto secundário */

  /* ── Brand / Accent ── */
  --color-brand:        #22c55e;   /* Green 500 — cor principal */
  --color-brand-hover:  #16a34a;   /* Green 600 — hover do botão */
  --color-brand-glow:   rgba(34, 197, 94, 0.25); /* Brilho verde */

  /* ── Semânticos ── */
  --color-code:         #34d399;   /* Emerald 400 — texto de código */
  --color-error:        #ef4444;   /* Red 500 — erros */
  --color-error-bg:     rgba(239, 68, 68, 0.1);  /* Fundo de erro */
  --color-success:      #22c55e;   /* Sucesso / confirmação */
}
```

#### Paleta visual

| Token | Hex | Uso |
|---|---|---|
| `--color-black` | `#09090b` | Fundo global do body |
| `--color-surface` | `#141419` | Cards, inputs, iframe |
| `--color-border` | `#27272a` | Bordas de todos elementos |
| `--color-text-primary` | `#fafafa` | `<h1>`, títulos marcantes |
| `--color-text-body` | `#e4e4e7` | Texto geral do body |
| `--color-text-muted` | `#71717a` | Subtítulos, placeholders |
| `--color-brand` | `#22c55e` | Botão, `<span>` destaque, links |
| `--color-brand-hover` | `#16a34a` | Hover do botão principal |
| `--color-code` | `#34d399` | Texto dentro do bloco de código |
| `--color-error` | `#ef4444` | Mensagens de erro |

---

### 📝 Tipografia (Typography Tokens)

```css
:root {
  /* ── Família ── */
  --font-family-base:   'Inter', sans-serif;

  /* ── Tamanhos ── */
  --font-size-xs:       12px;
  --font-size-sm:       14px;
  --font-size-base:     16px;
  --font-size-lg:       18px;
  --font-size-xl:       20px;
  --font-size-2xl:      24px;
  --font-size-3xl:      32px;
  --font-size-4xl:      40px;

  /* ── Pesos ── */
  --font-weight-regular: 400;
  --font-weight-medium:  500;
  --font-weight-semibold: 600;
  --font-weight-bold:    700;

  /* ── Line Height ── */
  --line-height-tight:  1.25;
  --line-height-normal: 1.5;
  --line-height-relaxed: 2;
}
```

| Token | Valor | Uso |
|---|---|---|
| `--font-size-4xl` | `40px` | `<h1>` — Headline principal |
| `--font-size-2xl` | `24px` | `<h2>` — Section titles |
| `--font-size-base` | `16px` | Botão, texto geral |
| `--font-size-sm` | `14px` | Bloco de código |
| `--font-size-xs` | `12px` | Labels, metadados |

---

### 📐 Espaçamento (Spacing Tokens)

```css
:root {
  --spacing-1:   4px;
  --spacing-2:   8px;
  --spacing-3:   12px;
  --spacing-4:   16px;
  --spacing-5:   20px;
  --spacing-6:   24px;
  --spacing-8:   32px;
  --spacing-10:  40px;
  --spacing-12:  48px;
  --spacing-16:  64px;
}
```

Escala baseada em múltiplos de **4px** (sistema 4-point grid).

---

### 🔲 Bordas & Raios (Border Tokens)

```css
:root {
  --border-width:        1px;
  --border-color:        var(--color-border);

  --radius-sm:           6px;
  --radius-md:           10px;
  --radius-lg:           12px;
  --radius-xl:           16px;
  --radius-full:         9999px;
}
```

---

### 🌫️ Sombras (Shadow Tokens)

```css
:root {
  --shadow-sm:   0 1px 3px rgba(0, 0, 0, 0.3);
  --shadow-md:   0 4px 12px rgba(0, 0, 0, 0.4);
  --shadow-glow: 0 0 20px var(--color-brand-glow);
}
```

---

### ⚡ Animações (Motion Tokens)

```css
:root {
  --duration-fast:    150ms;
  --duration-normal:  250ms;
  --duration-slow:    400ms;
  --ease-default:     cubic-bezier(0.4, 0, 0.2, 1);   /* Material ease */
  --ease-spring:      cubic-bezier(0.34, 1.56, 0.64, 1); /* Spring */
}
```

---

### 📏 Layout (Layout Tokens)

```css
:root {
  --max-width-input:    640px;   /* Largura máxima do form */
  --max-width-content:  1200px;  /* Largura máxima do layout geral */
  --output-min-height:  380px;   /* Altura mínima do grid de output */
}
```

---

## 🧩 Componentes

### Button — `.botao-gerar`

| Estado | Aparência |
|---|---|
| Default | Background `--color-brand`, texto preto bold |
| Hover | Background `--color-brand-hover`, shadow glow |
| Loading | Texto "Gerando..." + cursor not-allowed |
| Focus | Outline 2px `--color-brand` + offset |

```css
/* Uso dos tokens */
.botao-gerar {
  background:    var(--color-brand);
  color:         var(--color-black);
  font-size:     var(--font-size-base);
  font-weight:   var(--font-weight-bold);
  border-radius: var(--radius-md);
  padding:       var(--spacing-4) var(--spacing-5);
  transition:    background var(--duration-normal) var(--ease-default),
                 box-shadow var(--duration-normal) var(--ease-default);
}
.botao-gerar:hover {
  background:  var(--color-brand-hover);
  box-shadow:  var(--shadow-glow);
}
```

---

### Textarea — `.caixa-texto`

```css
.caixa-texto {
  background:    var(--color-surface);
  border:        var(--border-width) solid var(--border-color);
  border-radius: var(--radius-md);
  color:         var(--color-text-primary);
  font-size:     var(--font-size-base);
  padding:       var(--spacing-4);
}
```

---

### Code Block — `.bloco-codigo`

```css
.bloco-codigo {
  background:    var(--color-surface);
  border:        var(--border-width) solid var(--border-color);
  border-radius: var(--radius-lg);
  color:         var(--color-code);
  font-size:     var(--font-size-sm);
  line-height:   var(--line-height-relaxed);
}
```

---

### Preview Frame — `.resultado-codigo`

```css
.resultado-codigo {
  background:    var(--color-surface);
  border:        var(--border-width) solid var(--border-color);
  border-radius: var(--radius-lg);
  min-height:    var(--output-min-height);
}
```

---

## 🎭 Background Animado

O fundo usa dois layers empilhados:

1. **Mesh Gradient** — gradiente radial em posições absolutas que se movem via `@keyframes`
2. **Grid pattern** — pseudo-elemento com grade CSS sutil (`background-size: 40px 40px`)

```css
/* Exemplo do token de animação do fundo */
@keyframes gradientMove {
  0%   { transform: translate(0%, 0%) scale(1); }
  50%  { transform: translate(3%, 5%) scale(1.05); }
  100% { transform: translate(0%, 0%) scale(1); }
}
```

---

## ♿ Acessibilidade

- Contraste mínimo de **4.5:1** para texto sobre fundo (WCAG AA)
- `outline` visível em todos os elementos focáveis
- Atributo `aria-label` em elementos sem texto descritivo
- Semântica HTML correta (`<pre><code>` para blocos de código)
