# Workforce Analytics — Sistema de Controle de Efetivo

Sistema web para **planejamento e acompanhamento de efetivo** por função, dia e turno. Interface única em `index.html` com **HTML5 + Tailwind (CDN) + JavaScript Vanilla** e gráficos em **Canvas 2D**.

## Recursos
- **Período**: data inicial e nº de semanas com geração automática de dias.
- **Jornada**: entrada, saída e intervalo com **cálculo de carga líquida**.
- **Planejado vs Real**: lançamento por **função** e **turno (dia/noite)**, por dia.
- **Dashboard**: totais de horas, **eficiência (%)** e **variação** entre planejado e executado.
- **Análises**: gráfico comparativo **Planejado x Real** por função.
- **UX**: layout responsivo, sidebar, cabeçalho com ações rápidas e atividade recente.
- **Sem dependências pesadas**: Tailwind via CDN, Font Awesome e Google Fonts (Inter).

## Stack
- **Front-end**: HTML5 + Tailwind CSS (CDN) + Font Awesome + Google Fonts.
- **Lógica**: JavaScript Vanilla.
- **Gráfico**: `<canvas>` com API 2D nativa.
- **Persistência**: **não há** (estado em memória da página).

## Estrutura do Projeto
```
/
└── index.html
```

## Como Executar
1. Baixe o repositório ou copie o `index.html`.
2. Abra o arquivo no navegador moderno (Chrome, Edge ou Firefox).
3. Opcional para auto-reload: sirva em um host local.
   - VS Code: extensão **Live Server**.
   - Ou Python: `python -m http.server 8000` e acesse `http://127.0.0.1:8000`.

## Como Usar
1. **Configuração do Período**  
   Defina a **data inicial** e o **nº de semanas**. Se vazio, o sistema sugere a próxima segunda-feira.
2. **Configurações de Jornada**  
   Informe entrada, saída e intervalo. A carga líquida/dia é calculada.
3. **Planejamento**  
   Preencha por **função** e **turno** os quantitativos diários planejados.
4. **Execução**  
   Lance os valores **reais** por função e turno.
5. **Dashboard**  
   Veja **Horas Planejadas**, **Horas Reais**, **Eficiência (%)** e **Variação**.
6. **Análises**  
   Acesse o gráfico Planejado x Real por função.

## Cálculos (resumo)
- **Carga líquida/dia (h)** = `horaSaída − horaEntrada − intervalo`.
- **Horas por função** = soma (dia + noite) ao longo dos dias do período.
- **Eficiência (%)** = `(Horas Reais / Horas Planejadas) × 100`.
- **Variação (h)** = `Horas Reais − Horas Planejadas`.

## Personalização
### Adicionar/editar funções
No início do `<script>`, ajuste o objeto `functions`:
```js
const functions = {
  meiooficial: { name: 'MEIO OFICIAL', icon: 'tools', color: 'blue' },
  // ...
  pintor: { name: 'PINTOR', icon: 'brush', color: 'violet' } // exemplo
};
```
- `icon`: nome do ícone **Font Awesome** (versão 6).
- `color`: rótulo de cor usado nas classes utilitárias Tailwind (para estilos contextuais).

### Semanas padrão
```js
let weekCount = 4; // nº inicial de semanas
```

### Paleta e tema
Variáveis no `:root` em `<style>`:
```css
:root {
  --primary: #2563eb;  /* azul */
  --primary-dark: #1d4ed8;
  --surface: #ffffff;
  --background: #f8fafc;
  --border: #e2e8f0;
  /* ... */
}
```

## Limitações Atuais
- **Sem persistência**: os dados se perdem ao recarregar a página.
- **Sem autenticação** e **sem controle de acesso**.
- **Gráfico** básico em Canvas 2D sem zoom ou exportação.

## Roadmap Sugerido
- Persistência via **API (PHP/Node) + MySQL** ou **LocalStorage** opcional.
- **Exportar PDF** de planejamento e relatórios.
- **Importar/Exportar CSV** para escala.
- **Autenticação** e perfis de acesso.
- **Filtros avançados** no gráfico e indicadores adicionais (absenteísmo, alocação por centro de custo).
- **Modo escuro**.

## Boas Práticas e Manutenção
- Mantenha IDs e classes das seções: `dashboard-section`, `planning-section`, `execution-section`, `analytics-section`, `settings-section`.
- Evite renomear elementos usados por `querySelector`/`getElementById`.
- Teste em resoluções móveis e desktop. Tailwind já cobre responsividade básica.

## Requisitos
- Navegador moderno com ES6 habilitado.
- Acesso à CDN do Tailwind, Font Awesome e Google Fonts.

## Licença
Defina a licença do projeto (por exemplo, MIT).

## Autor
**Thaynison** — Gerente de TI e Analista de Sistemas  
Links: site e GitHub do projeto.
