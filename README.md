# Feng-Kai Huang 個人學術網站

這個 repository 存放 [leohuang0511.github.io](https://leohuang0511.github.io/) 的 Jekyll 原始檔，由 GitHub Pages 建置與發布。

## Conda 環境與本機預覽

建立隔離環境並安裝 Ruby、編譯工具：

~~~sh
conda create -n personal-site -c conda-forge ruby=3.2 c-compiler cxx-compiler make -y
conda activate personal-site
gem install bundler
ln -sfn "$CONDA_PREFIX/bin/ruby" "$CONDA_PREFIX/share/rubygems/bin/ruby"
bundle install
bundle exec jekyll serve --host 127.0.0.1
~~~

Conda Ruby 的 gem 指令需要上述 symlink，讓 bundle 等 gem 啟動器找到環境中的 Ruby。開啟 http://localhost:4000 預覽。VS Code Remote SSH 可在 Ports 面板轉發遠端 4000 埠。

重新連線後先執行 conda activate personal-site，再執行 bundle exec jekyll serve --host 127.0.0.1。修改 Markdown、YAML 或 CSS 後，Jekyll 會自動重建頁面。

## 更新網站內容

| 要更新的內容 | 編輯位置 |
| --- | --- |
| 姓名、職稱、學校、Email、大頭照、履歷與社群連結 | _config.yml |
| 首頁自我介紹與精選論文 | index.md |
| 研究方向與研究專案 | research.md、_data/optional_content.yml |
| 論文資訊、連結與縮圖 | _data/publications.yml |
| 學歷、經歷、獎項、演講、教學、服務與近況 | _data/optional_content.yml |
| 網站版型與導覽列 | _layouts/homepage.html |
| 顏色、間距與手機版樣式 | assets/css/site.css |

### 選配區塊與開關

在 _data/optional_content.yml 找到對應分類，新增資料後將該分類的 enabled: false 改成 enabled: true 即可公開。各筆資料可使用：

- title：項目名稱
- date：日期或年份
- detail：補充說明，支援 Markdown
- url：相關連結

目前學歷、經歷、獎項、演講、教學、研究專案與近況都預設關閉；內容填好再開啟。沒有資料的區塊不會顯示。CV 導覽項目會在至少一個 CV 區塊已啟用且有資料時出現。現有會議與期刊審稿服務已啟用，位於 cv.service。

### 新增論文

在 _data/publications.yml 的 main 清單最上方新增論文，最新的放前面。欄位包含 title、authors、conference_short、conference、pdf、code、page、bibtex、notes 與 image。縮圖放在 assets/img/。

## 發布網站

將修改 commit 並推送到 GitHub Pages 使用的分支，GitHub Pages 會建置並發布網站。根目錄的 CNAME 用於自訂網域，請保留。

## 目錄導覽

- _config.yml：網站基本資料與 Jekyll 設定
- _data/：論文及可選個人資料
- _includes/、_layouts/：共用頁面版型
- assets/：樣式、圖片、履歷與證書
- index.md、research.md、publications.md、cv.md：網站頁面
- resume/：LaTeX 履歷原始檔與 PDF
- google_scholar_crawler/、.github/workflows/：引用資料自動更新流程
