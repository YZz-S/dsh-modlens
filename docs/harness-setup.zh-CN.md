---
summary: '瀹夸富鎺ュ叆锛氬浘鐗囧湪 Codex銆丆laude Code銆丳i銆丱penCode 涓浣曟姷杈炬ā鍨?
read_when:
  - 鍦ㄦ煇涓叿浣撶殑缂栫爜 agent 閲屽畨瑁呴厤缃?modlens
  - 绮樿创鐨勫浘鐗囨病鏈夋姷杈炬ā鍨?  - 浜嗚В recover-paste 鍦ㄥ悇 harness 閲屽垎鍒仛浠€涔?---

# 瀹夸富鎺ュ叆

[English](harness-setup.md) | 涓枃

绮樿创鐨勫浘鐗囨渶缁堣惤鍦ㄥ摢閲岋紝姣忎釜 harness 閮戒笉涓€鏍凤紝modlens 鍦ㄦ瘡涓?harness 閲岃蛋鐨勮矾绾夸篃涓嶅悓銆俙recover-paste` 浼氭娴嬭嚜宸辫繍琛屽湪鍝釜 harness 閲岋紙鍏堢湅杩涚▼绁栧厛锛屽啀鐪嬬幆澧冨彉閲忔寚绾癸級锛屽彧璇诲彇璇?harness 鐨勫瓨鍌ㄣ€?
## Codex

绮樿创鐨勫浘鐗囦細钀芥垚鐪熷疄鐨勪复鏃舵枃浠讹紝娑堟伅閲屽甫鐫€褰㈠ `<image name=[Image #1] path="/tmp/xxxx.png">` 鐨勬爣绛俱€俿kill 鐩存帴浠庢爣绛鹃噷璇诲嚭璺緞銆俙recover-paste` 妫€娴嬪埌 Codex 鍚庝細鎷掔粷鎵ц锛屽苟鎶婁綘鎸囧洖杩欎釜鏍囩銆?
绾枃鏈ā鍨嬫湁涓€涓潙锛氫竴鏃?`models.json` 澹版槑浜?`input_modalities: ["text"]`锛孋odex TUI 浼氱洿鎺ユ嫤涓?Ctrl+V 绮樿创銆傛敼涓烘妸鏂囦欢鎷栬繘缁堢銆佹墜鍔ㄨ緭鍏ヨ矾寰勶紝鎴栦娇鐢?`codex exec -i image.png "..."`銆?
## Claude Code銆丳i銆丱penCode

杩欎笁瀹堕兘涓嶅儚 Codex 閭ｆ牱閫掔粰妯″瀷涓€涓彲鐢ㄧ殑涓存椂鏂囦欢璺緞锛堣緝鏂扮殑 Claude Code 鐗堟湰纭疄浼氭妸绮樿创鍐欒繘鑷繁鐨?`~/.claude/image-cache/`锛屼絾鍙湪缁堢鍏ュ彛浠ヨ矾寰勮鐨勫舰寮忔敞鍏ワ級锛屼笉杩囦笁鑰呴兘浼氬湪缃戝叧鍓ョ鍥剧墖涔嬪墠锛屾妸鐢ㄦ埛娑堟伅瀹屾暣瀛樺湪鏈湴锛?
| Harness | 瀛樺偍浣嶇疆 | 璇存槑 |
| :-- | :-- | :-- |
| Claude Code | `~/.claude/projects/<slug>/<session>.jsonl` | 鍥剧墖浠?base64 瀛樺偍銆傛敞鍏ョ殑 `CLAUDE_CODE_SESSION_ID` 鍙簿纭畾浣嶅綋鍓?session |
| Pi | `~/.pi/agent/sessions/--<encoded-cwd>--/*.jsonl` | 缁撴瀯涓?Claude Code 鐩稿悓 |
| OpenCode | `~/.local/share/opencode/opencode.db` | SQLite锛屽浘鐗囦互 data URL 瀛樺偍锛堥€氳繃 `node:sqlite` 璇诲彇锛?|

鍦?Claude Code 閲岄€氳繃 `ANTHROPIC_BASE_URL` 鎺ュ叆绾枃鏈ā鍨嬫椂锛岀矘璐寸殑鍥剧墖瑕佷箞鍙樻垚涓€涓笉甯﹁矾寰勭殑 `[Unsupported Image]` 鍗犱綅绗︼紙瀹芥澗鐨勭綉鍏筹級锛岃涔堢洿鎺ヨ璇锋眰鎶ラ敊锛圼#62009](https://github.com/anthropics/claude-code/issues/62009)锛夈€傚浘鐗囧瓧鑺傚苟娌℃湁涓紝`recover-paste` 鍙栧洖鐨勫氨鏄畠銆?
## skill 鐨勫瓨鏀句綅缃?
| Harness | skill 璇诲彇浣嶇疆 |
| :-- | :-- |
| Claude Code | `~/.claude/skills/` |
| Codex | `~/.codex/skills/` |
| Pi銆丱penCode | `~/.agents/skills/` |

杩欎簺浣嶇疆閮芥敮鎸佺鍙烽摼鎺ワ紝鎶?skill 鐩綍閾炬帴涓€娆★紝姣忎釜 agent 鐢ㄧ殑灏遍兘鏄渶鏂扮増鏈€?
## 骞冲彴鏀寔

macOS 鍜?Linux 瀹屾暣鏀寔锛屽苟鍦?CI 涓婁互 Node 22 鍜?24 楠岃瘉銆?
Windows 璺戝悓涓€濂?CI 鐭╅樀銆傞偅閲屾病鏈?`ps`锛屾娴嬩細璺宠繃杩涚▼绁栧厛杩欎竴姝ワ紝閫€鍥炲埌涓婇潰鐨勭幆澧冨彉閲忔寚绾癸紝鎵€浠ヤ竴涓粈涔堟寚绾归兘涓嶈鐨?harness 浼氳鍒や负鏈鍑猴紙鐢?`--harness` 鎴?`MODLENS_HARNESS` 寮哄埗鎸囧畾锛夈€侽penCode 鐨勭矘璐存仮澶嶅湪 Windows 涓婃湁瑕嗙洊锛屽寘鎷?[#11](https://github.com/liustack/modlens/issues/11) 閲岀殑璺緞鍒嗛殧绗﹀綊涓€鍖栵細opencode 璁板綍鐨?`session.directory` 鐢ㄦ鏂滄潬锛岃€岄偅閲岀殑 `path.resolve` 杩斿洖鍙嶆枩鏉狅紝鍖归厤鍓嶄袱杈归兘浼氬綊涓€鍖栥€侸SONL 瀛樺偍锛圕laude Code銆丳i锛変互 `os.homedir()` 鍜屽悇 harness 鑷繁鐨勭鐩?slug 涓洪敭锛屽湪 POSIX 涓婇獙璇併€傚閮ㄥ紩鎿庯紙Antigravity CLI銆丆laude CLI锛夊彧鍦ㄦ湁 Windows 鐗堟湰鐨勫钩鍙颁笂杩愯銆?
## 缃戝叧閰嶇疆

OpenCode 鎺?DeepSeek锛氭墽琛?`opencode auth login`锛岄€夋嫨 DeepSeek 骞剁矘璐?key锛堜細瀛樿繘 `~/.local/share/opencode/auth.json`锛夛紝鐒跺悗鍦?`~/.config/opencode/opencode.jsonc` 閲屾妸榛樿妯″瀷璁句负 `deepseek/deepseek-v4-flash`銆侾i 浠?`~/.pi/agent/auth.json` 璇诲彇瀹冪殑 key銆?
## DeepSeek Harness锛坉sh锛?
dsh 涓庡叾浠?harness 涓嶅悓锛歮odlens 浠ュ師鐢熷伐鍏风殑褰㈠紡鎺ュ叆锛岃€屼笉鏄潬鎻愮ず璇嶈Е鍙戠殑 skill銆傛湰鍖呰嚜韬氨鏄竴涓?dsh bundle锛屼竴鏉″懡浠ゅ嵆鍙杩涙煇涓?profile锛?
```sh
npx -y @deepseek-ai/dsh plugin --profile web add dsh-modlens@3.16.6
```

杩欎細娉ㄥ唽涓€涓?`modlens_read_image` 宸ュ叿锛屽畠鐨?schema 闅忔瘡娆¤姹傛姷杈炬ā鍨嬶紙涓嶉潬瑙﹀彂鍚彂寮忥級锛岃繍琛屽悓涓€涓寘閲岃嚜甯︾殑 modlens CLI锛屽苟鎶婄粨鏋勫寲璇佹嵁浣滀负宸ュ叿鐨勬爣鍑?JSON 杈撳嚭杩斿洖銆傚紩鎿庛€佸鐢ㄦ巿鏉冨拰 guard 瑙勫垯浠嶅湪 `~/.modlens/config.json` 閲岋紝涓庡叾浠栨墍鏈?harness 鍏变韩銆俤sh 杩樺湪寮€鍙戣€呴瑙堥樁娈碉紝鎻掍欢鎺ュ彛鍙兘鍙樺寲銆傝繖涓彃浠跺埢鎰忎繚鎸佸緢灏忕殑鎺ヨЕ闈紙鍘熺敓宸ュ叿娉ㄥ唽銆佽瑙夊彉浣撴墍鐢ㄧ殑 llm 閫傞厤灞傘€侀檮浠惰鍙栧櫒锛屼互鍙婁竴涓?agent 鎵ц鍓嶉挬瀛愶級锛屽叾涓换浣曚竴澶勫彉鍔紝瀹冮兘浼氬ぇ澹版姤閿欒€屼笉鏄棤澹伴€€鍖栥€?
### 淇濇寔鏇存柊

modlens 鍙戝竷寰堥绻侊紝鑰屼袱绉嶅畨瑁呭舰鎬侀兘浼氬喕缁撳湪瑁呰繘鏉ョ殑閭ｄ釜鐗堟湰涓娿€俤sh 涓婇噸璺戜竴閬嶅畨瑁呭嵆鍙紝鐗堟湰鍙疯鐐瑰悕锛?
```sh
npx -y @deepseek-ai/dsh plugin --profile <name> add dsh-modlens@3.16.6
```

`npm view dsh-modlens version` 鍙互鏌ュ埌褰撳墠鐗堟湰鍙凤紝鏈〉鐨勭増鏈彿鍒欑敱鍙戝竷娴佺▼鑷姩鍐欏叆銆?
杩欐潯鍛戒护閲屾湁涓ゅ鏄埢鎰忕殑銆傜敤 `add` 鑰屼笉鏄?`update`锛屽洜涓?`update` 鍙湪宸茶褰曠殑 semver 鑼冨洿鍐呮尓鍔紝鑰屾櫘閫氬畨瑁呭啓杩涘幓鐨勬槸 caret 鑼冨洿锛屾墍浠ヤ竴涓綋鍒濊鍒?2.7.1 鐨?profile 鍙細鏇存柊鍒?2.8.0锛屾案杩滆繘涓嶄簡 3.x銆傜偣鍚嶇増鏈彿鑰屼笉鐢?`@latest`锛屽垯鏄洜涓?pnpm 11 浼氭墸浣忔渶杩?24 灏忔椂鍐呭彂甯冪殑鐗堟湰锛坄minimumReleaseAge`锛岄粯璁ゅ紑鍚級锛宒ist-tag 鍙湪閫氳繃杩囨护鐨勫€欓€夐噷瑙ｆ瀽锛歚@latest` 浼氳惤鍒版洿鏃х殑鐗堟湰涓婏紝鑰屼笉鏄烦杩囧喎闈欐湡銆備唬浠锋槸涓€澶╃殑鑷劧鏃堕棿锛屼笉鏄竴涓増鏈紝鍙戝竷瀵嗛泦鐨勪竴鍛ㄩ噷灏辨槸濂藉嚑涓増鏈€傜偣鍚嶇増鏈槸涓€娆℃槑纭殑鎸囧畾锛屾墍浠?pnpm 浼氳涓婂畠锛?1.1.3 璧疯繕浼氭妸杩欎竴涓増鏈綔涓哄凡鎵瑰噯鐨勪緥澶栧啓杩涜 profile 鐨?`pnpm-workspace.yaml`锛屽叾浣欎竴鍒囦粛鐣欏湪绐楀彛鍚庨潰銆?
閲嶅惎 dsh锛岀劧鍚庣‘璁ゅ疄闄呰鍒颁簡浠€涔堬細

```sh
npx -y @deepseek-ai/dsh plugin --profile <name> list
```

鏇翠弗鏍肩殑鎯呭喌锛堜綘鑷繁閰嶈繃 `minimumReleaseAge`锛宲npm 浼氭嫆缁濊€屼笉鏄壒鍑嗭級瑙乕鏁呴殰鎺掓煡](troubleshooting.zh-CN.md#dsh-鎻愮ず-declares-no-dshbundle--installed-as-a-plain-dependency)銆?
skill 绫?harness 涓婏紝skill 鏄竴涓嫹璐濆嚭鏉ョ殑鏂囦欢澶癸紝鎷疯礉浼氫繚鐣欏畨瑁呮椂鐨勭増鏈紝閲嶈窇瀹夎鍘熷湴瑕嗙洊鍗冲彲銆俙modlens doctor` 浼氳鍑哄畠鑳芥壘鍒扮殑姣忎竴浠芥嫹璐濋噷閽変綇鐨勭増鏈紝骞舵爣鍑鸿惤鍚庝簬褰撳墠 CLI 鐨勯偅浜涳紝璁╃増鏈紓绉诲湪鍧戝埌浜轰箣鍓嶅氨鍏堟毚闇插嚭鏉ャ€?
### 绮樿创杞矾寰勶紙paste-to-path锛寃eb profile锛?
杩囧幓鍦?dsh Web UI 閲岋紝**绾枃鏈ā鍨?*涓嬬矘璐村浘鐗囦細姝诲湪鍥剧墖鍑嗗叆妫€鏌ヨ繖涓€姝ャ€傛彃浠剁幇鍦ㄥ甫浜嗕竴涓祻瑙堝櫒绔崐杈癸紙鐢?dsh 鐨勫鎴风鎻掍欢绯荤粺鑷姩鍔犺浇锛夛紝鎭板ソ鍦ㄨ繖绉嶆儏鍐典笅鎺ョ绮樿创锛氬浘鐗囧瓧鑺傚彂鍒版彃浠跺湪 dsh web 鏈嶅姟鍣ㄤ笂鐨?`/modlens/paste` 璺敱锛堜粎鍥炵幆鍦板潃锛屾牎楠?magic byte锛屼笂闄?25 MB锛夛紝钀芥垚涓€涓鏈変复鏃舵枃浠讹紝杈撳叆妗嗘敹鍒扮殑鍒欐槸绾枃鏈殑鏂囦欢璺緞銆傝繖涓?Pi銆丱penCode銆丆laude Code 閫掔粰妯″瀷鐨勫舰鎬佷竴鑷达紝涔熸鏄?modlens skill 鍜?`modlens_read_image` 宸ュ叿鐨勯瑕佽Е鍙戞潯浠躲€傛秷鎭噷涓嶅甫鍥剧墖闄勪欢锛屽噯鍏ユ鏌ユ牴鏈笉浼氳Е鍙戙€?
鎺ョ鏄湁鏉′欢鐨勶紝涓旇鍐虫潈鍦?host 涓€渚э細娴忚鍣ㄥ崐杈瑰厛鍚戞彃浠惰矾鐢辫闂綋鍓嶉€変腑鐨勬ā鍨嬫槸鍚︾函鏂囨湰锛宧ost 鐢?provider 娉ㄥ唽琛ㄩ噷澹版槑鐨勬ā鍨嬪厓鏁版嵁锛坄inputModalities`锛夊洖绛旓紝鑰屼笉鏄潬鍚嶇О鐚溿€俙(modlens vision)` 鍙樹綋鍜屼换浣曞０鏄庢敮鎸佸浘鐗囪緭鍏ョ殑妯″瀷閮戒繚鐣欏師鐢熺矘璐存祦绋嬶紙鍙樹綋鍦ㄥ彂璇锋眰鏃惰浆鎹笖淇濈暀缂╃暐鍥撅紝瑙嗚妯″瀷鑷繁璇诲浘锛夛紝host 璁や笉鍑虹殑妯″瀷鍚屾牱涓嶆帴绠★細鍦?host 纭璇ユ帴绠′箣鍓嶏紝绮樿创涓€寰嬭蛋鍘熺敓璺緞銆傛ā鍨嬪厓鏁版嵁閲屾病鏈夊０鏄庤緭鍏ユā鎬佺殑锛屼竴寰嬬畻璁や笉鍑猴細鍏冩暟鎹己澶辩粷涓嶅綋鎴愩€屽凡纭绾枃鏈€嶃€傝鍐宠繕鏈?60 绉掓椂鏁堬紝妯″瀷涓€斿彉浜嗕細閲嶆柊闂锛屼笉浼氭案杩滀俊鏃х瓟妗堛€傚湪鎻掍欢閰嶇疆琛岄噷璁?`pasteToPath: false` 鍙暣浣撳叧鎺夎繖涓姛鑳斤細绛栫暐绔偣 404 鏃舵祻瑙堝櫒鍗婅竟褰诲簳鍋滄墜銆傝嫢璺敱鍦ㄨ鍐崇‘璁ゅ悗涓€旀秷澶憋紝澶辫触缁撴灉杩斿洖鍓嶉偅涓煭鏆傜獥鍙ｏ紙涓€娆℃湰鍦板線杩旓級鍐呭彂鐢熺殑绮樿创浼氫涪澶憋紝涔嬪悗瀹㈡埛绔竻绌哄叏閮ㄨ鍐筹紝鍚庣画绮樿创涓€寰嬭蛋鍘熺敓璺緞銆?