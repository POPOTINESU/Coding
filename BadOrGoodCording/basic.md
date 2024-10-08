# 悪しきコーディングの弊害

## 命名規則

 ❌ IntやFlagといったプログラミング用語を変数名として使用すること
	どの変数で何をしているのか分からない

❌ 連番命名: list_1, list_2などただ連番になっているだけで、なにをしているのか分からないもの

🙆‍♂️ user_nameやtotal_costなど一眼で見て分かり易い名前をつけること

まとめ
何をしているのか分かり易い名前をこころがける
語彙力を鍛えると命名の幅も広がるので、身につけた方がいい

## 条件分岐

❌　条件分岐のネストが重なると可読性が低くバグの原因になり、テストにも時間がかかってしまう

対処法
冗長な条件がないか調べる
関数に分けて単一の役割をもたせることで、if文のネストを防ぐ

## データクラス

❌ 特定の場合を除き、データクラスとロジックが別々の場所で定義されている
	チーム開発をしていると気づかないうちに冗長コードが生まれ、バグの原因となることがある
	これを低凝集と呼ぶ

❌データクラスは、バリデーションを実装しないと不正値を渡せてしまう。
	ここでバリデーションロジックがまた、低凝集となって重複コードになってしまうことがあり、
	生産効率の低下につながってしまう。

まとめ
データクラス自体は悪いものではないが、使い方を間違えると、とんでもないバグを引き起こしかねない


## 再代入

❌　再代入を繰り返すと、思わぬところで値を変更してしまいバグの原因に繋がる

🙆‍♂️　特定の処理ごとに変数を作る(ただし、countなどの場合は別)


## メソッドの分割

❌　全ての動作をそのまま各手続き型プログラミング手法
	可読性が下がってしまう

🙆‍♂️　各役割ごとにメソッドを分けて実装する
	役割を分担すると、可読性も向上し、テストもやりやすくなる

🙆‍♂️　関わりの強い物をメソッドをまとめて、classに定義する
