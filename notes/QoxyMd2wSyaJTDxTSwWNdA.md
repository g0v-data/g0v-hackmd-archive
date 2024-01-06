# SBOM(SOFTWARE BILL OF MATERIALS) 工具探索

SBOM(SOFTWARE BILL OF MATERIALS)概念就是一個軟體的物料表，也就是詳列個別軟體包含哪些獨立元件、函式庫等，藉由這個物料表可以知道軟體的組成，或是進一步比對使用中的元件版本是否存在已知的問題。

環繞著 SBOM 主要就是物料表檔案的產出以及基於該檔案進行掃描工作，部份工具會同時包含兩者。在物料表檔案部份主要有兩種格式：

1. [SPDX](https://spdx.dev/) - 由 Linux 基金會主導建立的格式，主要用在軟體授權管理，也就是確保個別軟體使用的軟體授權不會產生衝突。
2. [CycloneDX](https://cyclonedx.org/) - 由 OWASP 基金會主導的格式，主要著眼在軟體元件安全問題的管理。

兩個基金會都有釋出工具來產出該格式的 SBOM( [SPDX](https://github.com/opensbom-generator/spdx-sbom-generator) 、[CycloneDX](https://github.com/CycloneDX/cdxgen) )， CycloneDX 也有提供[工具](https://github.com/CycloneDX/cyclonedx-cli)進行兩個格式的轉換，只是有時候轉換出來的格式會遇到相容性問題，也許是版本差異或是兩者本質上的不同造成。

因為軟體授權並不會經常性異動，而軟體安全領域則是更新非常頻繁，加上 CycloneDX 格式也能夠包含元件的授權資訊，可以發現環繞著 CycloneDX 的生態系會完整許多。

下面介紹環繞著 CycloneDX 深入所發現的工具與已知特色：
1. [cdxgen](https://github.com/CycloneDX/cdxgen) - 官方的指令化工具，可以針對常見的程式語言元件管理工具(package manager)檔案(例如： package-lock.json )轉換成 SBOM。
    * 功能基本但是輸出穩定，其他工具偶爾會遇到 package manager file 本身資訊錯誤而衍生問題。
    * 掃描整個目錄時會針對獨立的 javascript 檔案產出元件資訊，即使檔案並未列在 package manager file 中。
2. [syft](https://github.com/anchore/syft) - 由資安公司所釋出的工具，除了從元件管理工具的資訊之外，還可以針對特定語言的打包檔案(例如 java 環境的 *.jar )進行掃描，而且產出的 SBOM 會自動附加 CPE 資訊方便比對[NIST 的弱點資料庫](https://nvd.nist.gov/)。
    * 產出的 SBOM 附加資訊比較豐富，特別是針對 CPE 的部份，以及掃描 *.jar 檔案產出的資訊。
3. [osv](https://github.com/google/osv-scanner) - 由 Google 推出的元件弱點掃描工具，主要針對開放原始碼的軟體元件，輸入帶有 purl 欄位的 SBOM (CycloneDX預設就會產生)即可檢查元件已知問題。
    * 只針對開放原始碼元件，所以商業軟體元件大概還是要透過其他資料庫比對。
    * 會即時連線遠端資料庫進行比對，因此需要確保執行當下能夠連上網路。
4. [trivy](https://github.com/aquasecurity/trivy) - 一個整合性的工具，可以用來產出 SBOM ，同時可以進行包含弱點(vuln)、容器設定檔(config)、安全性檔案(secret)與授權(license)的檢查，需要注意全部檢查會需要很長時間，檢查弱點的資料庫包含 osv 。
    * 應該是目前已知生態系最完整的工具，只是因為功能太多還沒能夠深入檢驗。
    * 會自動在本地端建立與更新資料庫，原則上不會造成大量網路連線。
5. [grype](https://github.com/anchore/grype) - 可以針對輸入的 SBOM 跟公開的弱點資料庫比對，只是目前(2023/11/20)還沒有把 osv 資料庫整合到其中。
    * 跟 trivy 比起來相對沒有那麼活躍，會建議直接使用 trivy 進行弱點掃描。
    * 會自動在本地端建立與更新資料庫，原則上不會造成大量網路連線。
6. [purl2cpe](https://github.com/scanoss/purl2cpe) - 一個公開的對應表，主要用在把 purl 轉換成 cpe ，之後就可以用來檢索[NIST 的弱點資料庫](https://nvd.nist.gov/)。
    * 不過因為 trivy/grype 等工具都可以直接比對 NIST 資料庫，加上 syft 也可以直接產出帶有 cpe 資訊的 SBOM ，就不太需要自己處理轉換工作。
    * [轉換的程式與範例](https://gist.github.com/kiang/e90f5076812c44ca99872b12818ba5ad)

---
參考資料：
1. https://scribesecurity.com/blog/spdx-vs-cyclonedx-sbom-formats-compared/
2. https://www.cisa.gov/resources-tools/resources/types-software-bill-materials-sbom