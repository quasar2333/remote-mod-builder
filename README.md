# 馃殌 Remote Mod Builder

涓€涓€氱敤鐨勮繙绋?Minecraft 妯＄粍鏋勫缓宸ュ叿銆傛棤闇€鏈湴鐜锛屽叏绋嬩簯绔瀯寤猴紒

## 鉁?鍔熻兘鐗规€?

- 馃敡 **鏀寔浠绘剰浠撳簱** - 杈撳叆浠撳簱 URL 鎴?`owner/repo` 鏍煎紡鍗冲彲
- 馃尶 **鏀寔浠绘剰鍒嗘敮/鏍囩** - 鎸囧畾 `main`銆乣1.21.8`銆乣v1.0.0` 绛?
- 鈽?**澶?Java 鐗堟湰** - 鏀寔 Java 8/11/17/21
- 馃敤 **鑷姩妫€娴嬫瀯寤虹郴缁?* - Gradle 鎴?Maven 鑷姩璇嗗埆
- 馃摝 **鑷畾涔夋瀯寤哄懡浠?* - 鍙鐩栭粯璁ゆ瀯寤哄懡浠?
- 馃搧 **鐏垫椿鐨勪骇鐗╄矾寰?* - 鑷畾涔夐渶瑕佹敹闆嗙殑浜х墿
- 馃彿锔?**鑷姩鍙戝竷 Release** - 鏋勫缓鎴愬姛鍚庤嚜鍔ㄥ垱寤?GitHub Release

## 馃幆 浣跨敤鏂规硶

### 鏂规硶涓€锛氶€氳繃 GitHub Actions 椤甸潰瑙﹀彂

1. 鍓嶅線 [Actions 椤甸潰](../../actions/workflows/build-any-mod.yml)
2. 鐐瑰嚮 **"Run workflow"**
3. 濉啓鍙傛暟锛?
   - **Repository URL**: `https://github.com/FabricMC/yarn` 鎴?`FabricMC/yarn`
   - **Branch**: `1.21.8`
   - **Java Version**: `21`
   - **Build Command**: (鐣欑┖鑷姩妫€娴?
   - **Artifact Path**: `build/libs/*.jar`
4. 鐐瑰嚮 **"Run workflow"** 寮€濮嬫瀯寤?

### 鏂规硶浜岋細浣跨敤 GitHub CLI

```bash
gh workflow run build-any-mod.yml \
  --repo quasar2333/remote-mod-builder \
  -f repo_url="FabricMC/yarn" \
  -f branch="1.21.8" \
  -f java_version="21"
```

## 馃搵 鍙傛暟璇存槑

| 鍙傛暟 | 蹇呭～ | 榛樿鍊?| 璇存槑 |
|------|------|--------|------|
| `repo_url` | 鉁?| - | 鐩爣浠撳簱 URL 鎴?`owner/repo` 鏍煎紡 |
| `branch` | 鉁?| `main` | 瑕佹瀯寤虹殑鍒嗘敮鎴栨爣绛惧悕 |
| `java_version` | 鉁?| `21` | Java 鐗堟湰 (8/11/17/21) |
| `build_command` | 鉂?| 鑷姩妫€娴?| 鑷畾涔夋瀯寤哄懡浠?|
| `artifact_path` | 鉂?| `build/libs/*.jar` | 浜х墿璺緞锛岄€楀彿鍒嗛殧 |

## 馃敡 绀轰緥

### 鏋勫缓 Yarn Mappings 1.21.8
```yaml
repo_url: FabricMC/yarn
branch: 1.21.8
java_version: 21
```

### 鏋勫缓 Fabric API
```yaml
repo_url: FabricMC/fabric
branch: 1.21.4
java_version: 21
```

### 鏋勫缓 Forge Mod (鑷畾涔夊懡浠?
```yaml
repo_url: owner/forge-mod
branch: 1.20.1
java_version: 17
build_command: ./gradlew build -x test
artifact_path: build/libs/*.jar,build/resources/**
```

## 馃摜 鑾峰彇鏋勫缓浜х墿

鏋勫缓瀹屾垚鍚庯紝浣犲彲浠ワ細

1. **浠?Artifacts 涓嬭浇** - 鍦?Actions 杩愯椤甸潰搴曢儴
2. **浠?Releases 涓嬭浇** - 鍦ㄤ粨搴撶殑 Releases 椤甸潰

---

Made with 鉂わ笍 by [quasar2333](https://github.com/quasar2333)
