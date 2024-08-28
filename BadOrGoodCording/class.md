# クラス設計

## データクラスの改善

❌ 	値だけを持つクラスと、メソッド、バリデーションがバラバラになっていると、クラス単体で使うことができない
	チーム開発をしていると、複数箇所で実装されたり、値オブジェクトに不正値が容易に渡せてしまう

❌　変数の値を定数にしない

🙆‍♂️　クラスに必ず、インスタンス変数とメソッドを定義すること
	同じ場所にメソッドと値があることによって、他の場所で使ったりすることを防ぐことができる.

🙆‍♂️	メソッドの先頭に、バリデーションを実施して不正値を事前に防ぐ**ガード節**を実装する

🙆‍♂️	変数を定数にすることによって、宣言時かコンストラクタ生成時にしか代入できないので不正値を防ぐことができる
	変数を再度変更したい場合は、クラスのインスタンスを再度作成することで可能である。


	変数を使って処理をした後の結果を反映したインスタンスを返すメソッドにすれば、変更することが可能です。
	ローカル変数やメソッド引数で定数化すれば途中から途中で変更されないため、バグを防ぐことができる

🙆‍♂️　型を定義する
	プリミティブ型のままだと開発者のうっかりミスがあり、間違った値を入れてしまうことがある
	たとえばMoney型を自分で作ってその型じゃないとメソッドを扱えないようにすることで値渡しのバグを防ぐことができる

```java


import java.util.Currency;

class money{
	final int amount;
	final Currency currency;

	Money(final int amount, final Currency currency){
		if(amount < 0){
			throw new IllegalArgumentException(" 金額には、0以上を追加してください");
		}
		this.amount = amount;
		this.currency = currency;
	};

	Money add(final Money other){
		if(!currency.equels(other.currncy){
			throw new IllegalArgumentException("通過単位が違います");
		}
		final int added = amount + other.amount;
		return new Money(added, currency);
	}
}
```
