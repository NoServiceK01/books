<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ライトノベルAI工房</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Serif+JP:wght@400;700&family=Noto+Sans+JP:wght@300;400;500&family=Shippori+Mincho+B1:wght@400;700&display=swap" rel="stylesheet">
<style>
:root {
  --ink: #1a1410;
  --ink-light: #4a3f35;
  --paper: #fdf8f0;
  --paper-warm: #f5ede0;
  --paper-aged: #e8dcc8;
  --gold: #c8963e;
  --gold-light: #e8b86d;
  --red-accent: #8b2020;
  --border: #c8b89a;
  --shadow: rgba(50,30,10,0.15);
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'Noto Sans JP', sans-serif;
  background: var(--paper);
  color: var(--ink);
  min-height: 100vh;
  background-image: 
    radial-gradient(ellipse at 20% 0%, rgba(200,150,62,0.08) 0%, transparent 60%),
    radial-gradient(ellipse at 80% 100%, rgba(139,32,32,0.06) 0%, transparent 60%);
}

/* ── ヘッダー ── */
header {
  background: var(--ink);
  padding: 1.2rem 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 3px solid var(--gold);
  position: sticky;
  top: 0;
  z-index: 100;
  box-shadow: 0 2px 12px rgba(0,0,0,0.4);
}

.logo {
  font-family: 'Shippori Mincho B1', serif;
  font-size: 1.5rem;
  color: var(--gold-light);
  letter-spacing: 0.12em;
  display: flex;
  align-items: center;
  gap: 0.6rem;
}

.logo-icon {
  width: 32px;
  height: 32px;
  border: 2px solid var(--gold);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 16px;
}

nav {
  display: flex;
  gap: 0.5rem;
}

.nav-btn {
  background: transparent;
  border: 1px solid rgba(200,150,62,0.4);
  color: #c8b89a;
  padding: 0.45rem 1rem;
  font-family: 'Noto Sans JP', sans-serif;
  font-size: 0.8rem;
  cursor: pointer;
  transition: all 0.2s;
  letter-spacing: 0.05em;
}

.nav-btn:hover, .nav-btn.active {
  background: var(--gold);
  color: var(--ink);
  border-color: var(--gold);
}

/* ── メインレイアウト ── */
main {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1.5rem;
  display: grid;
  grid-template-columns: 340px 1fr;
  gap: 2rem;
  min-height: calc(100vh - 70px);
}

/* ── サイドパネル ── */
.side-panel {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}

.panel-card {
  background: white;
  border: 1px solid var(--border);
  border-top: 3px solid var(--gold);
  padding: 1.2rem;
  box-shadow: 2px 2px 8px var(--shadow);
}

.panel-title {
  font-family: 'Shippori Mincho B1', serif;
  font-size: 0.9rem;
  color: var(--gold);
  letter-spacing: 0.1em;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.panel-title::before {
  content: '◆';
  font-size: 0.6rem;
}

label {
  display: block;
  font-size: 0.78rem;
  color: var(--ink-light);
  margin-bottom: 0.3rem;
  letter-spacing: 0.04em;
}

input[type="text"],
input[type="password"],
textarea,
select {
  width: 100%;
  padding: 0.6rem 0.75rem;
  border: 1px solid var(--border);
  background: var(--paper);
  font-family: 'Noto Sans JP', sans-serif;
  font-size: 0.85rem;
  color: var(--ink);
  outline: none;
  transition: border-color 0.2s;
  margin-bottom: 0.9rem;
}

input:focus, textarea:focus, select:focus {
  border-color: var(--gold);
}

textarea {
  resize: vertical;
  line-height: 1.6;
}

.field-row { display: grid; grid-template-columns: 1fr 1fr; gap: 0.6rem; }

/* ── ジャンルタグ ── */
.genre-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
  margin-bottom: 0.9rem;
}

.genre-tag {
  padding: 0.3rem 0.7rem;
  border: 1px solid var(--border);
  background: transparent;
  font-size: 0.75rem;
  cursor: pointer;
  transition: all 0.18s;
  font-family: 'Noto Sans JP', sans-serif;
  color: var(--ink-light);
  letter-spacing: 0.03em;
}

.genre-tag.selected {
  background: var(--ink);
  color: var(--gold-light);
  border-color: var(--ink);
}

/* ── ボタン ── */
.btn-primary {
  width: 100%;
  padding: 0.85rem;
  background: var(--ink);
  color: var(--gold-light);
  border: 2px solid var(--gold);
  font-family: 'Shippori Mincho B1', serif;
  font-size: 1rem;
  letter-spacing: 0.15em;
  cursor: pointer;
  transition: all 0.2s;
  position: relative;
  overflow: hidden;
}

.btn-primary:hover:not(:disabled) {
  background: var(--gold);
  color: var(--ink);
}

.btn-primary:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.btn-secondary {
  padding: 0.55rem 1rem;
  background: transparent;
  border: 1px solid var(--border);
  color: var(--ink-light);
  font-family: 'Noto Sans JP', sans-serif;
  font-size: 0.8rem;
  cursor: pointer;
  transition: all 0.18s;
}

.btn-secondary:hover { border-color: var(--gold); color: var(--gold); }

/* ── メインエリア ── */
.main-area { display: flex; flex-direction: column; gap: 1.5rem; }

/* ── タブ ── */
.tabs {
  display: flex;
  border-bottom: 2px solid var(--border);
  gap: 0;
}

.tab {
  padding: 0.7rem 1.5rem;
  background: transparent;
  border: none;
  border-bottom: 3px solid transparent;
  margin-bottom: -2px;
  font-family: 'Noto Sans JP', sans-serif;
  font-size: 0.85rem;
  color: var(--ink-light);
  cursor: pointer;
  letter-spacing: 0.05em;
  transition: all 0.2s;
}

.tab.active {
  color: var(--gold);
  border-bottom-color: var(--gold);
  font-weight: 500;
}

/* ── コンテンツエリア ── */
.content-area {
  background: white;
  border: 1px solid var(--border);
  min-height: 500px;
  position: relative;
  box-shadow: 2px 2px 8px var(--shadow);
}

/* ── プレースホルダー ── */
.placeholder {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 500px;
  gap: 1rem;
  color: var(--border);
}

.placeholder-icon {
  font-size: 3rem;
  opacity: 0.4;
}

.placeholder-text {
  font-family: 'Shippori Mincho B1', serif;
  font-size: 1rem;
  letter-spacing: 0.1em;
  color: #c8b89a;
}

/* ── ローディング ── */
.loading-overlay {
  position: absolute;
  inset: 0;
  background: rgba(253,248,240,0.92);
  display: none;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 1.5rem;
  z-index: 10;
}

.loading-overlay.active { display: flex; }

.loading-spinner {
  width: 48px;
  height: 48px;
  border: 3px solid var(--paper-aged);
  border-top-color: var(--gold);
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}

@keyframes spin { to { transform: rotate(360deg); } }

.loading-text {
  font-family: 'Shippori Mincho B1', serif;
  color: var(--gold);
  font-size: 1rem;
  letter-spacing: 0.15em;
}

.loading-progress {
  font-size: 0.8rem;
  color: var(--ink-light);
  letter-spacing: 0.05em;
}

/* ── 小説表示 ── */
.novel-view {
  display: none;
  padding: 2.5rem;
}

.novel-view.active { display: block; }

.novel-header {
  text-align: center;
  margin-bottom: 2.5rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid var(--border);
  position: relative;
}

.novel-header::after {
  content: '◆　◆　◆';
  position: absolute;
  bottom: -0.65rem;
  left: 50%;
  transform: translateX(-50%);
  background: white;
  padding: 0 1rem;
  font-size: 0.6rem;
  color: var(--gold);
  letter-spacing: 0.3em;
}

.novel-title {
  font-family: 'Shippori Mincho B1', serif;
  font-size: 2rem;
  color: var(--ink);
  letter-spacing: 0.1em;
  margin-bottom: 0.5rem;
  line-height: 1.4;
}

.novel-subtitle {
  font-size: 0.85rem;
  color: var(--ink-light);
  letter-spacing: 0.08em;
}

/* ── 挿絵 ── */
.illustration-wrap {
  text-align: center;
  margin: 2rem 0;
  padding: 1.5rem;
  background: var(--paper-warm);
  border: 1px solid var(--border);
  position: relative;
}

.illustration-wrap::before {
  content: '挿絵';
  position: absolute;
  top: -0.6rem;
  left: 50%;
  transform: translateX(-50%);
  background: white;
  padding: 0 0.8rem;
  font-family: 'Shippori Mincho B1', serif;
  font-size: 0.72rem;
  color: var(--gold);
  letter-spacing: 0.1em;
}

.illustration-wrap img {
  max-width: 100%;
  max-height: 380px;
  object-fit: contain;
  display: block;
  margin: 0 auto;
}

.illust-placeholder {
  height: 240px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.8rem;
  color: var(--border);
}

/* ── 本文 ── */
.novel-body {
  font-family: 'Noto Serif JP', serif;
  font-size: 1rem;
  line-height: 2;
  color: var(--ink);
  letter-spacing: 0.02em;
  text-align: justify;
}

.novel-body p {
  margin-bottom: 1.2em;
  text-indent: 1em;
}

.novel-body p:first-child { text-indent: 0; }

/* ── メタ情報 ── */
.novel-meta {
  display: flex;
  gap: 0.5rem;
  align-items: center;
  margin-top: 2.5rem;
  padding-top: 1.5rem;
  border-top: 1px solid var(--border);
  font-size: 0.78rem;
  color: var(--ink-light);
  flex-wrap: wrap;
}

.meta-badge {
  padding: 0.25rem 0.7rem;
  background: var(--paper-aged);
  border: 1px solid var(--border);
  font-size: 0.72rem;
  letter-spacing: 0.05em;
}

.novel-actions {
  display: flex;
  gap: 0.6rem;
  margin-top: 1rem;
  flex-wrap: wrap;
}

/* ── ライブラリ ── */
.library-view { display: none; padding: 1.5rem; }
.library-view.active { display: block; }

.library-empty {
  text-align: center;
  padding: 3rem;
  color: var(--border);
  font-family: 'Shippori Mincho B1', serif;
  letter-spacing: 0.1em;
}

.library-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1rem;
}

.story-card {
  border: 1px solid var(--border);
  padding: 1rem;
  background: var(--paper-warm);
  cursor: pointer;
  transition: all 0.2s;
  position: relative;
}

.story-card:hover {
  border-color: var(--gold);
  box-shadow: 2px 2px 8px var(--shadow);
  transform: translateY(-2px);
}

.story-card-title {
  font-family: 'Shippori Mincho B1', serif;
  font-size: 0.92rem;
  color: var(--ink);
  margin-bottom: 0.4rem;
  letter-spacing: 0.05em;
  line-height: 1.5;
}

.story-card-genre {
  font-size: 0.72rem;
  color: var(--gold);
  margin-bottom: 0.5rem;
}

.story-card-date {
  font-size: 0.7rem;
  color: var(--ink-light);
}

.story-card-delete {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  background: transparent;
  border: none;
  cursor: pointer;
  color: var(--border);
  font-size: 1rem;
  padding: 0.2rem;
  transition: color 0.2s;
}

.story-card-delete:hover { color: var(--red-accent); }

/* ── API設定 ── */
.api-note {
  font-size: 0.72rem;
  color: var(--ink-light);
  line-height: 1.6;
  padding: 0.6rem;
  background: var(--paper-warm);
  border-left: 2px solid var(--gold);
  margin-bottom: 0.9rem;
}

/* ── 文字数 ── */
.char-count {
  text-align: right;
  font-size: 0.72rem;
  color: var(--ink-light);
  margin-top: -0.6rem;
  margin-bottom: 0.9rem;
}

/* ── トースト ── */
.toast {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  background: var(--ink);
  color: var(--gold-light);
  padding: 0.8rem 1.4rem;
  border: 1px solid var(--gold);
  font-size: 0.85rem;
  letter-spacing: 0.05em;
  opacity: 0;
  transform: translateY(10px);
  transition: all 0.3s;
  z-index: 999;
  pointer-events: none;
}

.toast.show { opacity: 1; transform: translateY(0); }

/* ── レスポンシブ ── */
@media (max-width: 900px) {
  main { grid-template-columns: 1fr; }
}
</style>
</head>
<body>

<header>
  <div class="logo">
    <div class="logo-icon">📖</div>
    ライトノベルAI工房
  </div>
  <nav>
    <button class="nav-btn active" onclick="switchTab('editor')">執筆</button>
    <button class="nav-btn" onclick="switchTab('library')">書架</button>
  </nav>
</header>

<main>
  <!-- ── サイドパネル ── -->
  <aside class="side-panel">

    <!-- API設定 -->
    <div class="panel-card">
      <div class="panel-title">API設定</div>
      <div class="api-note">
        Anthropic APIキーを入力してください。<br>
        キーはブラウザ内のみで使用され、外部には送信されません。
      </div>
      <label>Anthropic APIキー</label>
      <input type="password" id="apiKey" placeholder="sk-ant-..." />
      <label>挿絵生成方法</label>
      <select id="imageMode">
        <option value="pollinations">無料（Pollinations AI）</option>
        <option value="none">なし</option>
      </select>
    </div>

    <!-- 作品設定 -->
    <div class="panel-card">
      <div class="panel-title">作品設定</div>

      <label>タイトル</label>
      <input type="text" id="storyTitle" placeholder="例：月光少女と迷宮の騎士" />

      <label>ジャンル</label>
      <div class="genre-tags" id="genreTags">
        <button class="genre-tag selected" onclick="toggleGenre(this,'異世界ファンタジー')">異世界ファンタジー</button>
        <button class="genre-tag" onclick="toggleGenre(this,'学園ロマンス')">学園ロマンス</button>
        <button class="genre-tag" onclick="toggleGenre(this,'魔法少女')">魔法少女</button>
        <button class="genre-tag" onclick="toggleGenre(this,'ダーク・ファンタジー')">ダーク・ファンタジー</button>
        <button class="genre-tag" onclick="toggleGenre(this,'SF')">SF</button>
        <button class="genre-tag" onclick="toggleGenre(this,'ミステリー')">ミステリー</button>
        <button class="genre-tag" onclick="toggleGenre(this,'ホラー')">ホラー</button>
        <button class="genre-tag" onclick="toggleGenre(this,'コメディ')">コメディ</button>
      </div>

      <div class="field-row">
        <div>
          <label>主人公名</label>
          <input type="text" id="protagonist" placeholder="例：天音あかり" />
        </div>
        <div>
          <label>相手役名</label>
          <input type="text" id="heroine" placeholder="例：リュシアン" />
        </div>
      </div>

      <label>あらすじ・設定メモ</label>
      <textarea id="synopsis" rows="4" placeholder="世界観、設定、登場人物の関係性など自由に記述してください..."></textarea>

      <label>執筆の指示</label>
      <textarea id="directive" rows="3" placeholder="例：緊張感ある戦闘シーンで始まり、主人公が覚醒する場面を含めてください"></textarea>
    </div>

    <button class="btn-primary" id="generateBtn" onclick="generate()">
      ✦ 物語を生成する ✦
    </button>

  </aside>

  <!-- ── メインエリア ── -->
  <section class="main-area" id="editorTab">

    <div class="tabs">
      <button class="tab active" onclick="switchContentTab('preview')">プレビュー</button>
      <button class="tab" onclick="switchContentTab('raw')">テキスト編集</button>
    </div>

    <div class="content-area">
      <!-- ローディング -->
      <div class="loading-overlay" id="loadingOverlay">
        <div class="loading-spinner"></div>
        <div class="loading-text" id="loadingText">物語を紡いでいます…</div>
        <div class="loading-progress" id="loadingProgress"></div>
      </div>

      <!-- プレースホルダー -->
      <div class="placeholder" id="placeholder">
        <div class="placeholder-icon">✦</div>
        <div class="placeholder-text">左のパネルで設定して生成ボタンを押してください</div>
      </div>

      <!-- プレビュー -->
      <div class="novel-view" id="previewView">
        <div class="novel-header">
          <div class="novel-title" id="viewTitle"></div>
          <div class="novel-subtitle" id="viewSubtitle"></div>
        </div>

        <div class="illustration-wrap" id="illustWrap">
          <div class="illust-placeholder" id="illustPlaceholder">
            <span style="font-size:2rem;opacity:0.3">🖼</span>
            <span style="font-size:0.8rem;letter-spacing:0.08em">挿絵を生成中…</span>
          </div>
          <img id="illustImg" src="" alt="挿絵" style="display:none" />
        </div>

        <div class="novel-body" id="viewBody"></div>

        <div class="novel-meta" id="viewMeta"></div>

        <div class="novel-actions">
          <button class="btn-secondary" onclick="saveStory()">📚 書架に保存</button>
          <button class="btn-secondary" onclick="downloadTxt()">💾 TXTで保存</button>
          <button class="btn-secondary" onclick="copyText()">📋 コピー</button>
        </div>
      </div>

      <!-- テキスト編集 -->
      <div style="display:none;padding:1.5rem;" id="rawView">
        <label>タイトル</label>
        <input type="text" id="rawTitle" style="margin-bottom:1rem" />
        <label>本文（自由に編集できます）</label>
        <textarea id="rawBody" rows="24" style="font-family:'Noto Serif JP',serif;line-height:2;font-size:0.92rem;"></textarea>
        <div class="char-count" id="rawCharCount">0 文字</div>
        <button class="btn-secondary" onclick="applyRaw()" style="margin-top:0.5rem">プレビューに反映</button>
      </div>
    </div>
  </section>

  <!-- ── 書架タブ ── -->
  <section class="main-area" id="libraryTab" style="display:none;grid-column:1/-1">
    <div class="content-area" style="min-height:400px">
      <div style="padding:1.5rem">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:1.2rem">
          <div style="font-family:'Shippori Mincho B1',serif;font-size:1.1rem;letter-spacing:0.1em;color:var(--gold)">◆ 保存した作品</div>
          <button class="btn-secondary" onclick="clearLibrary()" style="font-size:0.72rem">全て削除</button>
        </div>
        <div id="libraryContent"></div>
      </div>
    </div>
  </section>
</main>

<div class="toast" id="toast"></div>

<script>
// ── ステート ── //
let currentStory = null;
let selectedGenres = ['異世界ファンタジー'];
let activeContentTab = 'preview';

// ── タブ切替 ── //
function switchTab(tab) {
  document.querySelectorAll('.nav-btn').forEach((b,i)=>{
    b.classList.toggle('active', (i===0&&tab==='editor')||(i===1&&tab==='library'));
  });
  document.getElementById('editorTab').style.display = tab==='editor' ? '' : 'none';
  document.getElementById('libraryTab').style.display = tab==='library' ? '' : 'none';
  if(tab==='library') renderLibrary();
}

function switchContentTab(tab) {
  activeContentTab = tab;
  document.querySelectorAll('.tab').forEach((b,i)=>{
    b.classList.toggle('active',(i===0&&tab==='preview')||(i===1&&tab==='raw'));
  });
  document.getElementById('previewView').style.display = tab==='preview'&&currentStory?'block':'none';
  document.getElementById('rawView').style.display = tab==='raw'&&currentStory?'block':'none';
  if(tab==='raw'&&currentStory){
    document.getElementById('rawTitle').value = currentStory.title;
    document.getElementById('rawBody').value = currentStory.body;
    updateRawCount();
  }
}

// ── ジャンル ── //
function toggleGenre(el, genre) {
  el.classList.toggle('selected');
  if(el.classList.contains('selected')) {
    if(!selectedGenres.includes(genre)) selectedGenres.push(genre);
  } else {
    selectedGenres = selectedGenres.filter(g=>g!==genre);
  }
}

// ── 生成メイン ── //
async function generate() {
  const apiKey = document.getElementById('apiKey').value.trim();
  if(!apiKey) { toast('APIキーを入力してください'); return; }

  const title = document.getElementById('storyTitle').value.trim() || '無題の物語';
  const protagonist = document.getElementById('protagonist').value.trim() || '主人公';
  const heroine = document.getElementById('heroine').value.trim() || 'ヒロイン';
  const synopsis = document.getElementById('synopsis').value.trim();
  const directive = document.getElementById('directive').value.trim();
  const genres = selectedGenres.join('・') || 'ファンタジー';
  const imageMode = document.getElementById('imageMode').value;

  setLoading(true, '物語を紡いでいます…', '');
  document.getElementById('placeholder').style.display = 'none';
  document.getElementById('previewView').style.display = 'none';
  document.getElementById('rawView').style.display = 'none';

  try {
    // ── 小説生成 ── //
    setLoadingProgress('AIが執筆中…（しばらくお待ちください）');
    const body = await generateNovel(apiKey, {title, protagonist, heroine, synopsis, directive, genres});

    currentStory = {
      title,
      body,
      genres,
      protagonist,
      heroine,
      illustUrl: null,
      createdAt: new Date().toISOString()
    };

    renderPreview();
    setLoading(false);
    switchContentTab('preview');

    // ── 挿絵生成（非同期） ── //
    if(imageMode !== 'none') {
      generateIllustration(title, genres, protagonist, heroine, body);
    } else {
      document.getElementById('illustWrap').style.display = 'none';
    }

  } catch(e) {
    setLoading(false);
    toast('エラー: ' + e.message);
    document.getElementById('placeholder').style.display = 'flex';
  }
}

// ── Claude API呼び出し ── //
async function generateNovel(apiKey, params) {
  const {title, protagonist, heroine, synopsis, directive, genres} = params;
  const prompt = `あなたは才能あるライトノベル作家です。以下の設定で魅力的な物語を執筆してください。

【タイトル】${title}
【ジャンル】${genres}
【主人公】${protagonist}
【ヒロイン/相手役】${heroine}
${synopsis ? `【設定・あらすじ】\n${synopsis}` : ''}
${directive ? `【執筆の指示】\n${directive}` : ''}

要件：
- 日本語のライトノベルとして自然な文体で書いてください
- 約5000文字（4800〜5200文字）の短編小説を執筆してください
- 地の文と会話文をバランスよく使用してください
- 読者を引き込む冒頭、展開、山場、余韻ある結末を含めてください
- セリフは「」で、心理描写や情景描写を豊かに書いてください
- 段落は改行で区切ってください
- タイトルや章番号は書かず、本文のみ出力してください`;

  const resp = await fetch('https://api.anthropic.com/v1/messages', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'x-api-key': apiKey,
      'anthropic-version': '2023-06-01',
      'anthropic-dangerous-direct-browser-access': 'true'
    },
    body: JSON.stringify({
      model: 'claude-opus-4-5',
      max_tokens: 8000,
      messages: [{ role: 'user', content: prompt }]
    })
  });

  if(!resp.ok) {
    const err = await resp.json().catch(()=>({}));
    throw new Error(err.error?.message || `HTTP ${resp.status}`);
  }

  const data = await resp.json();
  return data.content[0].text;
}

// ── 挿絵生成（Pollinations AI） ── //
async function generateIllustration(title, genres, protagonist, heroine, bodyText) {
  try {
    const illustPrompt = buildIllustPrompt(title, genres, protagonist, heroine, bodyText);
    const encoded = encodeURIComponent(illustPrompt);
    const url = `https://image.pollinations.ai/prompt/${encoded}?width=768&height=512&nologo=true&model=flux`;

    document.getElementById('illustPlaceholder').innerHTML = `
      <div style="font-size:1.5rem;opacity:0.4">🖼</div>
      <div style="font-size:0.78rem;letter-spacing:0.08em">挿絵を生成中…</div>
    `;
    document.getElementById('illustWrap').style.display = '';
    document.getElementById('illustImg').style.display = 'none';

    const img = document.getElementById('illustImg');
    img.onload = () => {
      document.getElementById('illustPlaceholder').style.display = 'none';
      img.style.display = 'block';
      if(currentStory) currentStory.illustUrl = url;
    };
    img.onerror = () => {
      document.getElementById('illustPlaceholder').innerHTML = `<span style="font-size:0.78rem;opacity:0.5">挿絵の生成に失敗しました</span>`;
    };
    img.src = url;
  } catch(e) {
    console.warn('挿絵生成エラー', e);
  }
}

function buildIllustPrompt(title, genres, protagonist, heroine, body) {
  const genreMap = {
    '異世界ファンタジー': 'fantasy world, medieval castle, magic spell, dramatic lighting',
    '学園ロマンス': 'school uniform, cherry blossoms, classroom, soft sunlight',
    '魔法少女': 'magical girl, sparkles, colorful magic, transformation',
    'ダーク・ファンタジー': 'dark fantasy, ruins, mysterious atmosphere, moonlight',
    'SF': 'sci-fi, futuristic city, hologram, space',
    'ミステリー': 'mystery, candlelight, old library, shadows',
    'ホラー': 'horror atmosphere, dark forest, fog, eerie',
    'コメディ': 'lighthearted, bright colors, cheerful, anime style'
  };

  const genreHint = Object.entries(genreMap)
    .filter(([g])=>genres.includes(g))
    .map(([,v])=>v)
    .join(', ') || 'fantasy, dramatic';

  return `anime illustration, light novel cover art, ${genreHint}, beautiful character, cinematic composition, highly detailed, vibrant colors, professional illustration`;
}

// ── プレビュー描画 ── //
function renderPreview() {
  if(!currentStory) return;

  document.getElementById('viewTitle').textContent = currentStory.title;

  const charCount = currentStory.body.length;
  document.getElementById('viewSubtitle').textContent =
    `${currentStory.genres} ／ ${charCount.toLocaleString()} 文字`;

  const bodyEl = document.getElementById('viewBody');
  bodyEl.innerHTML = '';
  currentStory.body.split(/\n+/).filter(l=>l.trim()).forEach(line => {
    const p = document.createElement('p');
    p.textContent = line;
    bodyEl.appendChild(p);
  });

  const metaEl = document.getElementById('viewMeta');
  metaEl.innerHTML = `
    <span class="meta-badge">${currentStory.genres}</span>
    <span class="meta-badge">主人公：${currentStory.protagonist}</span>
    <span class="meta-badge">相手役：${currentStory.heroine}</span>
    <span style="margin-left:auto;font-size:0.72rem">${new Date(currentStory.createdAt).toLocaleDateString('ja-JP')}</span>
  `;

  document.getElementById('previewView').style.display = 'block';
}

// ── テキスト編集 ── //
function updateRawCount() {
  const len = document.getElementById('rawBody').value.length;
  document.getElementById('rawCharCount').textContent = `${len.toLocaleString()} 文字`;
}

document.addEventListener('DOMContentLoaded', ()=>{
  document.getElementById('rawBody').addEventListener('input', updateRawCount);
});

function applyRaw() {
  if(!currentStory) return;
  currentStory.title = document.getElementById('rawTitle').value;
  currentStory.body = document.getElementById('rawBody').value;
  switchContentTab('preview');
  toast('プレビューに反映しました');
}

// ── 保存・ダウンロード ── //
function saveStory() {
  if(!currentStory) return;
  const lib = getLibrary();
  const id = Date.now().toString();
  lib[id] = { ...currentStory };
  saveLibrary(lib);
  toast('書架に保存しました ✦');
}

function downloadTxt() {
  if(!currentStory) return;
  const text = `${currentStory.title}\n${'═'.repeat(40)}\n\nジャンル：${currentStory.genres}\n主人公：${currentStory.protagonist}\n相手役：${currentStory.heroine}\n執筆日：${new Date(currentStory.createdAt).toLocaleDateString('ja-JP')}\n\n${'━'.repeat(40)}\n\n${currentStory.body}`;
  const blob = new Blob([text], {type:'text/plain;charset=utf-8'});
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = `${currentStory.title}.txt`;
  a.click();
  toast('ダウンロードしました');
}

function copyText() {
  if(!currentStory) return;
  navigator.clipboard.writeText(currentStory.body).then(()=>toast('コピーしました'));
}

// ── ライブラリ ── //
function getLibrary() {
  try { return JSON.parse(localStorage.getItem('ranobeLib')||'{}'); } catch{ return {}; }
}
function saveLibrary(lib) {
  localStorage.setItem('ranobeLib', JSON.stringify(lib));
}

function renderLibrary() {
  const lib = getLibrary();
  const el = document.getElementById('libraryContent');
  const keys = Object.keys(lib).sort((a,b)=>b-a);

  if(!keys.length) {
    el.innerHTML = `<div class="library-empty">まだ保存された作品はありません</div>`;
    return;
  }

  el.innerHTML = `<div class="library-grid">${keys.map(id=>{
    const s = lib[id];
    return `<div class="story-card" onclick="loadStory('${id}')">
      <button class="story-card-delete" onclick="event.stopPropagation();deleteStory('${id}')">×</button>
      <div class="story-card-genre">${s.genres||'不明'}</div>
      <div class="story-card-title">${s.title}</div>
      <div class="story-card-date">${s.body.length.toLocaleString()}文字 ／ ${new Date(s.createdAt).toLocaleDateString('ja-JP')}</div>
    </div>`;
  }).join('')}</div>`;
}

function loadStory(id) {
  const lib = getLibrary();
  if(!lib[id]) return;
  currentStory = lib[id];
  switchTab('editor');
  renderPreview();

  if(currentStory.illustUrl) {
    document.getElementById('illustWrap').style.display = '';
    document.getElementById('illustPlaceholder').style.display = 'none';
    const img = document.getElementById('illustImg');
    img.src = currentStory.illustUrl;
    img.style.display = 'block';
  } else {
    document.getElementById('illustWrap').style.display = 'none';
  }

  document.getElementById('storyTitle').value = currentStory.title;
  toast(`「${currentStory.title}」を読み込みました`);
}

function deleteStory(id) {
  if(!confirm('この作品を削除しますか？')) return;
  const lib = getLibrary();
  delete lib[id];
  saveLibrary(lib);
  renderLibrary();
  toast('削除しました');
}

function clearLibrary() {
  if(!confirm('全ての保存作品を削除しますか？')) return;
  localStorage.removeItem('ranobeLib');
  renderLibrary();
  toast('書架を空にしました');
}

// ── ローディング ── //
function setLoading(on, text='', progress='') {
  const overlay = document.getElementById('loadingOverlay');
  overlay.classList.toggle('active', on);
  document.getElementById('loadingText').textContent = text;
  document.getElementById('loadingProgress').textContent = progress;
  document.getElementById('generateBtn').disabled = on;
}

function setLoadingProgress(text) {
  document.getElementById('loadingProgress').textContent = text;
}

// ── トースト ── //
function toast(msg) {
  const el = document.getElementById('toast');
  el.textContent = msg;
  el.classList.add('show');
  clearTimeout(el._t);
  el._t = setTimeout(()=>el.classList.remove('show'), 2800);
}
</script>
</body>
</html>
