<!DOCTYPE html>
<html lang="pt-BR" data-theme="light">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Gestão de Academias</title>
  <link href="https://api.fontshare.com/v2/css?f[]=satoshi@300,400,500,700,900&display=swap" rel="stylesheet">
  <style>
    :root, [data-theme="light"] {
      --text-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
      --text-sm: clamp(0.875rem, 0.8rem + 0.35vw, 1rem);
      --text-base: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);
      --text-lg: clamp(1.125rem, 1rem + 0.75vw, 1.35rem);
      --text-xl: clamp(1.5rem, 1.2rem + 1.25vw, 2rem);
      --space-1: 0.25rem; --space-2: 0.5rem; --space-3: 0.75rem; --space-4: 1rem; --space-5: 1.25rem; --space-6: 1.5rem; --space-8: 2rem; --space-10: 2.5rem; --space-12: 3rem; --space-16: 4rem;
      --radius-sm: 0.5rem; --radius-md: 0.75rem; --radius-lg: 1rem; --radius-xl: 1.25rem; --radius-full: 9999px;
      --color-bg: #f5f5f6; --color-surface: #ffffff; --color-surface-2: #fafafa; --color-surface-offset: #ececef; --color-border: #ddddE3; --color-divider:#e8e8ec;
      --color-text: #16171a; --color-text-muted: #666b75; --color-text-faint: #969ba5; --color-text-inverse: #ffffff;
      --color-primary: #2f3338; --color-primary-hover: #191c20; --color-primary-highlight: #dfe1e4;
      --color-danger: #c53939; --color-danger-bg: #fdeaea; --color-success: #1f7a4f; --color-success-bg:#e7f7ef;
      --shadow-sm: 0 1px 2px rgba(10,10,10,.04); --shadow-md: 0 8px 22px rgba(10,10,10,.06); --shadow-lg: 0 20px 50px rgba(10,10,10,.10);
      --transition: 180ms cubic-bezier(0.16, 1, 0.3, 1);
      --sidebar-w: 272px;
      --font-body: 'Satoshi', Inter, sans-serif;
      --font-display: 'Satoshi', Inter, sans-serif;
    }
    [data-theme="dark"] {
      --color-bg: #101114; --color-surface: #17181c; --color-surface-2: #1b1c20; --color-surface-offset: #21232a; --color-border: #2d3038; --color-divider:#25272d;
      --color-text: #f1f3f5; --color-text-muted: #b1b6bf; --color-text-faint: #80848d; --color-text-inverse: #141518;
      --color-primary: #f0f1f3; --color-primary-hover: #d7dbe0; --color-primary-highlight: #2a2d32;
      --color-danger: #ff7b7b; --color-danger-bg: rgba(197,57,57,.12); --color-success: #6ad29a; --color-success-bg: rgba(31,122,79,.16);
      --shadow-sm: 0 1px 2px rgba(0,0,0,.2); --shadow-md: 0 8px 22px rgba(0,0,0,.25); --shadow-lg: 0 20px 50px rgba(0,0,0,.32);
    }
    *,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%;overflow:hidden}
    body{font-family:var(--font-body);font-size:var(--text-base);background:var(--color-bg);color:var(--color-text);-webkit-font-smoothing:antialiased;text-rendering:optimizeLegibility}
    button,input,select,textarea{font:inherit;color:inherit}
    button{border:none;background:none;cursor:pointer}
    img,svg{display:block;max-width:100%}
    :focus-visible{outline:2px solid var(--color-primary);outline-offset:3px;border-radius:var(--radius-sm)}
    .app-shell{display:grid;grid-template-columns:var(--sidebar-w) 1fr;height:100dvh}
    .sidebar{background:var(--color-surface);border-right:1px solid var(--color-border);padding:var(--space-6);display:flex;flex-direction:column;gap:var(--space-6);min-width:0}
    .brand{display:flex;align-items:center;gap:var(--space-3)}
    .brand-mark{width:42px;height:42px;border-radius:12px;background:var(--color-primary);color:var(--color-text-inverse);display:grid;place-items:center;box-shadow:var(--shadow-sm)}
    .brand h1{font-size:var(--text-lg);line-height:1.1}
    .brand p{font-size:var(--text-xs);color:var(--color-text-muted);margin-top:2px}
    .nav{display:grid;gap:var(--space-2)}
    .nav-btn{display:flex;align-items:center;gap:var(--space-3);padding:.9rem 1rem;border-radius:var(--radius-md);font-size:var(--text-sm);font-weight:600;color:var(--color-text-muted);transition:all var(--transition)}
    .nav-btn:hover,.nav-btn.active{background:var(--color-primary);color:var(--color-text-inverse);transform:translateY(-1px)}
    .sidebar-footer{margin-top:auto;padding-top:var(--space-4);border-top:1px solid var(--color-divider);display:grid;gap:var(--space-3)}
    .ghost{display:flex;justify-content:space-between;align-items:center;padding:.9rem 1rem;border:1px solid var(--color-border);border-radius:var(--radius-md);background:var(--color-surface-2);transition:all var(--transition)}
    .ghost:hover{border-color:var(--color-text-faint);transform:translateY(-1px)}
    .content{display:grid;grid-template-rows:auto 1fr;min-width:0;overflow:hidden}
    .topbar{display:flex;align-items:center;justify-content:space-between;gap:var(--space-4);padding:var(--space-5) var(--space-6);border-bottom:1px solid var(--color-border);background:color-mix(in srgb, var(--color-surface) 92%, transparent);backdrop-filter: blur(10px)}
    .page-title h2{font-size:var(--text-xl);line-height:1.05}
    .page-title p{font-size:var(--text-sm);color:var(--color-text-muted);margin-top:4px}
    .toolbar{display:flex;gap:var(--space-3);align-items:center}
    .btn,.select{border:1px solid var(--color-border);background:var(--color-surface);padding:.85rem 1rem;border-radius:var(--radius-md);font-size:var(--text-sm);font-weight:700;transition:all var(--transition);min-height:44px}
    .btn.primary{background:var(--color-primary);color:var(--color-text-inverse);border-color:var(--color-primary)}
    .btn:hover,.select:hover{transform:translateY(-1px);box-shadow:var(--shadow-sm)}
    .main{overflow:auto;padding:var(--space-6);display:grid;gap:var(--space-6);content-visibility:auto}
    .loader-screen{position:fixed;inset:0;background:var(--color-bg);display:grid;place-items:center;z-index:30;transition:opacity .4s ease, visibility .4s ease}
    .loader-screen.hidden{opacity:0;visibility:hidden}
    .loader-box{display:grid;gap:var(--space-4);place-items:center}
    .spinner{width:52px;height:52px;border:4px solid var(--color-primary-highlight);border-top-color:var(--color-primary);border-radius:50%;animation:spin .9s linear infinite}
    @keyframes spin{to{transform:rotate(360deg)}}
    .stats{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:var(--space-4)}
    .card{background:var(--color-surface);border:1px solid var(--color-border);border-radius:var(--radius-lg);box-shadow:var(--shadow-sm)}
    .stat-card{padding:var(--space-5);display:grid;gap:var(--space-3)}
    .stat-card span{font-size:var(--text-xs);text-transform:uppercase;letter-spacing:.08em;color:var(--color-text-muted)}
    .stat-card strong{font-size:1.75rem;font-variant-numeric:tabular-nums lining-nums}
    .stat-row{display:flex;justify-content:space-between;gap:var(--space-3);align-items:flex-end}
    .badge{display:inline-flex;align-items:center;gap:6px;padding:.35rem .7rem;border-radius:var(--radius-full);font-size:var(--text-xs);font-weight:800}
    .badge.success{background:var(--color-success-bg);color:var(--color-success)}
    .badge.danger{background:var(--color-danger-bg);color:var(--color-danger)}
    .grid-2{display:grid;grid-template-columns:1.2fr .8fr;gap:var(--space-4)}
    .panel-head{padding:var(--space-5);display:flex;justify-content:space-between;align-items:center;gap:var(--space-4);border-bottom:1px solid var(--color-divider)}
    .panel-head h3{font-size:var(--text-lg)}
    .panel-head p{font-size:var(--text-sm);color:var(--color-text-muted);margin-top:2px}
    .panel-body{padding:var(--space-4)}
    .list{display:grid;gap:var(--space-3)}
    .list-item{display:grid;grid-template-columns:1fr auto;gap:var(--space-4);padding:var(--space-4);border:1px solid var(--color-border);border-radius:var(--radius-md);background:var(--color-surface-2);transition:all var(--transition)}
    .list-item:hover{transform:translateY(-1px);box-shadow:var(--shadow-sm)}
    .list-meta{display:flex;flex-wrap:wrap;gap:var(--space-3);font-size:var(--text-xs);color:var(--color-text-muted);margin-top:6px}
    .amount.in{color:var(--color-success);font-weight:800}
    .amount.out{color:var(--color-danger);font-weight:800}
    .page{display:none;gap:var(--space-6)}
    .page.active{display:grid}
    .table-wrap{overflow:auto}
    table{width:100%;border-collapse:collapse}
    th,td{text-align:left;padding:1rem;border-bottom:1px solid var(--color-divider);font-size:var(--text-sm)}
    th{color:var(--color-text-muted);font-size:var(--text-xs);text-transform:uppercase;letter-spacing:.08em}
    tr:hover td{background:color-mix(in srgb, var(--color-surface-2) 80%, var(--color-primary-highlight))}
    .action-row{display:flex;flex-wrap:wrap;gap:var(--space-2)}
    .mini-btn{padding:.65rem .85rem;border-radius:var(--radius-md);border:1px solid var(--color-border);background:var(--color-surface);font-size:var(--text-xs);font-weight:800;min-height:38px}
    .mini-btn.pay{background:var(--color-success);color:white;border-color:var(--color-success)}
    .mini-btn.delete{background:var(--color-danger);color:white;border-color:var(--color-danger)}
    .due-overdue{background:var(--color-danger-bg)!important}
    .form-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:var(--space-4)}
    .field{display:grid;gap:8px}
    .field label{font-size:var(--text-xs);font-weight:800;text-transform:uppercase;letter-spacing:.08em;color:var(--color-text-muted)}
    .input,.textarea{width:100%;min-height:46px;border:1px solid var(--color-border);border-radius:var(--radius-md);padding:.85rem 1rem;background:var(--color-surface-2)}
    .textarea{min-height:100px;resize:vertical}
    .auth{position:fixed;inset:0;background:linear-gradient(180deg,var(--color-bg),var(--color-surface-offset));display:grid;place-items:center;z-index:40;padding:var(--space-4)}
    .auth.hidden{display:none}
    .auth-card{width:min(460px,100%);background:var(--color-surface);border:1px solid var(--color-border);border-radius:var(--radius-xl);box-shadow:var(--shadow-lg);padding:var(--space-8);display:grid;gap:var(--space-5)}
    .hint{font-size:var(--text-sm);color:var(--color-text-muted)}
    .error{display:none;padding:.85rem 1rem;border-radius:var(--radius-md);background:var(--color-danger-bg);color:var(--color-danger);font-size:var(--text-sm);font-weight:700}
    .error.show{display:block}
    .modal{position:fixed;inset:0;background:rgba(10,10,10,.45);display:none;align-items:center;justify-content:center;z-index:35;padding:var(--space-4)}
    .modal.open{display:flex}
    .modal-card{width:min(720px,100%);background:var(--color-surface);border:1px solid var(--color-border);border-radius:var(--radius-xl);box-shadow:var(--shadow-lg);overflow:hidden}
    .modal-body{padding:var(--space-6);display:grid;gap:var(--space-4)}
    .kv{display:grid;grid-template-columns:180px 1fr;gap:var(--space-3);font-size:var(--text-sm)}
    .kv strong{color:var(--color-text-muted)}
    .hide-desktop{display:none}
    @media (max-width: 1024px){
      .app-shell{grid-template-columns:88px 1fr}
      .sidebar{padding:var(--space-5)}
      .brand h1,.brand p,.nav-btn span,.ghost span:last-child{display:none}
      .nav-btn,.ghost{justify-content:center;padding:.85rem}
      .stats{grid-template-columns:repeat(2,minmax(0,1fr))}
      .grid-2{grid-template-columns:1fr}
    }
    @media (max-width: 768px){
      html,body{overflow:auto}
      .app-shell{grid-template-columns:1fr;height:auto}
      .sidebar{display:none}
      .hide-desktop{display:inline-flex}
      .content{grid-template-rows:auto auto 1fr;overflow:visible}
      .topbar{position:sticky;top:0;z-index:10;flex-wrap:wrap;padding:var(--space-4)}
      .main{padding:var(--space-4)}
      .stats,.form-grid{grid-template-columns:1fr}
      .list-item{grid-template-columns:1fr}
      .kv{grid-template-columns:1fr}
    }
    @media (prefers-reduced-motion: reduce){*{animation:none!important;transition:none!important}}
  </style>
</head>
<body>
  <div class="loader-screen" id="loaderScreen" aria-live="polite">
    <div class="loader-box">
      <div class="spinner" aria-hidden="true"></div>
      <p class="hint">Carregando painel da academia...</p>
    </div>
  </div>

  <section class="auth" id="authScreen" aria-labelledby="loginTitle">
    <form class="auth-card" id="loginForm">
      <div class="brand">
        <div class="brand-mark" aria-hidden="true">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-label="Logo FitCore"><path d="M4 16l4-8 4 8 4-8 4 8"/><path d="M3 18h18"/></svg>
        </div>
        <div>
          <h2 id="loginTitle">Gestão de Academias</h2>
          <p>Acesso administrativo</p>
        </div>
      </div>
      <p class="hint">Use o login hardcoded solicitado: admin / admin</p>
      <div class="error" id="loginError">Login inválido. Use admin como usuário e senha.</div>
      <div class="field">
        <label for="username">Login</label>
        <input class="input" id="username" name="username" value="admin" autocomplete="username" />
      </div>
      <div class="field">
        <label for="password">Senha</label>
        <input class="input" id="password" name="password" type="password" value="admin" autocomplete="current-password" />
      </div>
      <button class="btn primary" type="submit">Entrar no sistema</button>
    </form>
  </section>

  <div class="app-shell" id="appShell" hidden>
    <aside class="sidebar">
      <div class="brand">
        <div class="brand-mark">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-label="Logo FitCore"><path d="M4 16l4-8 4 8 4-8 4 8"/><path d="M3 18h18"/></svg>
        </div>
        <div>
          <h1>FitCore</h1>
          <p>Dashboard profissional</p>
        </div>
      </div>

      <nav class="nav" aria-label="Menu principal">
        <button class="nav-btn active" data-page-target="dashboard"><span>Início / Lançamentos</span></button>
        <button class="nav-btn" data-page-target="relatorios"><span>Relatórios</span></button>
        <button class="nav-btn" data-page-target="alunos"><span>Alunos</span></button>
        <button class="nav-btn" data-page-target="mensalidades"><span>Mensalidades</span></button>
      </nav>

      <div class="sidebar-footer">
        <button class="ghost" id="themeToggle"><span>Tema</span><span>Claro / Escuro</span></button>
        <button class="ghost" id="logoutBtn"><span>Sair</span><span>Encerrar sessão</span></button>
      </div>
    </aside>

    <section class="content">
      <header class="topbar">
        <div class="page-title">
          <h2 id="pageHeading">Início / Lançamentos</h2>
          <p id="pageSubheading">Controle financeiro, alunos ativos e próximos vencimentos.</p>
        </div>
        <div class="toolbar">
          <button class="btn hide-desktop" id="mobileMenuBtn">Menu</button>
          <select class="select" id="periodFilter">
            <option>Últimos 30 dias</option>
            <option>Últimos 90 dias</option>
            <option>Último ano</option>
          </select>
          <button class="btn primary" id="quickAddBtn">Novo lançamento</button>
        </div>
      </header>

      <main class="main">
        <section class="page active" id="page-dashboard">
          <div class="stats" id="statsCards"></div>
          <div class="grid-2">
            <article class="card">
              <div class="panel-head">
                <div>
                  <h3>Lançamentos recentes</h3>
                  <p>Entradas e saídas mais recentes</p>
                </div>
                <button class="btn" data-page-target="relatorios">Ver relatórios</button>
              </div>
              <div class="panel-body">
                <div class="list" id="recentTransactions"></div>
              </div>
            </article>
            <article class="card">
              <div class="panel-head">
                <div>
                  <h3>Próximas mensalidades</h3>
                  <p>Ordenadas por vencimento</p>
                </div>
                <button class="btn" data-page-target="mensalidades">Gerenciar</button>
              </div>
              <div class="panel-body">
                <div class="list" id="upcomingFees"></div>
              </div>
            </article>
          </div>
        </section>

        <section class="page" id="page-relatorios">
          <article class="card">
            <div class="panel-head">
              <div>
                <h3>Relatórios financeiros</h3>
                <p>Clique em um item para abrir o modal com detalhes completos.</p>
              </div>
            </div>
            <div class="panel-body table-wrap">
              <table>
                <thead>
                  <tr>
                    <th>Data</th>
                    <th>Tipo</th>
                    <th>Descrição</th>
                    <th>Categoria</th>
                    <th>Valor</th>
                  </tr>
                </thead>
                <tbody id="reportTableBody"></tbody>
              </table>
            </div>
          </article>
        </section>

        <section class="page" id="page-alunos">
          <div class="grid-2">
            <article class="card">
              <div class="panel-head">
                <div>
                  <h3>Novo aluno</h3>
                  <p>Cadastro e gerenciamento básico</p>
                </div>
              </div>
              <div class="panel-body">
                <form id="studentForm" class="form-grid">
                  <div class="field"><label for="studentName">Nome completo</label><input class="input" id="studentName" required /></div>
                  <div class="field"><label for="studentPlan">Plano</label><input class="input" id="studentPlan" placeholder="Mensal, trimestral..." required /></div>
                  <div class="field"><label for="studentPhone">Telefone</label><input class="input" id="studentPhone" required /></div>
                  <div class="field"><label for="studentStatus">Status</label><select class="input" id="studentStatus"><option>Ativo</option><option>Inativo</option><option>Pendente</option></select></div>
                  <div class="field" style="grid-column:1/-1"><label for="studentNotes">Observações</label><textarea class="textarea" id="studentNotes"></textarea></div>
                  <button class="btn primary" type="submit" style="grid-column:1/-1">Salvar aluno</button>
                </form>
              </div>
            </article>
            <article class="card">
              <div class="panel-head">
                <div>
                  <h3>Lista de alunos</h3>
                  <p>Gerencie os alunos cadastrados</p>
                </div>
              </div>
              <div class="panel-body">
                <div class="list" id="studentsList"></div>
              </div>
            </article>
          </div>
        </section>

        <section class="page" id="page-mensalidades">
          <article class="card">
            <div class="panel-head">
              <div>
                <h3>Mensalidades</h3>
                <p>Vencimentos mais próximos no topo, vencidas em vermelho.</p>
              </div>
            </div>
            <div class="panel-body">
              <div class="list" id="feesList"></div>
            </div>
          </article>
        </section>
      </main>
    </section>
  </div>

  <div class="modal" id="detailModal" aria-hidden="true">
    <div class="modal-card">
      <div class="panel-head">
        <div>
          <h3>Detalhes do lançamento</h3>
          <p>Informações completas do registro selecionado</p>
        </div>
        <button class="btn" id="closeModalBtn">Fechar</button>
      </div>
      <div class="modal-body" id="modalContent"></div>
    </div>
  </div>

<script>
const HARDCODED_AUTH = { login: 'admin', password: 'admin' };
const state = { loggedIn: false, theme: matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light', activePage: 'dashboard', db: null };
const els = {
  authScreen: document.getElementById('authScreen'), appShell: document.getElementById('appShell'), loginForm: document.getElementById('loginForm'), loginError: document.getElementById('loginError'),
  loaderScreen: document.getElementById('loaderScreen'), statsCards: document.getElementById('statsCards'), recentTransactions: document.getElementById('recentTransactions'), upcomingFees: document.getElementById('upcomingFees'),
  reportTableBody: document.getElementById('reportTableBody'), studentsList: document.getElementById('studentsList'), feesList: document.getElementById('feesList'),
  pageHeading: document.getElementById('pageHeading'), pageSubheading: document.getElementById('pageSubheading'), detailModal: document.getElementById('detailModal'), modalContent: document.getElementById('modalContent'), themeToggle: document.getElementById('themeToggle')
};
const pageMeta = {
  dashboard: ['Início / Lançamentos','Controle financeiro, alunos ativos e próximos vencimentos.'],
  relatorios: ['Relatórios','Lista de entradas e saídas com visualização detalhada.'],
  alunos: ['Alunos','Cadastre e gerencie alunos da academia.'],
  mensalidades: ['Mensalidades','Controle vencimentos, pagamentos e ações rápidas.']
};
const fmtMoney = v => v.toLocaleString('pt-BR',{style:'currency',currency:'BRL'});
const fmtDate = d => new Date(d+'T12:00:00').toLocaleDateString('pt-BR');
const daysUntil = d => Math.ceil((new Date(d+'T12:00:00') - new Date()) / 86400000);

async function loadDb(){ const res = await fetch('./db.json'); state.db = await res.json(); renderAll(); }
function setTheme(theme){ state.theme = theme; document.documentElement.setAttribute('data-theme', theme); }
function showLoader(ms=900){ els.loaderScreen.classList.remove('hidden'); setTimeout(()=>els.loaderScreen.classList.add('hidden'), ms); }
function calcStats(){
  const tx = state.db.transactions;
  const income = tx.filter(t=>t.type==='entrada').reduce((a,b)=>a+b.amount,0);
  const expense = tx.filter(t=>t.type==='saida').reduce((a,b)=>a+b.amount,0);
  const activeStudents = state.db.students.filter(s=>s.status==='Ativo').length;
  const overdue = state.db.memberships.filter(m=>daysUntil(m.dueDate) < 0 && !m.paid).length;
  return [
    {label:'Entradas',value:fmtMoney(income),badge:'Receita',class:'success'},
    {label:'Saídas',value:fmtMoney(expense),badge:'Custos',class:'danger'},
    {label:'Alunos ativos',value:String(activeStudents),badge:'Ativos',class:'success'},
    {label:'Mensalidades vencidas',value:String(overdue),badge:'Atenção',class: overdue ? 'danger':'success'}
  ];
}
function renderStats(){
  els.statsCards.innerHTML = calcStats().map(card => `
    <article class="card stat-card">
      <span>${card.label}</span>
      <div class="stat-row"><strong>${card.value}</strong><small class="badge ${card.class}">${card.badge}</small></div>
    </article>`).join('');
}
function renderRecentTransactions(){
  const items = [...state.db.transactions].sort((a,b)=> new Date(b.date)-new Date(a.date)).slice(0,5);
  els.recentTransactions.innerHTML = items.map(item => `
    <button class="list-item" onclick="openTransaction('${item.id}')">
      <div>
        <strong>${item.description}</strong>
        <div class="list-meta"><span>${fmtDate(item.date)}</span><span>${item.category}</span><span>${item.note}</span></div>
      </div>
      <div class="amount ${item.type === 'entrada' ? 'in':'out'}">${item.type === 'entrada' ? '+' : '-'} ${fmtMoney(item.amount)}</div>
    </button>`).join('');
}
function renderUpcomingFees(){
  const items = [...state.db.memberships].sort((a,b)=>new Date(a.dueDate)-new Date(b.dueDate)).slice(0,5);
  els.upcomingFees.innerHTML = items.map(item => {
    const due = daysUntil(item.dueDate); const overdue = due < 0 && !item.paid;
    return `<div class="list-item ${overdue ? 'due-overdue':''}">
      <div><strong>${item.studentName}</strong><div class="list-meta"><span>Vence: ${fmtDate(item.dueDate)}</span><span>${item.plan}</span><span>${item.paid ? 'Pago' : overdue ? 'Vencida' : 'Em aberto'}</span></div></div>
      <div class="amount ${item.paid ? 'in' : overdue ? 'out' : ''}">${fmtMoney(item.amount)}</div>
    </div>`;
  }).join('');
}
function renderReports(){
  const items = [...state.db.transactions].sort((a,b)=>new Date(b.date)-new Date(a.date));
  els.reportTableBody.innerHTML = items.map(item=>`
    <tr role="button" tabindex="0" onclick="openTransaction('${item.id}')" onkeydown="if(event.key==='Enter'||event.key===' '){event.preventDefault();openTransaction('${item.id}')}" >
      <td>${fmtDate(item.date)}</td><td>${item.type}</td><td>${item.description}</td><td>${item.category}</td><td class="amount ${item.type==='entrada'?'in':'out'}">${item.type==='entrada'?'+':'-'} ${fmtMoney(item.amount)}</td>
    </tr>`).join('');
}
function renderStudents(){
  els.studentsList.innerHTML = state.db.students.map(student => `
    <div class="list-item">
      <div>
        <strong>${student.name}</strong>
        <div class="list-meta"><span>${student.plan}</span><span>${student.phone}</span><span>${student.status}</span></div>
      </div>
      <div class="action-row"><button class="mini-btn">Editar</button><button class="mini-btn delete" onclick="deleteStudent('${student.id}')">Excluir</button></div>
    </div>`).join('');
}
function renderFees(){
  const items = [...state.db.memberships].sort((a,b)=>new Date(a.dueDate)-new Date(b.dueDate));
  els.feesList.innerHTML = items.map(item => {
    const overdue = daysUntil(item.dueDate) < 0 && !item.paid;
    return `<div class="list-item ${overdue ? 'due-overdue':''}">
      <div>
        <strong>${item.studentName}</strong>
        <div class="list-meta"><span>Plano: ${item.plan}</span><span>Vencimento: ${fmtDate(item.dueDate)}</span><span>${item.paid ? 'Pago' : overdue ? 'Vencida' : 'Em aberto'}</span></div>
      </div>
      <div class="action-row">
        <button class="mini-btn">Editar dados</button>
        <button class="mini-btn delete" onclick="deleteMembership('${item.id}')">Excluir</button>
        <button class="mini-btn pay" onclick="markAsPaid('${item.id}','30d')">Pagar 30d</button>
        <button class="mini-btn pay" onclick="markAsPaid('${item.id}','90d')">Pagar 90d</button>
        <button class="mini-btn pay" onclick="markAsPaid('${item.id}','1ano')">Pagar 1 ano</button>
        <button class="mini-btn" onclick="markAsPaid('${item.id}','custom')">Personalizado</button>
      </div>
    </div>`;
  }).join('');
}
function renderAll(){ renderStats(); renderRecentTransactions(); renderUpcomingFees(); renderReports(); renderStudents(); renderFees(); }
function switchPage(target){
  state.activePage = target;
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('page-'+target).classList.add('active');
  document.querySelectorAll(`[data-page-target="${target}"]`).forEach(btn=>btn.classList.add('active'));
  els.pageHeading.textContent = pageMeta[target][0]; els.pageSubheading.textContent = pageMeta[target][1];
  showLoader(450);
}
function openTransaction(id){
  const item = state.db.transactions.find(t=>t.id===id); if(!item) return;
  els.modalContent.innerHTML = `
    <div class="kv"><strong>ID</strong><span>${item.id}</span></div>
    <div class="kv"><strong>Tipo</strong><span>${item.type}</span></div>
    <div class="kv"><strong>Descrição</strong><span>${item.description}</span></div>
    <div class="kv"><strong>Categoria</strong><span>${item.category}</span></div>
    <div class="kv"><strong>Data</strong><span>${fmtDate(item.date)}</span></div>
    <div class="kv"><strong>Valor</strong><span>${fmtMoney(item.amount)}</span></div>
    <div class="kv"><strong>Forma de pagamento</strong><span>${item.paymentMethod}</span></div>
    <div class="kv"><strong>Observações</strong><span>${item.note}</span></div>`;
  els.detailModal.classList.add('open');
}
function closeModal(){ els.detailModal.classList.remove('open'); }
function deleteStudent(id){ state.db.students = state.db.students.filter(s=>s.id!==id); renderStudents(); renderStats(); }
function deleteMembership(id){ state.db.memberships = state.db.memberships.filter(m=>m.id!==id); renderFees(); renderUpcomingFees(); renderStats(); }
function markAsPaid(id, period){
  const item = state.db.memberships.find(m=>m.id===id); if(!item) return;
  let days = 30; if(period==='90d') days = 90; if(period==='1ano') days = 365; if(period==='custom'){ const input = prompt('Informe a quantidade de dias para o próximo vencimento:', '45'); const parsed = Number(input); if(!parsed || parsed < 1) return; days = parsed; }
  const base = new Date(); base.setDate(base.getDate() + days);
  item.paid = true; item.lastPayment = new Date().toISOString().slice(0,10); item.dueDate = base.toISOString().slice(0,10);
  renderFees(); renderUpcomingFees(); renderStats();
}

els.loginForm.addEventListener('submit', async (e)=>{
  e.preventDefault();
  const user = e.target.username.value.trim(); const pass = e.target.password.value.trim();
  if(user === HARDCODED_AUTH.login && pass === HARDCODED_AUTH.password){
    els.loginError.classList.remove('show'); state.loggedIn = true; els.authScreen.classList.add('hidden'); els.appShell.hidden = false; setTheme(state.theme); showLoader(1000); if(!state.db) await loadDb();
  } else { els.loginError.classList.add('show'); }
});
document.querySelectorAll('[data-page-target]').forEach(btn=>btn.addEventListener('click',()=>switchPage(btn.dataset.pageTarget)));
document.getElementById('closeModalBtn').addEventListener('click', closeModal);
els.detailModal.addEventListener('click',e=>{ if(e.target===els.detailModal) closeModal(); });
document.getElementById('themeToggle').addEventListener('click',()=>setTheme(state.theme = state.theme==='dark'?'light':'dark'));
document.getElementById('logoutBtn').addEventListener('click',()=>{ state.loggedIn=false; els.appShell.hidden=true; els.authScreen.classList.remove('hidden'); });
document.getElementById('studentForm').addEventListener('submit',(e)=>{
  e.preventDefault();
  const student = { id: 'stu-'+crypto.randomUUID().slice(0,8), name: studentName.value, plan: studentPlan.value, phone: studentPhone.value, status: studentStatus.value, notes: studentNotes.value };
  state.db.students.unshift(student); e.target.reset(); renderStudents(); renderStats(); switchPage('alunos');
});
document.getElementById('quickAddBtn').addEventListener('click',()=>switchPage('dashboard'));
document.getElementById('mobileMenuBtn').addEventListener('click',()=>alert('No mobile, use a versão desktop expandida ou adapte este botão para um drawer.'));
window.openTransaction = openTransaction; window.deleteStudent = deleteStudent; window.deleteMembership = deleteMembership; window.markAsPaid = markAsPaid;
setTheme(state.theme);
showLoader(1200);
</script>
</body>
</html>

