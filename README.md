ワランティ分析
==============================
クレームデータを分析して、早期に不具合を検知し根本原因を特定します。企業としては、ワランティコストの削減、顧客満足度の向上が期待されます。

<br><br>
<img src="https://user-images.githubusercontent.com/3815677/94828618-9c35f080-0444-11eb-8903-46edf2d0990f.gif" width = 800><br/>
<br><br>

#### よくある課題と対策
- テキスト分析のコスト
  - 課題：テキストデータを含むクレームデータの処理を人力で行っているためコストが高い  
  - 対策：機械学習によるテキスト分類モデルの活用
- 過去の不具合情報の活用
  - 課題：過去の膨大なクレームデータが構造化されていないため、検索が難しかったり、開発・設計に生かせていない
  - 対策：Knowledge Graph を構築し、不具合情報の関連づけることで、活用しやすくする

## Sample

| 分析方法 | ツール | 利用データ | 内容 | 
| --- | --- | --- | --- |
| Knowledge Graph (キーフレーズ単位) | [Azure Machine Learning](https://azure.microsoft.com/ja-jp/services/machine-learning/), [Azure Cognitive Service](https://azure.microsoft.com/ja-jp/services/cognitive-services/), [Power BI](https://powerbi.microsoft.com/ja-jp/)| 自動車のリコールデータ(MLIT) | クレームデータからキーフレーズを抽出し、「不具合の部位」「原因」「対策」を共起ネットワークで可視化| 






## 開発環境の準備

[Azure Machine Learning の Compute Instance](https://docs.microsoft.com/ja-jp/azure/machine-learning/concept-compute-instance) で下記コマンドを実行します。
**conda 仮想環境 (warranty) の作成**
```bash
conda create -n warranty python=3.6 
conda activate warranty
pip install -r requirements.txt
```

**Jupyter Kernel の作成**
```bash
export env_name="warranty"
ipython kernel install --user --name=$env_name  --display-name=$env_name
```

### 利用するデータ
公開されているクレームデータ
- [自動車のリコール・不具合情報 (MLIT)](http://www.mlit.go.jp/jidosha/carinf/rcl/data.html)
  - 本リポジトリではこちらの公開情報を利用
- [リコール情報 (METI)](https://www.meti.go.jp/product_safety/recall/index.html)
- [製品事故情報・リコール情報 (NITE)](https://www.nite.go.jp/index.html)
  - [検索サイト](https://www.nite.go.jp/jiko/jiko-db/recall/search/) にて検索可能
    - 全件抽出したい場合は、"半角スペース" をキーワード入力し、条件は "１・２・３のどれかを満たしているもの" に設定

### 分析方法
- キーフレーズ抽出
- テキスト分類
- Word Cloud
- Knowledge Graph
- トピック抽出 (not yet implemented)
- Sanky Diagram (not yet implemented)
- ネットワーク分析 (not yet implemented)
...


### 利用するサービス
- [Azure Machine Learning](https://azure.microsoft.com/ja-jp/services/machine-learning/)
  - Jupyter による Data Wrangling
  - 機械学習・深層学習モデルの構築と運用 (not yet implemented)
- [Azure Text Analytics (Azure Cognitive Service)](https://azure.microsoft.com/ja-jp/services/cognitive-services/)
  - キーフレーズ抽出
- [Power BI](https://powerbi.microsoft.com/ja-jp/)
  -　データ可視化

※ Ubuntu or Mac での動作を想定しています。Windows など他の環境では文字コードの相違による問題が発生する場合があります。
