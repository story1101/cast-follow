<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>キャスト一括フォロー - 自動更新版</title>
    <style>
        body {
            font-family: 'Helvetica Neue', Arial, sans-serif;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }
        
        .container {
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }
        
        .header {
            text-align: center;
            margin-bottom: 40px;
        }
        
        .header h1 {
            color: #1da1f2;
            font-size: 2.5rem;
            margin-bottom: 10px;
            font-weight: 700;
        }
        
        .header p {
            color: #666;
            font-size: 1.1rem;
        }
        
        .follow-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }
        
        .cast-card {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            transition: transform 0.2s, box-shadow 0.2s;
            border: 2px solid transparent;
        }
        
        .cast-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            border-color: #1da1f2;
        }
        
        .cast-name {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 10px;
            color: #333;
        }
        
        .username {
            color: #666;
            margin-bottom: 15px;
            font-family: monospace;
        }
        
        .follow-button-container {
            display: flex;
            justify-content: center;
            align-items: center;
        }
        
        .custom-follow-btn {
            background: #1da1f2;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 25px;
            font-size: 14px;
            font-weight: 600;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            transition: background-color 0.2s;
            cursor: pointer;
        }
        
        .custom-follow-btn:hover {
            background: #0d8bd9;
            text-decoration: none;
            color: white;
        }
        
        .twitter-icon {
            width: 16px;
            height: 16px;
        }
        
        .bulk-actions {
            text-align: center;
            padding: 30px;
            background: #f1f3f4;
            border-radius: 15px;
            margin-bottom: 30px;
        }
        
        .bulk-follow-btn {
            background: linear-gradient(45deg, #1da1f2, #0d8bd9);
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 30px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: transform 0.2s;
            margin: 10px;
        }
        
        .bulk-follow-btn:hover {
            transform: scale(1.05);
        }
        
        .instructions {
            background: #e3f2fd;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 30px;
        }
        
        .instructions h3 {
            color: #1976d2;
            margin-bottom: 15px;
        }

        .management-info {
            background: #d1ecf1;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 30px;
            border-left: 4px solid #bee5eb;
        }

        .management-info h3 {
            color: #0c5460;
            margin-bottom: 15px;
        }

        .sheets-link {
            background: #28a745;
            color: white;
            padding: 10px 20px;
            text-decoration: none;
            border-radius: 5px;
            display: inline-block;
            margin-top: 10px;
        }

        .sheets-link:hover {
            background: #218838;
            text-decoration: none;
            color: white;
        }
        
        .stats {
            text-align: center;
            color: #666;
            margin-bottom: 20px;
        }

        .loading {
            text-align: center;
            padding: 40px;
            color: #666;
            font-size: 1.1rem;
        }

        .error {
            background: #f8d7da;
            color: #721c24;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 30px;
            text-align: center;
        }

        .last-updated {
            text-align: center;
            color: #999;
            font-size: 0.9rem;
            margin-top: 20px;
            font-style: italic;
        }

        .refresh-btn {
            background: #6c757d;
            color: white;
            padding: 8px 16px;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            font-size: 14px;
            margin-left: 10px;
        }

        .refresh-btn:hover {
            background: #5a6268;
        }
        
        @media (max-width: 600px) {
            .follow-grid {
                grid-template-columns: 1fr;
            }
            
            .header h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
   <body> 
       <div class="bulk-actions" id="bulkActions" style="display: none;">
            <button class="bulk-follow-btn" onclick="openAllFollowPages()">
                🚀 一括フォロー（新しいタブで開く）
            </button>
            <button class="bulk-follow-btn" onclick="openRandomFollow()">
                🎲 ランダム5人フォロー
            </button>
        </div>
        
        <div class="follow-grid" id="followGrid">
            </div>

        <div class="last-updated" id="lastUpdated" style="display: none;">
            最終更新: <span id="updateTime"></span>
        </div>
        
        <div style="text-align: center; margin-top: 40px; padding: 20px; background: #f8f9fa; border-radius: 10px;">
            <h3 style="color: #333; margin-bottom: 15px;">🎯 埋め込み用コード</h3>
            <p style="color: #666; margin-bottom: 15px;">このページを他のサイトに埋め込む場合は、以下のコードを使用してください：</p>
            <textarea readonly style="width: 100%; height: 60px; padding: 10px; border: 1px solid #ddd; border-radius: 5px; font-family: monospace; background: white;">
&lt;iframe src="このページのURL" width="100%" height="800" frameborder="0"&gt;&lt;/iframe&gt;
            </textarea>
        </div>
    </div>
    <body>
    <div class="container">
        <div class="header">
            <h1>🌟 キャスト一括フォロー</h1>
            <p>お気に入りのキャストをフォローして最新情報をチェック！</p>
        </div>

        <div class="management-info">
            <h3>📊 自動更新システム</h3>
            <p>
                <strong>キャストの追加方法：</strong><br>
                下記のGoogle Sheetsに「名前」と「アカウント名」を追加するだけで、このページに自動で反映されます！
            </p>
            <a href="https://docs.google.com/spreadsheets/d/1J8v5iVOLX5erxUmcyt6TmlsIX-kEXVRBtb2PAt50XHM/edit" target="_blank" class="sheets-link">
                📝 キャスト管理シートを開く
            </a>
            <p style="margin-top: 15px; font-size: 0.9rem; color: #666;">
                ※ シートを編集できるのは管理者のみです。新しいキャストの追加依頼は管理者にお声かけください。
            </p>
        </div>
        
        <div class="instructions">
            <h3>📋 使い方</h3>
            <ul>
                <li>各キャストのフォローボタンをクリックするとXの公式フォロー画面に移動します</li>
                <li>「一括フォロー（新しいタブで開く）」ボタンで複数のフォロー画面を同時に開けます</li>
                <li>すべて安全なX公式機能を使用しています</li>
                <li>データは自動で最新状態に更新されます</li>
            </ul>
        </div>
        
        <div class="stats">
            <strong>総キャスト数: <span id="castCount">読み込み中...</span>名</strong>
            <button class="refresh-btn" onclick="refreshData()">🔄 最新データに更新</button>
        </div>

        <div id="errorMessage" class="error" style="display: none;">
            <h3>⚠️ データの読み込みに失敗しました</h3>
            <p>Google Sheetsが「ウェブに公開」されているか確認してください。またはネットワーク接続を確認してください。</p>
            <button class="refresh-btn" onclick="refreshData()">再試行</button>
        </div>

        <div id="loading" class="loading">
            <h3>📡 最新のキャストデータを読み込み中...</h3>
            <p>Google Sheetsから自動取得しています</p>
        </div>
        
    <script>
        let castList = [];

        // ★★★ ここにあなたのGoogle SheetsのIDを設定してください ★★★
        // 例: https://docs.google.com/spreadsheets/d/【このID部分】/edit
        const SHEET_ID = '1J8v5iVOLX5erxUmcyt6TmlsIX-kEXVRBtb2PAt50XHM';
        
        // ★★★ スプレッドシートのシート名が「キャスト一覧」であることを確認してください ★★★
        // もし違う名前にしている場合は、下のURLの「キャスト一覧」の部分を修正してください
        const SHEET_URL = `https://docs.google.com/spreadsheets/d/${SHEET_ID}/gviz/tq?tqx=out:json&sheet=キャスト一覧`;

        // TwitterアイコンのSVG
        const twitterIconSVG = `
            <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
            </svg>
        `;

        // Google Sheetsからデータを取得
        async function loadCastData() {
            try {
                showLoading();
                
                const response = await fetch(SHEET_URL);
                if (!response.ok) {
                    throw new Error(`HTTP error! status: ${response.status}`);
                }
                
                const text = await response.text();
                // Google Sheets APIのレスポンスはJSONP形式なので、JSON部分を抽出
                const jsonData = JSON.parse(text.substr(47).slice(0, -2));
                
                // データを配列に変換
                castList = [];
                if (jsonData.table && jsonData.table.rows) {
                    jsonData.table.rows.forEach(row => {
                        // A列(名前)とB列(ユーザー名)が存在することを確認
                        if (row.c && row.c[0] && row.c[1]) {
                            const name = row.c[0].v;
                            const username = row.c[1].v;
                            if (name && username) {
                                castList.push({ name, username });
                            }
                        }
                    });
                }
                
                // 最終更新時刻を設定
                const updateTime = new Date().toLocaleString('ja-JP');
                document.getElementById('updateTime').textContent = updateTime;
                document.getElementById('lastUpdated').style.display = 'block';
                
                hideLoading();
                renderCasts();
                showBulkActions();
                
            } catch (error) {
                console.error('キャストデータの読み込みに失敗しました:', error);
                hideLoading();
                showError();
                
                // エラー時に表示するフォールバック用のデータ
                castList = [
                    { name: 'ちひろ', username: 'chihiro20230901' },
                    { name: 'うさ', username: 'usa__Story3' },
                    { name: 'くろ', username: 'kuro_story012' },
                    { name: 'ゆうと', username: 'yuto__Story' },
                    { name: 'かいと', username: 'kaito__Story' },
                    { name: 'たける', username: 'takeru_story001' },
                    { name: 'じん', username: 'jin_story2' },
                    { name: 'なぎ', username: 'nagi__Story' },
                    { name: 'ゆずる', username: 'yuzuru_story66' },
                    { name: 'ひびき', username: 'hibiki__Story' },
                    { name: 'もがみ', username: 'mogami_story01' },
                    { name: 'とし', username: 'toshi_Story' },
                    { name: 'やまと', username: 'yamato_Story' },
                    { name: 'ちひろサブ', username: 'chihirosabu1101' },
                    { name: 'みずき', username: 'mizuki___Story' },
                    { name: 'さく', username: 'saku__Story' },
                    { name: 'じゅん', username: 'Jun_Story01' } 
                ];
                
                setTimeout(() => {
                    document.getElementById('errorMessage').style.display = 'none';
                    renderCasts();
                    showBulkActions();
                }, 2000);
            }
        }

        // データを手動で更新
        function refreshData() {
            loadCastData();
        }

        // キャストカードを生成する関数
        function createCastCard(cast) {
            return `
                <div class="cast-card">
                    <div class="cast-name">${cast.name}</div>
                    <div class="username">@${cast.username}</div>
                    <div class="follow-button-container">
                        <a href="https://twitter.com/intent/follow?screen_name=${cast.username}" 
                           class="custom-follow-btn" target="_blank">
                            ${twitterIconSVG}
                            フォロー
                        </a>
                    </div>
                </div>
            `;
        }

        // ページを再描画する関数
        function renderCasts() {
            const grid = document.getElementById('followGrid');
            const castCount = document.getElementById('castCount');
            
            grid.innerHTML = castList.map(cast => createCastCard(cast)).join('');
            castCount.textContent = castList.length;

            // カードを一枚ずつアニメーション表示
            const cards = document.querySelectorAll('.cast-card');
            cards.forEach((card, index) => {
                card.style.opacity = '0';
                card.style.transform = 'translateY(20px)';
                setTimeout(() => {
                    card.style.opacity = '1';
                    card.style.transform = 'translateY(0)';
                }, index * 50);
            });
        }

        // ローディング表示
        function showLoading() {
            document.getElementById('loading').style.display = 'block';
            document.getElementById('errorMessage').style.display = 'none';
        }

        // ローディング表示を隠す
        function hideLoading() {
            document.getElementById('loading').style.display = 'none';
        }

        // エラーメッセージを表示
        function showError() {
            document.getElementById('errorMessage').style.display = 'block';
            document.getElementById('castCount').textContent = 'エラー';
        }

        // バルクアクションボタンを表示
        function showBulkActions() {
            document.getElementById('bulkActions').style.display = 'block';
        }

        // 全員のフォローページを一度に開く
        function openAllFollowPages() {
            const usernames = castList.map(cast => cast.username);
            
            if (confirm(`${usernames.length}個のフォローページを新しいタブで開きます。よろしいですか？\n（ブラウザのポップアップブロックにご注意ください）`)) {
                usernames.forEach((username, index) => {
                    setTimeout(() => {
                        window.open(`https://twitter.com/intent/follow?screen_name=${username}`, '_blank');
                    }, index * 200); // 一度に開きすぎないように少しずつ遅延させる
                });
            }
        }
        
        // ランダム5人のフォローページを開く
        function openRandomFollow() {
            const usernames = castList.map(cast => cast.username);
            const count = Math.min(5, usernames.length);
            
            const shuffled = [...usernames].sort(() => 0.5 - Math.random());
            const selected = shuffled.slice(0, count);
            
            if (confirm(`ランダムに選ばれた${selected.length}人のフォローページを開きます。よろしいですか？`)) {
                selected.forEach((username, index) => {
                    setTimeout(() => {
                        window.open(`https://twitter.com/intent/follow?screen_name=${username}`, '_blank');
                    }, index * 200);
                });
            }
        }
        
        // 初期状態でカードを非表示にするスタイル
        const style = document.createElement('style');
        style.textContent = `
            .cast-card {
                opacity: 0;
                transform: translateY(20px);
                transition: all 0.3s ease;
            }
        `;
        document.head.appendChild(style);

        // ページ読み込み時にデータをロード
        document.addEventListener('DOMContentLoaded', function() {
            loadCastData();
            
            // 5分ごとに自動更新
            setInterval(loadCastData, 5 * 60 * 1000);
        });
    </script>
</body>
</html>
