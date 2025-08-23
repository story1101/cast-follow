<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>キャスト一括フォロー</title>
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
        
        .stats {
            text-align: center;
            color: #666;
            margin-bottom: 20px;
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
    <div class="container">
        <div class="header">
            <h1>🌟 キャスト一括フォロー</h1>
            <p>お気に入りのキャストをフォローして最新情報をチェック！</p>
        </div>
        
        <div class="instructions">
            <h3>📋 使い方</h3>
            <ul>
                <li>各キャストのフォローボタンをクリックするとXの公式フォロー画面に移動します</li>
                <li>「一括フォロー（新しいタブで開く）」ボタンで複数のフォロー画面を同時に開けます</li>
                <li>すべて安全なX公式機能を使用しています</li>
            </ul>
        </div>
        
        <div class="stats">
            <strong>総キャスト数: 16名</strong>
        </div>
        
        <div class="bulk-actions">
            <button class="bulk-follow-btn" onclick="openAllFollowPages()">
                🚀 一括フォロー（新しいタブで開く）
            </button>
            <button class="bulk-follow-btn" onclick="openRandomFollow()">
                🎲 ランダム5人フォロー
            </button>
        </div>
        
        <div class="follow-grid">
            <div class="cast-card">
                <div class="cast-name">ちひろ</div>
                <div class="username">@chihiro20230901</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=chihiro20230901" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">うさ</div>
                <div class="username">@usa__Story3</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=usa__Story3" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">くろ</div>
                <div class="username">@kuro_story012</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=kuro_story012" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.70-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">ゆうと</div>
                <div class="username">@yuto__Story</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=yuto__Story" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">かいと</div>
                <div class="username">@kaito__Story</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=kaito__Story" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">たける</div>
                <div class="username">@takeru_story001</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=takeru_story001" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">じん</div>
                <div class="username">@jin_story2</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=jin_story2" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">なぎ</div>
                <div class="username">@nagi__Story</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=nagi__Story" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">ゆずる</div>
                <div class="username">@yuzuru_story66</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=yuzuru_story66" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">ひびき</div>
                <div class="username">@hibiki__Story</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=hibiki__Story" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">もがみ</div>
                <div class="username">@mogami_story01</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=mogami_story01" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">とし</div>
                <div class="username">@toshi_Story</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=toshi_Story" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">やまと</div>
                <div class="username">@yamato_Story</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=yamato_Story" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">ちひろサブ</div>
                <div class="username">@chihirosabu1101</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=chihirosabu1101" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
            
            <div class="cast-card">
                <div class="cast-name">みずき</div>
                <div class="username">@mizuki___Story</div>
                <div class="follow-button-container">
                    <a href="https://twitter.com/intent/follow?screen_name=mizuki___Story" 
                       class="custom-follow-btn" target="_blank">
                        <svg class="twitter-icon" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.170-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                        </svg>
                        フォロー
                    </a>
                </div>
            </div>
        </div>
        
        <div style="text-align: center; margin-top: 40px; padding: 20px; background: #f8f9fa; border-radius: 10px;">
            <h3 style="color: #333; margin-bottom: 15px;">🎯 埋め込み用コード</h3>
            <p style="color: #666; margin-bottom: 15px;">このページを他のサイトに埋め込む場合は、以下のコードを使用してください：</p>
            <textarea readonly style="width: 100%; height: 60px; padding: 10px; border: 1px solid #ddd; border-radius: 5px; font-family: monospace; background: white;">
&lt;iframe src="このページのURL" width="100%" height="800" frameborder="0"&gt;&lt;/iframe&gt;
            </textarea>
        </div>
    </div>
    
    <script>
        // 全員のフォローページを一度に開く
        function openAllFollowPages() {
            const usernames = [
                'chihiro20230901', 'usa__Story3', 'kuro_story012', 'yuto__Story',
                'kaito__Story', 'takeru_story001', 'jin_story2', 'nagi__Story',
                'yuzuru_story66', 'hibiki__Story', 'mogami_story01', 'toshi_Story',
                'yamato_Story', 'chihirosabu1101', 'mizuki___Story'
            ];
            
            if (confirm(`${usernames.length}個のフォローページを新しいタブで開きます。よろしいですか？`)) {
                usernames.forEach((username, index) => {
                    setTimeout(() => {
                        window.open(`https://twitter.com/intent/follow?screen_name=${username}`, '_blank');
                    }, index * 500); // 0.5秒間隔で開く
                });
            }
        }
        
        // ランダム5人のフォローページを開く
        function openRandomFollow() {
            const usernames = [
                'chihiro20230901', 'usa__Story3', 'kuro_story012', 'yuto__Story',
                'kaito__Story', 'takeru_story001', 'jin_story2', 'nagi__Story',
                'yuzuru_story66', 'hibiki__Story', 'mogami_story01', 'toshi_Story',
                'yamato_Story', 'chihirosabu1101', 'mizuki___Story'
            ];
            
            // ランダムに5人選択
            const shuffled = usernames.sort(() => 0.5 - Math.random());
            const selected = shuffled.slice(0, 5);
            
            if (confirm(`ランダムに選ばれた${selected.length}人のフォローページを開きます。よろしいですか？`)) {
                selected.forEach((username, index) => {
                    setTimeout(() => {
                        window.open(`https://twitter.com/intent/follow?screen_name=${username}`, '_blank');
                    }, index * 500);
                });
            }
        }
        
        // ページ読み込み時のアニメーション
        document.addEventListener('DOMContentLoaded', function() {
            const cards = document.querySelectorAll('.cast-card');
            cards.forEach((card, index) => {
                setTimeout(() => {
                    card.style.opacity = '1';
                    card.style.transform = 'translateY(0)';
                }, index * 50);
            });
        });
        
        // 初期状態でカードを非表示に
        const style = document.createElement('style');
        style.textContent = `
            .cast-card {
                opacity: 0;
                transform: translateY(20px);
                transition: all 0.3s ease;
            }
        `;
        document.head.appendChild(style);
    </script>
</body>
</html>
