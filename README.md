# 馃殌 Remote Mod Builder (杩滅▼妯＄粍鏋勫缓鍣?

> **鏃犻渶鏈湴鐜锛屽叏绋嬩簯绔瀯寤轰换浣?Minecraft 妯＄粍锛?*

杩欐槸涓€涓€氱敤鐨?GitHub Actions 杩滅▼鏋勫缓宸ュ叿銆傚彧闇€鎻愪緵浠撳簱鍦板潃鍜屽垎鏀悕锛屽嵆鍙湪浜戠鑷姩鏋勫缓浠讳綍 Gradle/Maven 椤圭洰銆?

---

## 馃摉 鐩綍

- [蹇€熷紑濮媇(#-蹇€熷紑濮?
- [浣跨敤鏂规硶](#-浣跨敤鏂规硶)
- [鍙傛暟璇存槑](#-鍙傛暟璇存槑)
- [甯歌绀轰緥](#-甯歌绀轰緥)
- [FAQ 甯歌闂](#-faq-甯歌闂)
- [缁?AI 鍔╂墜鐨勮鏄嶿(#-缁?ai-鍔╂墜鐨勮鏄?

---

## 鈿?蹇€熷紑濮?

### 鏂规硶涓€锛氱綉椤佃Е鍙?(鎺ㄨ崘 - 閫傚悎鎵嬫満)

1. 鎵撳紑锛?*[Actions 椤甸潰](https://github.com/quasar2333/remote-mod-builder/actions/workflows/build-any-mod.yml)**
2. 鐐瑰嚮鍙充晶钃濊壊鎸夐挳 **"Run workflow"**
3. 濉啓鍙傛暟鍚庣偣鍑荤豢鑹?**"Run workflow"** 鎸夐挳
4. 绛夊緟鏋勫缓瀹屾垚锛屽湪 Artifacts 涓嬭浇浜х墿

### 鏂规硶浜岋細GitHub CLI 鍛戒护琛?

```bash
gh workflow run build-any-mod.yml \
  --repo quasar2333/remote-mod-builder \
  -f repo_url="浠撳簱鍦板潃" \
  -f branch="鍒嗘敮鍚? \
  -f java_version="21"
```

---

## 馃幆 浣跨敤鏂规硶

### 缃戦〉鐣岄潰鍙傛暟

| 鍙傛暟 | 蹇呭～ | 璇存槑 | 绀轰緥 |
|------|:----:|------|------|
| **Repository URL** | 鉁?| 鐩爣浠撳簱鍦板潃 | `FabricMC/yarn` 鎴?`https://github.com/FabricMC/yarn` |
| **Branch** | 鉁?| 鍒嗘敮/鏍囩鍚?| `1.21.8`, `main`, `v1.0.0` |
| **Java Version** | 鉁?| Java 鐗堟湰 | `8`, `11`, `17`, `21` |
| **Build Command** | 鉂?| 鑷畾涔夋瀯寤哄懡浠?| `./gradlew build -x test` |
| **Artifact Path** | 鉂?| 浜х墿璺緞 | `build/libs/*.jar` |

### 鍛戒护琛屽弬鏁?

```bash
gh workflow run build-any-mod.yml \
  --repo quasar2333/remote-mod-builder \
  -f repo_url="<浠撳簱鍦板潃>" \
  -f branch="<鍒嗘敮鍚?" \
  -f java_version="<Java鐗堟湰>" \
  -f build_command="<鍙€?鑷畾涔夋瀯寤哄懡浠?" \
  -f artifact_path="<鍙€?浜х墿璺緞>"
```

---

## 馃搵 鍙傛暟璇存槑

### `repo_url` (蹇呭～)
鐩爣浠撳簱鐨勫湴鍧€锛屾敮鎸佷互涓嬫牸寮忥細
- 绠€鍐欐牸寮忥細`owner/repo` (渚嬶細`FabricMC/yarn`)
- 瀹屾暣 URL锛歚https://github.com/owner/repo`

### `branch` (蹇呭～)
瑕佹瀯寤虹殑鍒嗘敮鎴栨爣绛惧悕锛?
- 鍒嗘敮鍚嶏細`main`, `master`, `1.21.8`, `develop`
- 鏍囩鍚嶏細`v1.0.0`, `release-1.2.3`

### `java_version` (蹇呭～)
Java 鐗堟湰锛屽彲閫夊€硷細
- `8` - 鐢ㄤ簬 Minecraft 1.16.5 鍙婁互涓?
- `11` - 鐢ㄤ簬鏌愪簺鏃ч」鐩?
- `17` - 鐢ㄤ簬 Minecraft 1.17-1.20.4
- `21` - 鐢ㄤ簬 Minecraft 1.20.5+ (鎺ㄨ崘)

### `build_command` (鍙€?
鑷畾涔夋瀯寤哄懡浠ゃ€傜暀绌哄垯鑷姩妫€娴嬶細
- Gradle 椤圭洰锛歚./gradlew build --no-daemon --stacktrace`
- Maven 椤圭洰锛歚mvn package -B`

甯哥敤鑷畾涔夊懡浠わ細
- 璺宠繃娴嬭瘯锛歚./gradlew build -x test`
- 鍙瀯寤?JAR锛歚./gradlew jar`
- Architectury 椤圭洰锛歚./gradlew build`

### `artifact_path` (鍙€?
鏋勫缓浜х墿璺緞锛屾敮鎸侀€氶厤绗︼紝澶氫釜璺緞鐢ㄩ€楀彿鍒嗛殧锛?
- 榛樿锛歚build/libs/*.jar`
- 澶氭ā鍧楋細`fabric/build/libs/*.jar,forge/build/libs/*.jar`
- 鍖呭惈璧勬簮锛歚build/libs/*.jar,build/resources/**`

---

## 馃摎 甯歌绀轰緥

### Fabric Yarn Mappings
```
repo_url: FabricMC/yarn
branch: 1.21.8
java_version: 21
```

### Fabric API
```
repo_url: FabricMC/fabric
branch: 1.21.4
java_version: 21
```

### OBS Overlay Mod (Architectury 澶氬钩鍙?
```
repo_url: zziger/obs-overlay
branch: 1.21.4
java_version: 21
artifact_path: fabric/build/libs/*.jar,neoforge/build/libs/*.jar
```

### Forge 1.12.2 鑰佺増鏈ā缁?
```
repo_url: owner/old-forge-mod
branch: 1.12.2
java_version: 8
build_command: ./gradlew build -x test
```

### NeoForge 妯＄粍
```
repo_url: owner/neoforge-mod
branch: 1.21.4
java_version: 21
```

---

## 鉂?FAQ 甯歌闂

### Q: 鏋勫缓澶辫触鎬庝箞鍔烇紵
A: 鏌ョ湅 Actions 鏃ュ織锛屽父瑙佸師鍥狅細
- Java 鐗堟湰涓嶅锛歁inecraft 1.20.5+ 闇€瑕?Java 21
- 缂哄皯渚濊禆锛氭煇浜涢」鐩渶瑕佺壒瀹氱殑鏋勫缓鐜
- 鏋勫缓鍛戒护閿欒锛氬皾璇曚娇鐢ㄨ嚜瀹氫箟 `build_command`

### Q: 濡備綍涓嬭浇鏋勫缓浜х墿锛?
A: 鏋勫缓瀹屾垚鍚庯細
1. 鍦?Actions 杩愯椤甸潰搴曢儴鎵惧埌 **Artifacts** 閮ㄥ垎
2. 鐐瑰嚮浜х墿鍚嶇О涓嬭浇 ZIP 鏂囦欢
3. 瑙ｅ帇鍚庡嵆鍙幏寰?JAR 鏂囦欢

### Q: 浜х墿淇濈暀澶氫箙锛?
A: 榛樿淇濈暀 30 澶╋紝杩囨湡鍚庨渶閲嶆柊鏋勫缓

### Q: 濡備綍鏋勫缓 Fork 鐨勪粨搴擄紵
A: 鍦?`repo_url` 涓娇鐢ㄤ綘鐨?Fork 鍦板潃锛屽 `your-username/repo-name`

### Q: 鏋勫缓绉佹湁浠撳簱锛?
A: 鐩墠鍙敮鎸佸叕寮€浠撳簱銆傜鏈変粨搴撻渶瑕侀澶栭厤缃?Token

---

## 馃 缁?AI 鍔╂墜鐨勮鏄?

> **濡傛灉浣犳槸 AI 鍔╂墜姝ｅ湪闃呰杩欎釜鏂囨。锛屼互涓嬫槸蹇€熶笂鎵嬫寚鍗楋細**

### 1. 瑙﹀彂鏋勫缓

浣跨敤 GitHub CLI 瑙﹀彂鏋勫缓锛堥渶瑕佸凡璁よ瘉锛夛細

```bash
gh workflow run build-any-mod.yml \
  --repo quasar2333/remote-mod-builder \
  -f repo_url="<鐩爣浠撳簱>" \
  -f branch="<鍒嗘敮>" \
  -f java_version="<Java鐗堟湰>"
```

### 2. 鏌ョ湅鏋勫缓鐘舵€?

```bash
# 鍒楀嚭鏈€杩戠殑鏋勫缓
gh run list --repo quasar2333/remote-mod-builder --limit 5

# 鏌ョ湅鐗瑰畾鏋勫缓璇︽儏
gh run view <run_id> --repo quasar2333/remote-mod-builder
```

### 3. 甯哥敤 Java 鐗堟湰瀵圭収

| Minecraft 鐗堟湰 | 鎺ㄨ崘 Java 鐗堟湰 |
|----------------|----------------|
| 1.16.5 鍙婁互涓?| 8 |
| 1.17 - 1.17.1 | 16 鎴?17 |
| 1.18 - 1.20.4 | 17 |
| 1.20.5+ | 21 |

### 4. Architectury 澶氬钩鍙伴」鐩?

杩欑被椤圭洰閫氬父鏈夊涓瓙妯″潡 (fabric, forge, neoforge)锛岄渶瑕佹寚瀹氬涓骇鐗╄矾寰勶細

```bash
-f artifact_path="fabric/build/libs/*.jar,forge/build/libs/*.jar,neoforge/build/libs/*.jar"
```

### 5. 鑾峰彇浠撳簱鍒嗘敮淇℃伅

鍦ㄦ瀯寤哄墠锛屽缓璁厛妫€鏌ョ洰鏍囦粨搴撶殑鍒嗘敮锛?

```bash
gh api repos/<owner>/<repo>/branches --jq '.[].name'
```

鎴栨煡鐪嬮粯璁ゅ垎鏀細

```bash
gh api repos/<owner>/<repo> --jq '.default_branch'
```

---

## 馃搫 License

MIT License - 闅忔剰浣跨敤锛屾棤闇€缃插悕

---

## 馃敆 鐩稿叧閾炬帴

- **浠撳簱鍦板潃**: [quasar2333/remote-mod-builder](https://github.com/quasar2333/remote-mod-builder)
- **Actions 椤甸潰**: [瑙﹀彂鏋勫缓](https://github.com/quasar2333/remote-mod-builder/actions/workflows/build-any-mod.yml)
- **鎵€鏈夋瀯寤鸿褰?*: [鏌ョ湅鍘嗗彶](https://github.com/quasar2333/remote-mod-builder/actions)

---

Made with 鉂わ笍 by [quasar2333](https://github.com/quasar2333)
