# UUGaroon

Google Apps Script (GAS)とGaroonのREST APIを用いて、  
Garoon上のスケジュールを、設定した時間おきに、指定のGoogleカレンダーに同期する

## 免責事項・注意点
本スクリプトの実行・改変等に伴ういかなる不具合についても責任を負いかねます。  

REST APIの使用制限は
>1アプリに対するリクエスト数：10,000 リクエスト/日 まで  
>ドメインごとのAPIによる同時アクセス数：100 まで

となっており、これを超えると利用が制限される恐れがあります。

## 使用方法
[動画(音声なし)へのリンクはこちら(Youtubeが開きます)](https://www.youtube.com/watch?v=jitF2p7Y9mY)

1. 同期先のGmailアカウントにログインする  
2. 共有ファイル([Googleスプレッドシート](https://docs.google.com/spreadsheets/d/13tcD9HkP4nxWE6hjLcsEDYejW7Ym2Z-Idd6UZ7mfj40/edit?usp=sharing))にアクセスし、コピーを作成する
3. スプレッドシートの[ツール]から[スクリプトエディタ]を選択
    * スプレッドシートからスクリプトエディタを起動する際、デフォルトアカウントでないと、  
      *現在、ファイルを開くことができません。アドレスを確認して、もう一度試してください。*  
      というエラーが出ます。  
    * 複数アカウントを運用している場合は、対象とするカレンダーのアカウントをデフォルトアカウント(u/0)にしてください  
    * メインのアカウントと同期先としたいアカウントが別の場合、普段使っていないブラウザでデフォルトアカウントとしてログインして設定するのがおすすめです。  
    * 一部のブラウザでポップアップを許可しない設定の場合、スクリプトの実行ができない場合があります。  
4. [初回実行.gs]のユーザー名・パスワード、同期したいカレンダーの名前を編集し実行する
    * すでにある小カレンダーに同期したければ、CalendarName変数をそれに合わせて編集する
    * カレンダー名を編集しない場合、"Garoon"というカレンダーが新規作成されるので、実行後にGoogleカレンダー側で同期(表示)の設定を行う
5. 4.実行後に[メインコード.gs]のsyncGaroonSchedule関数が選択された状態で実行する
6. 5.がうまく行ったら、左側の時計マークから[トリガーを追加]し、  
   syncGaroonSchedule関数を一定の時間間隔で自動で実行するよう編集する
    * [イベントのソースを選択]→時間主導型
    * [時間ベースのトリガーのタイプを選択]→時間ベースのタイマー
    * 間隔を選択 →1-6時間 (長めを推奨とします)    
    * REST APIの同時接続はドメインごとに100が上限となっています。  
      **分ベースの同期は使用しないでください!!**
      > APIの利用制限について
      https://www.cybozu.com/jp/service/restrictions.html
    * GASの制限にも抵触する場合があります。
      https://developers.google.com/apps-script/guides/services/quotas
    * エラー通知設定→お好みで
7. 一度6.まで実行すれば(エラー等が出ない限り)再実行の必要はないはずです

## 問い合わせ
[Googleフォーム](https://docs.google.com/forms/d/e/1FAIpQLScVIvjqleax3_knxYJp63SmWvoxuhZ9rp308qFg9xV-HWwFKg/viewform?usp=sf_link)
* 学外からの問い合わせには対応しかねます
* 原則、個別の対応ではなくQ&Aの公開といった対応とさせて頂きます
* 逆(Googleカレンダー→Garoon)については、作成の予定はありません。

## 参考:  
 https://developer.cybozu.io/hc/ja/articles/360000577946-Garoon-REST-API-一覧  
 https://www.330k.info/essay/sync-garoon-google-calendar/  
