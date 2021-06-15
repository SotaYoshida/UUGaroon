# UUGaroon

Google Apps Script (GAS)を用いて、GaroonからGoogleカレンダーに同期を行う。

## 免責事項
本スクリプトの実行・改変等に伴ういかなる不具合についても責任を負いかねます。  

## 何ができるのか
設定した時間おきに、Garoon上の予定が指定したGoogleカレンダーに同期される  
手元のPCで24時間スクリプトを常駐させておく、といった手間は必要はない

## 使用方法

(末尾に動画があります)

1. 同期先のGmailアカウントにログインする  
2. 共有ファイル(Googleスプレッドシート)にアクセスし、コピーを作成する
3. スプレッドシートの[ツール]から[スクリプトエディタ]を選択
    * スプレッドシートからスクリプトエディタを起動する際、デフォルトアカウントでないと、  
      **現在、ファイルを開くことができません。アドレスを確認して、もう一度試してください。**  
      というエラーが出ます。  
    * 複数アカウントを運用している場合は、対象とするカレンダーのアカウントをデフォルトアカウント(u/0)にしてください  
    * メインのアカウントと同期先としたいアカウントが別の場合、普段使っていないブラウザでデフォルトアカウントとしてログインして設定するのがおすすめです。  
    * 一部のブラウザでポップアップを許可しない設定の場合、スクリプトの実行ができない場合があります。  
4. 初回実行.gsのユーザー名パスワード、同期したいカレンダーの名前を編集し実行する
    * すでにある小カレンダーに同期したければ、カレンダー名を編集する
    * カレンダー名を編集しない場合、"Garoon"というカレンダーが新規作成されるので、実行後にGoogleカレンダー側で同期(表示)の設定を行う
5. メインコード.gsのsyncGaroonScheduleが選択された状態で実行する
6. 4.5.がうまく行ったら、左側の時計マークから、[トリガーを追加]し、syncGaroonSchedule関数を一定の時間間隔で自動で実行するよう編集する
    * [イベントのソースを選択]→時間主導型
    * [時間ベースのトリガーのタイプを選択]→時間ベースのタイマー
    * 時間の感覚を選択 →1時間
    * 分ベースで同期させることもできますが、ゆとりのある設定にしましょう。GASの制限にも抵触する場合があります。
      https://developers.google.com/apps-script/guides/services/quotas
    * エラー通知設定→お好みで

[![](https://img.youtube.com/vi/jitF2p7Y9mY/0.jpg)](https://www.youtube.com/watch?v=jitF2p7Y9mY)

## 参考:  
 https://developer.cybozu.io/hc/ja/articles/360000577946-Garoon-REST-API-一覧  
 https://www.330k.info/essay/sync-garoon-google-calendar/  
