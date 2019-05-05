##modelのオプションであるoptional: trueとは
これはbelongs_toの外部キーのnilを許可することである。

##自己結合モデル
 has_many :children, class_name: 'Area', foreign_key: 'parent_id', dependent: :destroy
 belongs_to :parent, class_name: 'Area', optional: true 
**children, parentの部分は任意の名前でOKである。**

この例で言うとbelongs_to :parentになっている部分はテーブルのカラムで言うparent_idに当たる。
optional: trueとなっているので値がnilであっても許可される構造になっている。

自己結合をとっているのでhas_many :childrenとしてforeign_keyをparent_idとしている。
これを定義することで@area.children, @area.parentが呼べる。