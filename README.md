# Flow業務用FileMakerのファイル複製法
年始になると，その年の分のファイルを新たに作成する必要がある．  
年に1回の作業であり，全員が経験することでもないと思われるのでFileMakerのファイル複製方法等を記録しておく．
## FileMakerファイルデータの保管場所
FileMakerファイルデータはMy Book (外付けハード) の中に保存されている．  
例えば，2023年版だと  `/Volumes/My Book/Macintosh HD 2/documents/FLOW業務用データ/Flow 報告書/2023フローⅡ`に保存してある．  

---
## FileMakerファイルの複製方法
以下の複製方法は[ファイルの保存とコピー](https://fmhelp.filemaker.com/help/12/fmp/jp/html/fmp_basics.3.33.html)のサイトを参考にした．  
1. [ファイル]メニューから[名前を付けて保存...]を選択する．  
   <img width="300" alt="CleanShot 2023-01-05 at 09 04 53@2x" src="https://user-images.githubusercontent.com/89718855/210673501-67337638-7c50-4a8e-938f-a1435ff47206.png">

2. 複製したファイルを保存するディレクトリを所定の場所 (`/Volumes/My Book/Macintosh HD 2/documents/FLOW業務用データ/Flow 報告書`) に新規作成 (フォルダ名は"<年>フローII"などとする) する．
3. [名前:]にファイル名を入力 ("<年>遺伝子細胞療法部.fmp12") する．
4. [タイプ:]で，"データなしのコピー"のオプションを選択する．
 - ここで他のオプションを選ぶと，複製元のファイルのデータ毎複製されてしまう．  

    <img width="600" alt="CleanShot 2023-01-05 at 09 06 30@2x" src="https://user-images.githubusercontent.com/89718855/210673999-9b3acbe1-7a3f-45e1-b09b-01e55fcf2eeb.png">
5. [保存]をクリックする．
---
## ファイル複製後の各種設定
ファイルを複製した後，データを初めてインポートする際はルーチンの設定ではなくなっているため，多少設定をやり直す必要がある．一度設定すれば，以降はそれがデフォルトになるようで毎回設定する必要はない．  
※ただし，以下の方法は我流 (文責: 石原) なので，もし不都合などあれば適宜改訂してください．
1. 解析ファイル (Excelファイル) をインポートする際に"Filemaker import"オプションを選択する．
   <img width="300" alt="CleanShot 2023-01-05 at 10 15 26@2x" src="https://user-images.githubusercontent.com/89718855/210680285-95f80044-e7c6-4642-8485-a09ab95ba538.png">
2. [インポート先:]で"現在のテーブル（「ﾌﾛｰII」）"を選択し，下の方にある"フィールド名が含まれる最初のレコードはインポートしない"にチェックを入れる．
3. [配置順:]を"照合名順"を選択してインポートを実行する．  
   <img width="450" alt="CleanShot 2023-01-05 at 10 15 48@2x" src="https://user-images.githubusercontent.com/89718855/210680551-5a766357-e359-412a-b54f-b9ffdc6e9af0.png">
---
## Mergeファイルのエクスポート時の注意点
新たにFileMakerファイルを複製した後，初めてMergeファイル (`.mer`) をエクスポートする際も普段と設定がやや違っているので注意が必要である．
1. 通常通り，FileMakerのエクスポートを行う．
2. デフォルト拡張子が`.tab`になっているので"Mergeファイル"に変換する．  
   <img width="600" alt="CleanShot 2023-01-05 at 10 16 11@2x" src="https://user-images.githubusercontent.com/89718855/210680883-5e444d28-4868-47ea-b778-dd473c182b1d.png">
 
3. エクスポートするフィールドで"現在のテーブル（「ﾌﾛｰII」）"にチェックを入れる．
- "現在のレイアウト (...)"を選択したままエクスポートしようとすると，バーコード情報がエクスポートされない．  
   <img width="450" alt="CleanShot 2023-01-05 at 10 16 32@2x" src="https://user-images.githubusercontent.com/89718855/210681530-5397ad7e-25e2-4b50-b216-b498a21a22ac.png">

4. "全てを移動"を実行すると[フィールドのエクスポート順:]に各項目が表示される．  
   <img width="450" alt="CleanShot 2023-01-05 at 10 16 51@2x" src="https://user-images.githubusercontent.com/89718855/210682688-446d7b9e-cd3e-4327-babb-6357deb2df74.png">

5. [出力ファイルの文字セット:]で"日本語(Shift-JIS)"オプションを選択してエクスポートを実行する．
6. 以降は，通常通りの操作でMergeファイルをExcelファイルへ変換すればよい．
