# TODO TASK 一覧
## todo
- すでに埋まっているはずのスロットにプレイヤーが入ってきた場合イベントの漏れが発生している可能性
  - プレイヤーの入場時とスロット移動時の処理は実装済み。あとは重複チェック処理
- 複数起動対応
- abort時の順番
  - 新ホストが曲を変えずにスタートし、プレイヤーがabort投票、スキップ投票を行うと、一人余分に飛ばしてしまう。
  
## wip
- history repoをlobbyに移動
  - historyloaderは読み込みタイミングなどを管理する
    - historyloaderの機能は他に分散させる
  - repoのイベントの種類を増やす
  - ボット再起動直後に現在試合中かどうか判断するのに使用する
  - マップチェッカーは再起動後に直前の曲を調べる -> !mp map 0対策
## done
- ヒストリーを""定期的に""読み込んで、キックや試合の詳細情報をイベントとし発生させる
- lobbykeeperに定期的なアナウンス機能を追加する
- 不必要にキックを行ったプレイヤーをキックする機能
  - オーナーやレフェレーをキックした場合即座に処罰
  - オーナーやレフェレーは処罰の対象外
  - 同じユーザーを何度もキックするのは認めるべき
- History取得でエラーが起きた場合の復帰
  - ID取得ができなくなってしまう
  - 1分後に再試行とか？
- ログサーバーを分離
- 再接続時のオーダーがおかしい
- start voteが試合中でも投票できてしまう.
- aborterのstat対応
- cliにstatの結果を載せない
- MAPIDは編集アップロード時に変更される？
  + 呼び込みくん normal:2346156, prototype:2345992,insane:2345991, extra 2345993, set:1122617
  + 更新しても変わらない
- タイマー起動をバンチョーレスポンスで判定する(match starter auto start timerなど)
- 試合終了後ボットが変更する前に変更されるとループになる <- selectorでpendinghostに対する処理が抜けていた
- 切断時に自動!mp settings
- !mp settingsを任意のタイミングで解析する。cliのinfoにロビータイトルを表示
- 順番復元機能　ゼロ幅スペース取り除き機能
- ホストになったあとすぐに!skipすると無視されてしまう。前の!skip投票の誤検知との兼ね合いどうするか => スキップ成立後だけクールタイム
- 複数同時起動できる？その場合、ログの分離をどうするか？
- cliのsから!mpコマンドが発行できない。
- ゲームモードや勝利条件を変更したときに挙動が変化しないか確かめる
- skiptoが機能しない
- recorderの使用をオプションから切り替え
- All players are ready が連続で発生することがある？!mp startに短いcooltimeを設ける
- 一部のチャットがircでは記録されているのにchatとして認識されない問題。ユーザー単位で発生している？ => replaceが１つ分のスペースしか変換していなかった
- team mode でのmp settings
- lobbyのplayersfinishedやplayersingameはplayerクラスにgamestatusというプロパティをもたせて管理したほうが良い.
- !infoにバージョンを表示する。
- 自作マップを貼ったときのイベント => mapid 0
- Team modeになるとユーザー参加を検知できない
- 長い名前のユーザー名が処理できない
- cliで試合開始時にマップ名を表示したい
- レフェリー検出時にログ
- 権限ユーザーが!mp start 30 すると２重でチャットしてしまう 権限管理の見直し、プレイヤー情報に権限を保存
- cliからコマンドを起動したい
- wordcounter用のinfo出力作成
- skip受付後にメッセージが表示されない
- refereeが部屋を抜けたら？listref => 部屋を抜けてもrefreeは継続する
- spamフィルター対策
- MatchStarter拡張、!start vote, !start timer 機能を追加
- プレイヤーが一人のときにタイマーが起動中判定になってしまう
- auto abortまでの時間が短い?
- 試合中にhostsが抜けた状態でAbortが受け付けられるとhostが誰もいない状態になる
- !mp start の連続使用時の挙動
- !mp start 1, !mp start 60 のときの挙動 second(s)?
- mp response check !mp start, !mp aborttimer, !mp kick, !mp addref, !mp removeref, !mp listrefs
- !mp abortもAbort判定にしたい
- cli ロビー作成時と入室時にコンソールにもっと情報を表示する
- hostsキュー表示するとき全員を表示する必要はない？名前を省略するか、後半を省くか
- 試合がスタックした場合のabort投票。abort時のホスト切り替え（始まる前にスタックしたか、終了時にスタックしたか） => 一人でもmatch finishedなら切り替え。
- !mp abortで試合を終了した場合、ホストが変更されない
- マップを変更しなかった場合ホストを変更しない仕組み
- スキップ後に自動で変更されないことがあった　修正済み
- abort後に ismatching フラグを折り忘れていた　修正済み
- キューの先頭にゴミが付く 修正
- mp settings で名前に[] が入るプレイヤーを正しく認識できない 修正済み
- /skip機能の追加 hostなら即変更、それ以外なら投票で変更　
- host skip timer機能　
- host skipperの表示が投票0でも退出時に表示されてしまう。修正済み
- cliのdisplayの誤字とエラー　修正済み
- log4jsのコンフィグは起動時書き換えを有効にするために独立したファイルにしたほうがいい。
- プレイヤーのチャット専用のログファイルがほしい。
- auth2のプレイヤーがホストのときに/skipしても即スキップにならない
- ユーザーがいなくなったときにエラーが発生
-  ホストが試合中に抜けると順番がおかしくなる.キューの並び替えタイミングを変更 
- ロビーが空になった際の自動クローズ
- ホストのスキップ時間が迫ったときに警告文を出すか、チャットしたときにタイマーが再設定されるようにする
- 誰もいない状態で!mp settingsしたときにどうなるか？ -> players: 0で打ち切り
- スキップ時にたまりすぎる問題 -> クールタイムを設けた
- ロビーに入って!mp settingsで情報を取得した際に、ホストからスロット順で並ぶようにする
- skip voteの票が１つでも入っている場合、プレイヤーの入退出のたびにメッセージが出て鬱陶しいかもしれない。