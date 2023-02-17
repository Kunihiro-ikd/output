1. アノテーションの形式
・ファイル形式: json形式
・文字コード: utf-8
・ファイル名: ***.json (*** = 対応する画像ファイル名と同じ(***.jpgの***).)
・詳細:
  - attributes:
      - 年代: "古典籍|近代"
      - データ公開: "可|不可"
      - URL
      - タイトル
      - シリーズ
      - 版表示
      - 巻次
      - 著者
      - 出版者
      - 冊数（ページ数・大きさ）
      - ISSN
      - ISBN
      - 出版年
      - 公開範囲
      - 件名
      - 古典籍資料種別
  - labels []:
      - category: "1_overall|2_handwritten|3_typography|4_illustration|5_stamp|6_headline|7_caption|8_textline|9_table"
      - box2d:
          - x1: int
          - y1: int
          - x2: int
          - y2; int
・注意点:
   - "年代"において, "古典籍"は"古典籍資料", "近代"は"明治期以降刊行資料"を意味する.
   - "データ公開"において, "可"は"対応する画像を一般公開してもよい", "不可"は"対応する画像を一般公開してはならない"
     ことを意味する. 
   - (x1, y1, x2, y2)は(left, top, right, bottom)に対応する.

2. 提出ファイルの形式
・ファイル形式: json形式
・ファイル名: ***.json (*** = 自分の好きな名前(e.g. submit))
・詳細:
  - image_file_0:
      - category_1: [[x1, y1, x2, y2],...]
      - category_2: [[x1, y1, x2, y2],...]
      ...
  - image_file_1:
      - category_1: [[x1, y1, x2, y2],...]
      - category_2: [[x1, y1, x2, y2],...]
      ...
  ...
・注意点:
  - それぞれの画像に対して, それぞれのラベルについて, bounding boxを確信度が高い順に並べること.
  - "9_table"は評価対象外となるので, 予測する際ははずすこと.
  - (x1, y1, x2, y2)は(left, top, right, bottom)に対応する.
  - それぞれの画像に対して, ラベルの種類数は異なる.
      - e.g.) image_file_0: ["1_overall", "8_textline"], image_file_1: ["1_overall"]
  - "sample_submit.json"も参照すること.