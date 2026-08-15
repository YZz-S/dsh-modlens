---
summary: '鏁呴殰鎺掓煡锛歮odlens 鍙兘鎵撳嵃鐨勬瘡涓€鏉℃姤閿欍€佹垚鍥犱笌瑙ｆ硶'
read_when:
  - 杩愯澶辫触浜嗭紝鎶ラ敊淇℃伅鐪嬩笉鏄庣櫧
  - recover-paste 浠€涔堥兘娌℃壘鍒帮紝鎴栨壘鍒颁簡閿欑殑鍥剧墖
  - 鍒ゆ柇涓€娆″け璐ュ睘浜庨厤缃棶棰樸€侀搴﹂棶棰樿繕鏄?bug
---

# 鏁呴殰鎺掓煡

[English](troubleshooting.md) | 涓枃

鍏堣窇 `modlens doctor`锛氬畠浼氭鏌ヤ綘鐨?Node 鐗堟湰銆佸摢浜?provider 宸插氨缁€佸皢閫変腑鍝竴涓強鍏跺師鍥狅紝浠ュ強妫€娴嬪埌鐨?harness锛屽叏绋嬩笉娑堣€楅搴︼紝涔熶笉鍙戠綉缁滆姹傘€傚ぇ澶氭暟閰嶇疆闂鍦ㄤ綘缁х画寰€涓嬭涔嬪墠灏辫兘琚畠鏌ュ嚭鏉ャ€?
涓嬮潰姣忔潯娑堟伅閮芥槸 modlens 瀹為檯浼氭墦鍗扮殑銆傛嬁浣犵湅鍒扮殑瀛楃溂鍦ㄦ湰鏂囬噷鎼滅储鍗冲彲銆?
## Antigravity CLI 璇讳笉鍒板凡淇濆瓨鐨勭櫥褰曚护鐗?
```
Antigravity CLI cannot read its stored login token.

On Linux this usually means the OS keyring is locked, which is normal for headless
sessions (agents, cron, systemd, SSH without a desktop login) ...
```

agy 鎶婁护鐗屽瓨鍦ㄦ搷浣滅郴缁熼挜鍖欎覆閲屻€傞挜鍖欎覆琚攣瀹氭椂锛宎gy 浼氭妸鑷繁鎶ュ憡涓烘湭鐧诲綍锛屽苟灏濊瘯娴忚鍣ㄧ櫥褰曪紝鑰屾病鏈夋樉绀哄櫒鏃惰繖涓祦绋嬫棤娉曞畬鎴愩€備笁鏉″嚭璺細

- 瑙ｉ攣閽ュ寵涓诧紝鎴栧湪妗岄潰浼氳瘽閲岃繍琛?modlens銆?- 鐢?`agy` 閲嶆柊鐧诲綍銆?- 鎹竴涓笉闇€瑕佷氦浜掑紡鐧诲綍鐨?provider锛?
```bash
modlens config set gemini-api.apiKey <key>   # free key: https://aistudio.google.com
modlens config set provider gemini-api
```

## 棰濆害鐢ㄥ敖

```
Individual quota reached. ... Resets in 94h19m9s.

agy's free tier is one weekly bucket shared by the desktop app, the CLI, and the SDK ...
```

绛夐噸缃紝鎴栨崲鍒?`gemini-api`锛屽畠鏈夎嚜宸辩嫭绔嬬殑棰勭畻銆傚苟琛岀殑 subagent 浼氶蹇€楀共杩欎釜鍏变韩棰濆害姹狅紝鐢ㄥ緱鐚涚殑涓€澶╁氨鑳芥妸瀹冪敤瀹屻€?
## 鎵句笉鍒?provider CLI

```
Provider CLI not found: agy (spawn ENOENT). Install it and sign in first.
```

浜岃繘鍒朵笉鍦?PATH 涓婏紝鎴栬€?`--provider-bin` 鎸囬敊浜嗗湴鏂广€傚叾浠?spawn 绾уけ璐ワ紙`... could not start \`claude\`: spawn EACCES`锛変細淇濈暀鐪熷疄閿欒鐮侊紝鏂逛究瀹氫綅銆俉indows 涓?npm 瑁呯殑 CLI 鏄?`.cmd` shim锛宮odlens 閫氳繃 PATHEXT 瑙ｆ瀽骞剁洿鎺ヨ繍琛屽畠鑳屽悗鐨?Node 鍏ュ彛锛屾墍浠ヨ８鍚嶏紙ENOENT锛夊拰 `.cmd`锛圗INVAL锛夐兘涓嶄細鍗′綇瀹冦€?
```
Working directory does not exist: /some/path
```

鎴愬洜涓嶅悓锛屼絾鎿嶄綔绯荤粺杩斿洖鐨勬槸鍚屼竴涓簳灞傞敊璇爜锛歚--workdir` 鎸囧悜浜嗕竴涓笉瀛樺湪鐨勭洰褰曘€備簩杩涘埗鏈韩娌￠棶棰樸€?
## recover-paste 浠€涔堥兘娌℃壘鍒?
```
No pasted images found in any session storage for this directory (looked in: ...)
```

鎸夊彲鑳芥€т粠楂樺埌浣庯細

- **浣犲湪閿欒鐨勭洰褰曢噷銆?*鎭㈠鍙檺浜庡璇濇墍鍦ㄧ殑椤圭洰銆備紶 `--cwd /path/to/project`銆?- **鏍规湰娌℃湁绮樿创杩囥€?*鎷栬繘鏉ョ殑鏂囦欢鍜屾墜鎵撶殑璺緞鏈潵灏辨槸鐪熷疄鏂囦欢锛屾病鏈変粈涔堝彲鎭㈠鐨勶細鐩存帴鐢ㄩ偅涓矾寰勩€?- **鏌愪釜閰嶇疆闂鎸′綇浜嗕竴涓?harness銆?*琚尅鐨勫師鍥犱細鍑虹幇鍦ㄥ悓涓€鏉℃秷鎭殑 `Blocked:` 涔嬪悗锛屼緥濡?OpenCode 闇€瑕?Node 22.13+ 鎵嶈兘鐢?`node:sqlite`銆?
## recover-paste 杩斿洖浜嗗彟涓€涓」鐩殑鍥剧墖

杩欑鎯呭喌鐜板湪涓嶅簲璇ュ啀鍑虹幇浜嗭紝鐪熷嚭鐜板氨鏄€煎緱涓婃姤鐨?bug銆傛仮澶嶆鏌ョ殑鏄?transcript 閲岃褰曠殑宸ヤ綔鐩綍锛屼笉鍙槸鐩綍鍚嶏紝鍥犱负鐩綍 slug 浼氭挒杞︼紙`/tmp/a.b` 鍜?`/tmp/a-b` 鐢熸垚鍚屼竴涓?slug锛夈€傛彁 issue 鏃跺甫涓婅緭鍑洪噷鐨?`harness` 鍜?`transcript` 瀛楁銆?
## 椤圭洰瀵逛簡锛屽浘鐗囨仮澶嶉敊浜?
杈撳嚭鎸変粠鏃у埌鏂版帓鍒楋紝鎵€浠?*鏈€鍚?*涓€鏉℃墠鏄渶杩戜竴娆＄矘璐淬€俬arness 瀛樹簡鏂囦欢鍚嶆椂鏉＄洰浼氬甫 `filename`锛氱敤鎴锋彁鍒板悕瀛楁椂鎸夊畠鏉ュ尮閰嶃€俙--count 3` 鑳藉缁欏嚑涓€欓€夈€?
## recover-paste锛氳鐩栨娴嬬粨鏋滀笌杈撳嚭浣嶇疆

`recover-paste` 浼氳嚜鍔ㄦ娴嬭嚜宸辫繍琛屽湪鍝釜 harness 閲岋紙鍏堢湅杩涚▼绁栧厛锛屽啀鐪嬬幆澧冪壒寰侊級锛屽苟涓斿彧璇婚偅涓?harness 鐨勫瓨鍌ㄣ€備袱涓棆閽彲浠ヨ鐩栧畠锛?
- **`MODLENS_HARNESS`** 涓嶇敤鍛戒护琛屽弬鏁板氨鑳藉己鍒舵寚瀹氬瓨鍌ㄨ寖鍥达細`claude-code`銆乣pi`銆乣opencode`銆乣codex`锛屾垨 `none`锛堟壂鎻忔墍鏈夊瓨鍌紝涓嶉檺鑼冨洿锛夈€傛娴嬫渶鍏堣瀹冿紝鎵€浠ュ畠浼樺厛浜庤繘绋嬬鍏堝拰鐜鐗瑰緛銆俙--harness` 瀵瑰崟娆¤繍琛屽仛鍚屾牱鐨勪簨銆?- **`--out-dir`** 鍐冲畾鎭㈠鍑虹殑鍥剧墖钀藉湪鍝€傞粯璁ゆ瘡娆¤繍琛岄兘鏂板缓涓€涓笉鍙娴嬬殑 `<tmpdir>/modlens-paste-*` 鐩綍锛?700锛屽唴鍚?0600 鏂囦欢锛夛紝娌′汉鑳介鍏堝垱寤轰竴涓叡浜矾寰勬潵鎴幏瀛楄妭銆傜郴缁熶复鏃剁洰褰曚笉鍚堥€傛椂鍙互鎸囧埌鍒銆傛樉寮忎紶鍏ョ殑 `--out-dir` 鑻ュ凡瀛樺湪锛屽繀椤绘槸鐪熷疄鐩綍锛堜笉鏄鍙烽摼鎺ワ級銆佸綊浣犳墍鏈夈€佺粍鍜屽叾浠栫敤鎴锋棤浠讳綍鏉冮檺锛屽惁鍒欎細琚嫆缁濄€俉indows 涓婁細璺宠繃鎵€鏈夋潈鍜屾潈闄愭鏌ワ紝鍥犱负璇ュ钩鍙版病鏈?POSIX 鏉冮檺浣嶏紙瑙佷笅鏂?Windows 涓€鑺傦級銆傜鍙烽摼鎺ユ鏌ヤ粛鐒剁敓鏁堛€?
## 杩欐槸涓€涓?Codex 浼氳瘽

```
This is a Codex session: pasted images already exist as temp files, and each image
tag in the message carries its path.
```

涓€鍒囩鍚堣璁°€侰odex 浼氭妸绮樿创鐨勫浘鐗囧啓鍒扮鐩橈紝骞舵妸璺緞鏀捐繘娑堟伅閲岋紝鎵€浠ョ洿鎺ヤ粠 tag 閲屽彇璺緞鏉ヨ锛屼笉闇€瑕佹仮澶嶄换浣曚笢瑗裤€?
## openai provider 鐨勭粨鏋滆鎷掔粷

```
OpenAI-compatible API returned JSON that does not match the vision schema
(wrong or missing: visual.notes, ...)
```

閭ｄ釜绔偣杩斿洖浜嗕笉绗﹀悎濂戠害鐨勫唴瀹广€傛敞鎰忔帾杈烇細琚偣鍚嶇殑瀛楁鍙兘鏄己澶憋紝涔熷彲鑳芥槸瀛樺湪浣嗗舰鐘朵笉瀵广€傚儚 `visual.notes` 杩欐牱鐨勫彲閫夊瓧娈靛彧鍙兘鏄悗鑰咃紝鍥犱负瀹冪己澶辨槸琚帴鍙楃殑銆傚啓鎴?`null` 涔熶細琚涪寮冭€屼笉鏄嫆缁濓紝鎵€浠ュ墿涓嬬殑灏辨槸鐪熸鐨勭被鍨嬮敊璇€?
澶у鏁?OpenAI 鍏煎缃戝叧鍦ㄦ湇鍔＄浠€涔堥兘涓嶅己鍒讹紝濂戠害鏄互濉ソ鐨?JSON 妯℃澘褰㈠紡闅忔彁绀鸿瘝鍙戣繃鍘荤殑锛岃兘鍔涘急涓€浜涚殑妯″瀷鍙兘鍙瓟鍑轰竴鍗婏紝鍏虫帀鎬濊€冩椂灏ゅ叾鏄庢樉銆傚彲浠ユ敼鎴愯缃戝叧鑷繁寮哄埗鎵ц锛?
```bash
modlens config set openai.structuredOutput true
```

杩欎細鎶婂绾︿互 `response_format: json_schema` 鐨勪弗鏍煎舰寮忓彂杩囧幓锛宻chema 鐢?modlens 鏍￠獙鐢ㄧ殑閭ｄ唤鎺ㄥ鑰屾潵锛屾病鏈夐渶瑕佹墜宸ュ悓姝ョ殑鍓湰銆傞粯璁ゅ叧闂紝鍥犱负涓嶆敮鎸佽繖涓瓧娈电殑缃戝叧浼氱洿鎺?400銆傜湡閬囧埌灏卞叧鍥炲幓锛?
```bash
modlens config set openai.structuredOutput false
```

浣犺嚜宸卞湪 `extraBody` 閲岃鐨?`response_format` 浼樺厛绾ф洿楂樸€?
杩樻槸涓嶈灏遍噸璇曚竴娆★紝鐒跺悗鎹?provider锛?
```bash
modlens -i <image> -p gemini-api
```

## guard 缁欏嚭浜?deny锛屾垨涓€娆¤鍙栬鎷掔粷

```
Invocation guard denied this read: active model "gemini-3.1-pro" matches guards.denyModels pattern "gemini-3*". A model with native vision should read the image itself. To override, unset MODLENS_MODEL or edit guards in /Users/you/.modlens/config.json.
```

杩欐槸閰嶇疆鍦ㄦ寜棰勬湡宸ヤ綔锛氶厤缃枃浠堕噷鐨?`guards.denyModels` 鍒楀嚭浜嗚嚜甯﹁瑙夌殑妯″瀷锛屽綋鍓嶆ā鍨嬪尮閰嶅埌浜嗗叾涓竴鏉★紝寮曟搸鍥犳鎷掔粷涓轰竴寮犺妯″瀷鑷繁灏辫兘璇荤殑鍥剧墖鑺辨帀涓€娆?provider 璋冪敤銆俙modlens doctor` 鏈変竴涓?Guard 灏忚妭锛屽睍绀鸿鍒欍€佹娴嬪埌鐨勬ā鍨嬨€佹潵鑷摢涓俊鍙凤紙`MODLENS_MODEL` 鐜鍙橀噺銆佷細璇濆瓨鍌ㄦ垨 `--model` 鑷姤锛夛紝浠ュ強鍒ゅ畾缁撴灉銆?
濡傛灉妫€娴嬮敊浜嗭紝`MODLENS_MODEL=<actual-model> modlens guard` 瑕嗙洊涓€鍒囷紝`MODLENS_MODEL=none` 鎶婃ā鍨嬫爣涓烘湭鐭ワ紙鍒ゅ畾闅?`denyWhenUnknown` 璧帮紝榛樿 allow锛夈€傚交搴曞叧鎺?guard锛歚modlens config set guards.denyModels ''`銆?
涓€涓凡鐭ョ洸鍖猴細瀛樺偍妫€娴嬭鐨勬槸杩欎釜椤圭洰璁板綍鐨勬渶鏂颁竴鏉?assistant 杞锛屾墍浠ュ悓涓€涓」鐩洰褰曢噷鍚屾椂璺戠潃涓嶅悓妯″瀷鐨勪袱涓細璇濆彲鑳戒簰鐩搁伄钄斤紙Claude Code 鍜?Codex 閫氳繃娉ㄥ叆鐨勪細璇?id 閿佸畾纭垏浼氳瘽锛孭i 鍜?OpenCode 鍋氫笉鍒帮級銆備腑鎷涙椂鐢?`MODLENS_MODEL` 瑕嗙洊銆?
娉ㄦ剰涓婇潰閭ｇ纭嫆缁濆彧鍦ㄦ樉寮忕殑 `MODLENS_MODEL` 鍊肩湡姝ｅ尮閰嶅埌 `denyModels` 鏃舵墠瑙﹀彂銆傚瓨鍌ㄦ娴嬪拰 `denyWhenUnknown` 绛栫暐浠庝笉闃绘柇 `analyze`锛屽畠浠彧閫氳繃 `modlens guard` 鍙戝０锛岃€?guard 鐨?deny 鏄粰 agent 鐨勫缓璁紝涓嶆槸涓婁簡閿佺殑闂ㄣ€?
## dsh 鎻愮ず `declares no dsh.bundle 鈥?installed as a plain dependency`

dsh profile 瑁呭埌鐨勬槸鏃х増 modlens銆俙dsh.bundle` 澹版槑浠?3.9.0 璧锋墠瀛樺湪锛岃€?pnpm 11 浼氭墸浣忔渶杩?24 灏忔椂鍐呭彂甯冪殑鐗堟湰锛坄minimumReleaseAge`锛岃嚜 11.0 璧烽粯璁ゅ紑鍚€俙pnpm config get` 涓嶅睍绀鸿繖涓€椤圭殑鍐呯疆榛樿鍊硷紝鎵€浠ユ煡瀹冧粈涔堥兘涓嶆樉绀猴級銆傚綋甯﹀０鏄庣殑鐗堟湰鍏ㄩ兘钀藉湪杩欎釜绐楀彛鍐呮椂锛宲npm 浼氶潤榛樺洖閫€鍒版洿鏃х殑鐗堟湰锛岃€屾棫鐗堟湰娌℃湁 bundle 澹版槑锛宒sh 浜庢槸姝ｇ‘鍦版妸瀹冨綋浣滄櫘閫氫緷璧栵紝涓€涓伐鍏烽兘涓嶄細鍑虹幇銆?
`@latest` 缁曚笉寮€杩欎竴灞傦紝鏈〉鏃╁厛鐨勮娉曟槸閿欑殑銆傚喎闈欐湡鍏堟妸鍊欓€夌増鏈繃婊ゆ帀锛宒ist-tag 鎵嶅湪鍓╀笅鐨勯噷闈㈣В鏋愶紝浜庢槸瀹冪洿鎺ヨ惤鍒颁簡鏇存棫鐨勯偅涓笂銆傛敼鎴愬啓姝荤簿纭増鏈彿锛宲npm 浼氭妸瀹冨綋浣滀竴娆℃槑纭殑鎸囧畾锛岃€屼笉鏄竴娆¤В鏋愶細

```sh
npx -y @deepseek-ai/dsh plugin --profile <name> add dsh-modlens@3.16.6
```

`npm view dsh-modlens version` 鍙互鏌ュ埌褰撳墠鐗堟湰鍙枫€俻npm 11 浼氳涓婅鐐瑰悕鐨勭増鏈紝11.1.3 璧疯繕浼氭妸瀹冧綔涓轰竴鏉″凡鎵瑰噯鐨勪緥澶栧啓杩涜 profile 鐨?`pnpm-workspace.yaml`锛屽叾浣欐墍鏈夊寘鍜?modlens 浠ュ悗鐨勭増鏈粛鐒剁暀鍦ㄧ獥鍙ｅ悗闈€?
濡傛灉浣犺嚜宸辫杩?`minimumReleaseAge`锛宲npm 浼氭妸杩欐潯绛栫暐瑙嗕负涓ユ牸妯″紡锛岃浆鑰屾嫆缁濆畨瑁呭苟鎶ュ嚭鐗堟湰涓庢埅姝㈡椂闂达紙`ERR_PNPM_NO_MATURE_MATCHING_VERSION`锛夈€傚湪鍚屼竴涓枃浠堕噷鏀捐杩欎竴涓増鏈細

```yaml
minimumReleaseAgeExclude:
  - 'dsh-modlens@3.16.6'
```

鎴栬€呭彧涓鸿繖涓€鏉″懡浠よВ闄ゅ喎闈欐湡锛屾敞鎰忓畠瑙ｉ櫎鐨勬槸杩欐潯鍛戒护瑙ｆ瀽鍒扮殑鎵€鏈夊寘锛屼笉鍙?modlens锛?
```sh
npx -y @deepseek-ai/dsh plugin --profile <name> add dsh-modlens@latest --config.minimumReleaseAge=0
```

dsh 鐨?reconcile 浼氭敞鎰忓埌鏂扮増鏈笂鐨?bundle 澹版槑骞舵縺娲诲畠锛岄殢鍚庨噸鍚?dsh銆傜敤 `npx -y @deepseek-ai/dsh plugin --profile <name> list` 楠岃瘉銆?
## dsh锛氭ā鍨嬬湅涓嶅埌 read_image 宸ュ叿

鎻掍欢娉ㄥ唽鐨勫伐鍏峰悕鏄?`modlens_read_image`锛屼笉鏄?`read_image`銆俤sh 鐨勫伐鍏锋敞鍐岃〃鏄垎灞傜殑锛宻coped 灞備細閬斀鍏ㄥ眬灞傦細瀹夸富鐨?`read_image` 鎸傚湪 agent preset 浣滅敤鍩熴€佹彃浠舵敞鍐屽湪鍏ㄥ眬灞傦紝涓よ€呮牴鏈笉绠楅噸鍚嶏紝浜庢槸娉ㄥ唽闈欓粯鎴愬姛锛屾ā鍨嬭В鏋愬埌鐨勪粛鏄涓婚偅涓紝鑰屽畠瀵圭函鏂囨湰妯″瀷鐩存帴鎷掔粷锛圼#34](https://github.com/liustack/modlens/issues/34)锛夈€傜敤鑷繁鐨勫悕瀛楀氨娌℃湁涓滆タ浼氶伄钄藉畠锛屾ā鍨嬫槸閫氳繃宸ュ叿 schema 鎵惧埌瀹冪殑锛岃€?schema 姣忔璇锋眰閮戒細閫佽揪锛屼笌鍙粈涔堝悕瀛楁棤鍏炽€?
濡傛灉妯″瀷浠嶇劧鐪嬩笉鍒帮紝鍘?harness 鏃ュ織閲屾悳 `[modlens] ... registration skipped`銆傛兂鏀瑰悕灏卞湪鎻掍欢閰嶇疆琛岄噷璁?`toolName`锛屼絾瑕佹寫涓€涓埆浜烘病鐢ㄧ殑锛氫换浣曞凡琚煇涓?scoped 宸ュ叿鍗犵敤鐨勫悕瀛楋紝閮戒細鍍?`read_image` 涓€鏍疯閬斀锛岄偅灏卞張缁曞洖鏈妭浜嗐€?
```yaml
- id: modlens
  config:
    toolName: vision_read_image
```

## fetch failed 鎴栬繛鎺ュけ璐?
```
Could not connect to generativelanguage.googleapis.com (UND_ERR_CONNECT_TIMEOUT). The request never reached the network. ...
```

API 璇锋眰鏍规湰娌＄寮€杩欏彴鏈哄櫒銆傚湪瑕侀潬浠ｇ悊鎵嶈兘涓婄綉鐨勭綉缁滈噷杩欐槸棰勬湡琛ㄧ幇锛歂ode 鐨?fetch 榛樿鏃犺浠ｇ悊鐜鍙橀噺銆備綘鏄庣‘瑕佹眰璧颁唬鐞嗗悗 modlens 鎵嶄細閬靛惊锛屼袱绉嶅啓娉曚换閫夛細

```bash
HTTPS_PROXY=http://127.0.0.1:7890 modlens -i shot.png -p gemini-api   # env (NO_PROXY honored too)
modlens config set proxy http://127.0.0.1:7890                        # persistent, all API providers
modlens config set openai.proxy http://127.0.0.1:7890                 # one provider only
```

浠ｇ悊鍙綔鐢ㄤ簬 API provider 鐨勮姹傘€傝繙绋嬪浘鐗囩殑涓嬭浇璺緞鏈夋剰淇濇寔鐩磋繛骞堕拤姝?IP锛氬畠鐨?SSRF 闃叉姢鏍￠獙鐨勬鏄疄闄呰繛鎺ョ殑閭ｄ釜鍦板潃锛屽姞浜嗕唬鐞嗚繖浜涢槻鎶ゅ氨澶辨槑浜嗐€傚湪蹇呴』璧颁唬鐞嗙殑鏈哄櫒涓婏紝浼樺厛鐢ㄦ湰鍦版枃浠讹紝鎴栬鏁呴殰杞Щ閾炬妸杩滅▼ URL 浜ょ粰浼氬湪涓婃父鑷鎶撳彇鐨?provider銆?
## 閰嶇疆鏂囦欢闂

```
Cannot read /Users/you/.modlens/config.json: EACCES ... Fix the file or its permissions.
```

鏂囦欢瀛樺湪浣嗚涓嶄簡銆傛枃浠剁己澶辨槸姝ｅ父鐨勶紝鎵€浠ヨ繖鏄湡闂锛屼笉鑳芥棤瑙嗐€?
```
Failed to parse ... Fix or delete the file.
```

JSON 鏃犳晥銆俙modlens config init --force` 浼氬啓鍏ヤ竴浠藉共鍑€鐨勯厤缃紝鏃у唴瀹逛細涓㈠け銆?
## 瓒呮椂

```
antigravity-cli provider timed out after 210000 ms.
```

甯?`--timeout 300000` 閲嶈瘯涓€娆°€備俊鎭瘑闆嗙殑鍥剧墖鍦?agy 涓婅姳 15-40 绉掑睘浜庢甯革紝`-m gemini-3.1-pro-high` 杩樹細鏇存參銆傛棤瑙?SIGTERM 鐨勫紩鎿庝細琚崌绾т负 SIGKILL锛屾墍浠ヨ秴鏃舵棤璁哄浣曢兘浼氳繀閫熻繑鍥炪€?
## 鎺ㄧ悊妯″瀷涓婃瘡娆¤鍙栭兘寰堟參

榛樿鎬濊€冪殑妯″瀷浼氬湪寮€濮嬭浆褰曚箣鍓嶅厛鎶婇绠楄姳鍦ㄦ€濊€冧笂锛岃€岃瑙夎鍙栧苟涓嶉渶瑕佹€濊€冦€傛病鏈夌粺涓€鐨?`--no-thinking` 鍙傛暟锛屽洜涓烘瘡瀹跺巶鍟嗙粰杩欎釜寮€鍏宠捣鐨勫悕瀛楅兘涓嶄竴鏍凤紝鎵€浠ョ洿鎺ヤ紶鍘傚晢鑷繁鐨勫瓧娈碉細

```bash
modlens config set openai.extraBody '{"thinking":{"type":"disabled"}}'
modlens -i shot.png --extra-body '{"reasoning_effort":"low"}'    # one run only
```

鍚勫鍘傚晢鐨勫叿浣撳啓娉曘€佸摢浜涙ā鍨嬪畬鍏ㄥ叧涓嶆帀锛屼互鍙婃€庝箞纭瀛楁鐪熺殑鐢熸晥锛岃[閰嶇疆鎵嬪唽](../skills/modlens/references/configure.zh-CN.md#鍏抽棴鎬濊€?銆?
```
extraBody cannot override "messages" for the openai provider
```

杩欎釜瀛楁鎵胯浇鐫€鍥剧墖銆乸rompt 鍜?schema 寮哄埗閫昏緫銆傛妸瀹冨垹鎺夛紝鍙繚鐣欏巶鍟嗙殑寮€鍏冲瓧娈点€傜綉鍏宠繑鍥?400 骞剁偣鍚嶄綘璁剧疆鐨勬煇涓瓧娈碉紝璇存槑閭ｄ釜绔偣鐢ㄧ殑鏄彟涓€绉嶅啓娉曘€傚湪 `antigravity-cli` 鎴?`claude-cli` 涓婅繍琛屾椂锛宍meta.warnings` 浼氳鏄庤鍊艰蹇界暐浜嗭紝鍥犱负 CLI provider 娌℃湁璇锋眰浣撱€?
## Windows

ModLens 鍙互鍦?Windows 涓婅繍琛屻€備笁涓€煎緱浜嗚В鐨勫钩鍙板樊寮傦細

- **娌℃湁 POSIX 鏉冮檺妫€鏌ャ€?*Windows 鏂囦欢娌℃湁鎵€鏈夎€呫€佺粍銆佸叾浠栫敤鎴风殑鏉冮檺浣嶏紙璇诲嚭鏉ユ槸 `0o666`/`0o777`锛屽疄闄呰闂敱 ACL 鎺у埗锛夛紝鎵€浠?`doctor` 涓嶈瘎鍒ら厤缃枃浠剁殑鏉冮檺妯″紡锛宍recover-paste --out-dir` 涔熶笉浼氬洜鎵€鏈夋潈鎴栫粍鍜屽叾浠栫敤鎴风殑鏉冮檺鑰屾嫆缁濈洰褰曘€俙--out-dir` 鐨勭鍙烽摼鎺ユ鏌ヤ粛鐒剁敓鏁堛€?- **Harness 妫€娴嬩緷璧栫幆澧冪壒寰併€?*娌℃湁 `ps` 鍙互璇昏繘绋嬫爲锛屾娴嬪彧鑳戒緷闈犲悇 harness 璁剧疆鐨勭幆澧冨彉閲忋€傜寽閿欐椂鐢?`--harness <name>` 鎴?`MODLENS_HARNESS` 寮哄埗鎸囧畾銆?- **绮樿创鎭㈠銆?*OpenCode 鐨勬仮澶嶅湪 Windows 涓婂凡瑕嗙洊锛坕ssue #11锛夈€侰laude Code 鍜?Pi 鐨?JSONL 璺緞渚濊禆 `os.homedir()` 鍜屽悇 harness 鍦ㄩ偅閲岀殑纾佺洏 slug銆傛仮澶嶆墤绌烘椂锛岀敤 `--transcript` 鐩存帴鎸囧悜鏂囦欢锛屾垨鎶婂浘鐗囨嫋杩涚粓绔€?
## 杩樻槸娌¤В鍐?
鎻?issue 鏃堕檮涓婂畬鏁村懡浠ゅ拰瀹屾暣鎶ラ敊锛歨ttps://github.com/liustack/modlens/issues
