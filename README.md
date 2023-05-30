# AI_StackChan2_README
AIｽﾀｯｸﾁｬﾝ2の使い方です。
<br><br>
AIｽﾀｯｸﾁｬﾝ2の特徴<br>

* 音声合成にWeb版 VOICEVOXを使います。
* 音声認識に"Google Cloud STT"か"OpenAI Whisper"のどちらかを選択できます。
<br>


Google Cloud STTは、”MhageGH”さんの [esp32_CloudSpeech](https://github.com/MhageGH/esp32_CloudSpeech/ "Title") を参考にさせて頂きました。ありがとうございました。<br>
"OpenAI Whisper"が使えるようにするにあたって、多大なご助言を頂いた”イナバ”さん、”kobatan”さんに感謝致します。<br>


---

### ChatGPTのAPIキーの取得 ###

ChatGPTのAPIキー取得方法は以下の通りです。(詳細はこのページ一番下のリンクを参照してください。)

* [OpenAIのウェブサイト](https://openai.com/ "Title")にアクセスして、アカウントを作成します。メールアドレスと携帯電話番号が必要です。
* アカウント作成後、APIキーを発行します。APIキーは有料ですが、無料期間やクレジットがあります。<br>

### Web版 VOICEVOX のAPIキーの取得 ###

* Web版 VOICEVOX のAPIキーの取得方法は、このページ（[ttsQuestV3Voicevox](https://github.com/ts-klassen/ttsQuestV3Voicevox/ "Title")）の一番下の方を参照してください。)<br>
VOICEVOXのAPIキー取得後忘れずに“VOICEVOX用API利用登録”をしてください。そうしないと音声合成が高速にならないので音声が途切れ途切れになります。

### Google Cloud Speech to Text のAPIキーの取得（音声認識にWhisperを使うときは不要） ###

Google Cloud Speech to TextのAPIキー取得方法は以下の通りです。(詳細はこのページ一番下のリンクを参照してください。)

* [Google Cloud Platformのウェブサイト](https://cloud.google.com/?hl=ja/ "Title")にアクセスして、アカウントを作成します。メールアドレスと携帯電話番号が必要です。カードの登録が必須ですが、無料トライアルや無料枠があります。
* アカウント作成後、APIキーを取得します。<br>
APIキーでSpeech to Textを有効にするのを忘れないで下さい。<br>

---


### 使い方 ###

* SDカードのルートに以下の2つのファイルを作成しておくと、使用できるようになります。<br>正常に動作するのが確認できたら設定に使ったSDカードは必ず抜いておいて下さい。

1. wifi.txtファイル：ファイル名は"wifi.txt"で、中身は次の通りです。<br>
YOUR_WIFI_SSID<br>
YOUR_WIFI_PASS<br>

2. apikey.txtファイル：ファイル名は"apikey.txt"で、中身は次の通りです。<br>
YOUR_OPENAI_APIKEY<br>
YOUR_VOICEVOX_APIKEY<br>
YOUR_STT_APIKEY<br>

* 【注意】<br>"YOUR_STT_APIKEY"には"Google Cloud STTのAPIキー" または、"YOUR_OPENAI_APIKEY"と同じものを設定します。<br>
"YOUR_STT_APIKEY"に"YOUR_OPENAI_APIKEY"と同じものを設定した場合は音声認識にOpenAI Whisperが使われます。


* もしM5Stackが以前にWifiに接続していた場合、SDカードが必要なく自動的にWifiに接続されます。<br>
この場合、ブラウザで"http://XXX.XXX.XXX.XXX/apikey"にアクセスし、APIキーを設定できます。<br>
(xxxx.xxxx.xxxx.xxxxはAIスタックチャンの起動時に表示されるIPアドレスです。)<br>

* ｽﾀｯｸﾁｬﾝの額付近にタッチするとマイクからの録音が始まり音声認識で会話できるようになります。<br>
録音時間は7秒程度です。<br>

* デフォルトの声（話者）を設定できます。<br>
例：http://xxxx.xxxx.xxxx.xxxx/setting?speaker=1<br>
値は0～60<br>
値の一覧は一番下の話者番号一覧に有ります。<br>

* 一時的な声の変更には、voiceパラメータを指定できます。<br>
値の一覧は一番下の話者番号一覧に有ります。<br>
例えば、次のように指定します。<br><br>
http://192.168.11.20/chat?voice=4&text=こんにちは<br>
<br>

* ブラウザで"http://xxxx.xxxx.xxxx.xxxx/role"にアクセスすると、ロールを設定できます。<br>
(xxxx.xxxx.xxxx.xxxxはAIスタックチャンの起動時に表示されるIPアドレスです。)<br>
テキストエリアに何も入力せずに送信すると、以前に設定されたロールが削除されます。<br><br>
ロール情報は自動的にspiffsに保存されます。<br>

* ブラウザで"http://xxxx.xxxx.xxxx.xxxx/role_get"にアクセスすると、現在設定しているロールを取得できます。<br>

* スピーカーの音量を調整できます。<br><br>
例：http://xxxx.xxxx.xxxx.xxxx/setting?volume=180<br>
volumeの値は0～255<br>

* 独り言モードを追加しました。ランダムな時間間隔で、ランダムに喋ります。<br>
感情表現機能と組み合わせると楽しいです。<br>
ボタンAで独り言モードをON/OFFできます。<br>
独り言モードでも従来通りスマホから会話できます。<br>
<br>

* M5Stack Core2の画面中央付近にタッチするとｽﾀｯｸﾁｬﾝの首振りを止められます。<br>

* M5Stack Core2のボタンCを押すと、音声合成のテストが出来ます。<br>

以上が、AIスタックチャンの使い方になります。<br><br>
### 注意点として、M5Burnerでファームを書き込み後には再度SDからAPIキーを設定することを忘れないようにしてください。 ###
<br>

---

### ChatGPTのAPIキー取得の参考リンク ###

* [ChatGPT API利用方法の簡単解説](https://qiita.com/mikito/items/b69f38c54b362c20e9e6/ "Title")<br>

### Web版 VOICEVOX のAPIキーの取得 ###

* Web版 VOICEVOX のAPIキーの取得方法は、このページ（[ttsQuestV3Voicevox](https://github.com/ts-klassen/ttsQuestV3Voicevox/ "Title")）の一番下の方を参照してください。)<br>

### Google Cloud Speech to TextのAPIキー取得の参考リンク ###

* [Speech-to-Text APIキーの取得／登録方法について](https://nicecamera.kidsplates.jp/help/feature/transcription/apikey/ "Title")<br>

### ChatGPTのキャラクター設定の参考リンク ###

* [ChatGPTのAPIでキャラクター設定を試してみた](https://note.com/it_navi/n/nf5f702b36a75#8e42f887-fb07-4367-9f3f-ab7f119eb064/ "Title")<br>
<br>

### VoiceVoxの話者番号 ###

* VoiceVox話者番号一覧<br>
 0:四国めたん（あまあま）<br>
 1:ずんだもん（あまあま）<br>
 2:四国めたん（ノーマル）<br>
 3:ずんだもん（ノーマル）<br>
 4:四国めたん（セクシー）<br>
 5:ずんだもん（セクシー）<br>
 6:四国めたん（ツンツン）<br>
 7:ずんだもん（ツンツン）<br>
 8:春日部つむぎ（ノーマル）<br>
 9:波音リツ（ノーマル）<br>
10:雨晴はう（ノーマル）<br>
11:玄野武宏（ノーマル）<br>
12:白上虎太郎（ふつう）<br>
13:青山龍星（ノーマル）<br>
14:冥鳴ひまり（ノーマル）<br>
15:九州そら（あまあま）<br>
16:九州そら（ノーマル）<br>
17:九州そら（セクシー）<br>
18:九州そら（ツンツン）<br>
19:九州そら（ささやき）<br>
20:もち子(cv 明日葉よもぎ)<br>
21:剣崎雌雄（ノーマル）<br>
22:ずんだもん（ささやき）<br>
23:WhiteCUL（ノーマル）<br>
24:WhiteCUL（たのしい）<br>
25:WhiteCUL（かなしい）<br>
26:WhiteCUL（びえーん）<br>
27:後鬼（人間ver.）<br>
28:後鬼（ぬいぐるみver.）<br>
29:No.7（ノーマル）<br>
30:No.7（アナウンス）<br>
31:No.7（読み聞かせ）<br>
32:白上虎太郎（わーい）<br>
33:白上虎太郎（びくびく）<br>
34:白上虎太郎（おこ）<br>
35:白上虎太郎（びえーん）<br>
36:四国めたん（ささやき）<br>
37:四国めたん（ヒソヒソ）<br>
38:ずんだもん（ヒソヒソ）<br>
39:玄野武宏（喜び）<br>
40:玄野武宏（ツンギレ）<br>
41:玄野武宏（悲しみ）<br>
42:ちび式じい（ノーマル）<br>
43:櫻歌ミコ（ノーマル）<br>
44:櫻歌ミコ（第二形態）<br>
45:櫻歌ミコ（ロリ）<br>
46:小夜/SAYO（ノーマル）<br>
47:ナースロボ＿タイプＴ（ノーマル）<br>
48:ナースロボ＿タイプＴ（楽々）<br>
49:ナースロボ＿タイプＴ（恐怖）<br>
50:ナースロボ＿タイプＴ（内緒話）<br>
51:†聖騎士 紅桜†（ノーマル）<br>
52:雀松朱司（ノーマル）<br>
53:麒ヶ島宗麟（ノーマル）<br>
54:春歌ナナ（ノーマル）<br>
55:猫使アル（ノーマル）<br>
56:猫使アル（おちつき）<br>
57:猫使アル（うきうき）<br>
58:猫使ビィ（ノーマル）<br>
59:猫使ビィ（おちつき）<br>
60:猫使ビィ（人見知り）<br>
<br><br>
