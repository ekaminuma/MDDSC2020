 2020年にGoogle Classroonで公開していた資料です。
  
---
**「NGS解析入門」第１回「 NGS配列の基礎知識と変異注釈」

＜第１回実習コード＞
-  [NGS解析入門①A.ipynb](NGS解析入門①A.ipynb)＝＞溶血性レンサ球菌WGS配列のクオリティコントロール
-  [NGS解析入門①B.ipynb](NGS解析入門①B.ipynb)＝＞個体NA18507の21番染色体変異の機能注釈


＜機能注釈用の個体NA18507のURL＞

- 1000 genomesのNA18507個体情報
  - http://www.internationalgenome.org/data-portal/sample/NA18507

- NA18507の21番染色体変異vcfとsnpeff機能注釈実行結果ファイル
  - https://data.bits.vib.be/pub/trainingen/NGSDNA2013/ex7-files/snpeff_chr21-results/

＜空間遺伝子発現解析(スライドp.37)のデモ＞
 - https://www.10xgenomics.com/jp/spatial-transcriptomics/

---
---
**「NGS解析入門」第2回「 NGS配列からの微生物叢解析」
- 第2回微生物叢解析のURLとコマンド

＜ヒトマイクロバイオームのα多様性＞
- https://www.ncbi.nlm.nih.gov/sra　NCBI SRA
- 検索キーワード：human duodenal mucosa

＜SRAメタゲノムの解析結果DB＞
- http://microbedb.jp/

＜分類済メタゲノムをキーワードで絞込＞
- http://leamicrobe.jp/

＜遺伝研スパコンの利用申請＞
- https://sc2.ddbj.nig.ac.jp/index.php/ja-new-application
-  ※解説動画（ngs_supercom.mp4）とスライド（EK_NGS解析入門_スパコン利用解説スライド.pdf）をClassroomに掲載しました。

＜TeraTermソフトウェアのインストール＞
- https://ja.osdn.net/projects/ttssh2/

＜遺伝研スパコン：シェルスクリプトのコマンド＞
```
qlogin

cp /home/kaminuma/.bashrc_dsc ~/.bashrc
source ~/.bashrc
cp /home/kaminuma/.bash_profile_dsc ~/.bash_profile
source ~/.bash_profile

cp /home/kaminuma/tmp_data/test.sh .
qsub test.sh

ls -l
cat ~/test.sh.o325
cat ~/test.sh.e325

qstat
または
qstat -u "*"　
qdel -u kaminuma
```

＜遺伝研スパコン：qiime2解析のコマンド＞
```
wget https://docs.qiime2.org/2017.12/data/tutorials/moving-pictures/table.qza

singularity pull --name qiime.simg docker://qiime2/core

singularity run qiime.simg /bin/bash

(qiime2-2019.4) $ qiime diversity beta --i-table table.qza --p-metric braycurtis --o-distance-matrix output.qza

(qiime2-2019.4) $ exit

unzip output.qza
cat ***/data/distance-matrix.tsv
```
