## Perl Nitro Booster

Once you understand this, probably okay. Probably... :)


# 0. Preamble by ytnobody

Hi guys. I\'m author of this original documentation.

Perl Nitro Booster I wrote in February 25, 2015. First commit in japanese.

Maybe you know, my english is so poor. If you can help my project, please patch my broken english.

Thank you.

---

# 1. Cliche

* First, You have to use `\n`(LF) as a new line character. *DO NOT USE `\r\n`(CR LF) IN YOUR CODE*
* And, You have to write `;`(semicolon) tail of syntax.
* Hey guys, let us write `use strict;` and `use warnings;` in a head of your code.
* For peace of your mind. If you want to use "multi bytes characters" like as japanese, You have to write `use utf8;` in your code.
* And write `binmode STDOUT, 'utf8';` when you want to output multi bytes characters.

---

# 2. Write a simple code

    use strict;
    use warnings;
    print "Hello, ". "world!\n";

Save this as `hello.pl`.

---

## Run your code

    perl hello.pl

---

## Description

* You can output some string with `print` function.
* A string is defined by `"`.
* `\n` is a new line character. It will be described in "metacharacters".
* Look your code! Can you see `;` after each syntax?
* `.` is an operator that concatenates two strings.

---

# 3. Variables

This is like followings.

    my $item = 'perl';
    print "Hello, $item world!\n";

---

## Description

A variable is like `$item`.
A variable in perl can contain a string, or numeric. Anyway welcome!

Like this, ** A variable that containable a single value ** is called as `Scalar Variable`.

In perl, define variable with `my` syntax.

And, And, a part of `$` is called `Sigil`. `$` is ** a sigil does expression that variable is a "Scalar Variable" **.

---

# 4. metacharacters

Roughly, a special character that does expression with backslash and alphabet.

* `\n` New Line
* `\t` Horizontal Tab
* `\r` Carriage Return. It appears when wrote a code in "Notepad" on Windows. Noisy.
* `\s` Space. It uses frequently in "Regular Expression" feature.
* `\d` Numeric. It uses frequently in "Regular Expression" feature too.

---

## metacharacters and quotation

Look at an example code. 
Replacing from double quotations to single quotations is to make confusion.

    print "Hello, $item world!\n";

↓

    print 'Hello, $item world!\n';

---

## Why?

Metacharacters is never resolved their representation in `''` syntax.

---

# 5. Calculation

Use perl as a calculator.

    use strict;
    use warnings;
    use utf8;
    
    binmode STDOUT, 'utf8';
    
    my $width = 14;
    my $height = 37;
    my $triangle = ( $width * $height ) / 2;
    
    printf "The area of a triangle△ with %dcm width and %dcm height is %0.02fcm2.\n", $width, $height, $triangle;

---

## Description

* `printf` requires 1 or more arguments. Specify the string-format in first argument. Special strings as like '%s', '%d' or '%0.02f' in format string is become replaced by 2nd or later arguments. Then, output a string to the terminal.
* `use utf8;` for manipulating multibyte character `△`.
* `binmode STDOUT, 'utf8';` for output multibyte character `△`. 

---

## Calculation Operators

Only operator to frequent.

* `*` multiplication
* `-` subtraction
* `+` addition
* `/` division
* `**` power
* `++` increment
* `--` decrement

Please read [here](http://perldoc.perl.org/perlop.html) for more information.

---

# 6. Conditional forking / Comparison operators

Syntax like 'If foo is 2, print "abc".'.

    my $item = 'perl';
    if ( $item eq 'perl' ) {
        print "Hello, amazing perl world!\n";
    }
    elsif ( $item eq 'java' ) {
        print "Hello, bourjois java world!\n";
    }
    else {
        print "Hello, $item world!\n";
    }

---

## Numeric Comparison Operator

Only operator to frequent.

* `==` Return `true` when lefthand side and righthand side is equal numerically.
* `!=` Return `true` when lefthand side and righthand side is *not* equal numerically.

* `>`  Return `true` when lefthand side is greater than righthand side numerically.
* `>=` Return `true` when lefthand side is equal or greater than righthand side numerically.
* `<`  Return `true` when lefthand side is lesser than righthand side numerically.
* `<=` Return `true` when lefthand side is equal or lesser than righthand side numerically.

---

## String Comparison Operator

Only operator to frequent.

* `eq` Return `true` when lefthand side and righthand side is equal as string.
* `ne` Return `true` when lefthand side and righthand side is *not* equal as string.

---

## Logical Operator

Only operator to frequent.

* `&&` AND operation
* `||` OR operation
* `!`  NOT operation

---

# 7. Array and Loop

    my @favlist = ('Gyoza', 'Curry', 'Ramen');
    
    for my $fav ( @favlist ) {
        print "MMmmmmmm, yummy! $fav is my favorite food!!!\n";
    }

Array is a one of variable type that begin with `@`. It contains multiple variable, and their order is guaranteed. 

And, `@` is a `sigil` that express array.

---

## 要素を一個だけ取り出したいとき

    use utf8;
    binmode STDOUT, 'utf8';
    
    my @favlist = ('餃子', 'インドカレー', '生春巻き');
    print $favlist[1]; # 'インドカレー' が出力される
    
`$配列名[要素番号]` で取り出せます。要素番号は0が最初！

---

## forループ

    for my $item ( @items ) {
        # ここに処理コードを書く
    }

配列の中身が一つ一つ、`$item`に代入され、ループ内で処理するのに使えるようになる。
配列の中身全体に何か処理をかける時に使ったりする。

---

## whileループ

    while ( $condition ) {
        # ここに処理コードを書く
    }

`$condition`には、何らかの判定結果を入れる。
すると、`$condition`が`0`か`undef`にならない限りは``無限``にループする。

---

# 8. 正規表現

* `ほげふが`って文字列に`ふが`が入ってるかどうか調べたい
* `ほげふが`から`ふが`を抜き出したい

みたいなときに使えます。

---

## 文字列検索/置換する場合

    use utf8;
    binmode STDOUT, 'utf8';
    
    my $str = 'ほげふが';
    if ( $str =~ /ふが/ ) {
        print "「ふが」ありました！\n"
        $str =~ s/ふが/ぴよ/;
    }
    print $str. "\n";

---

## 文字列を抜き出す場合

    my $str = 'hello, world';
    my ($word) = $str =~ /(.+), world/;
    print $word. "\n";

---

## かなりよく使うマッチング表現

* `\A` 文字列の始まりを表します。
* `\z` 文字列の終わりを表します。
* `+` 直前の文字の1回以上の繰り返しを表します。
* `*` 直前の文字の0回以上の繰り返しを表します。
* `(.+)` １文字でもマッチすれば、それを抜き出す。
* `[0-9]` 半角数字１文字にマッチ

正規表現は奥が深いので、[こちら](http://perldoc.jp/docs/perl/5.14.1/perlre.pod)を見ておくと良いでしょう。

---

## 正規表現のよくある罠

正規表現には`\d`という物があります。これは通常`0から9までの数値文字１文字`を表現する`文字クラス`です。

    use strict;
    use warnings;
    my $num = '３００'; ### 注意! 全角数字!
    
    ### コレはマッチしない
    if ( $num =~ /\A\d*\z/ ) {
        print "$num is number!\n"; 
    }

しかし、`\d`は`use utf8`されている状況下では、**半角数字だけではなく全角数字にもマッチする**ので、注意が必要です。

    use strict;
    use warnings;
    use utf8; ### コイツを使ってると、\dは全角数字にもマッチするよ！
    my $num = '３００'; ### 注意! 全角数字!
    
    ### コレはマッチする
    if ( $num =~ /\A\d*\z/ ) {
        print "$num is number!\n"; 
    }

もしどうしても半角数字だけにマッチさせたければ、`[0-9]`を利用しましょう。


---

# 9. ハッシュ（連想配列）

Key-value型のデータ構造。%なんとか みたいな書き方をします。
ハッシュの中の単体要素を取り出すときは `$ハッシュ名{要素名}` のように指定します。

    my %human = (
        name => 'ytnobody',
        age => 34,
        sex => male,
    );
    print "$human{name} is $human{sex}, and $human{age} years old.\n";

---

# 10. ファイルとディレクトリ

ファイルを開くときには `open` を使う。なお、モードを指定する必要が有ります。

    my $mode = '<';
    my $file = '/path/to/file.txt';
    open my $fh, $mode, $file; 

`$fh`のことを`ファイルハンドル`と呼ぶ。

--- 

## 実際の利用例

ファイルハンドルを`<`と`>`で囲ってやると、一行ずつファイルの中身を配列として持ってきてくれる。

    open my $fh, '<', '/path/to/somefile';
    for my $line (<$fh>) {
        print $line;
    }
    close $fh;

---

## ファイルオープン時のモード

* `<` : 読み込み専用
* `>` : 書き込み専用（上書きモード）
* `>>` : 書き込み専用（追記モード）

---

## ターミナルからの入力を受け取りたい

`STDIN`というファイルハンドルが最初から存在するので、それを使う

    ## Ctrl+D が押下されるまで、入力された文字列をオウム返しする。
    while (my $input = <STDIN>) {
        print $input;
    }
    
`STDIN`は`標準入力`と呼ばれる。

---

## ディレクトリの中身調べたりする

`glob` を使うと、unixの`ls`コマンドのような指定方法でファイル/ディレクトリ一覧を得ることができます。

    my @logs = glob '/path/to/some/*.log';

---

# 11. サブルーチン

`サブルーチン`とは、一連の処理をまとめたプログラムです。またの名を`関数`。`sub`命令で定義できます。

    sub make_ramen {
        print "フタ開ける\n";
        
        print "湯〜注ぐ\n";
        
        ### ここで３分間まつ
        sleep 60 * 3;           
        
        print "出来上がり\n";
    }

---

## サブルーチンを実行する

サブルーチン名の後ろに丸括弧をつけてやると、サブルーチンの中身を実行します。

    make_ramen();
    
これを`サブルーチンのコール`とか`関数呼び出し`などと呼びます。

---

## サブルーチンに引数を与えて挙動を変える

例えばこんなサブルーチンがあるとします。

    sub eat {
        my ($dish, $tableware) = @_;
        print "I eat a $dish using $tableware.\n";
    }

実際にコールするときには、以下のようにします。

    eat('sushi', 'chopsticks');
    # とか
    eat('steak', 'knife and fork');

この時、`'sushi'`や`'shopsticks'`のことを`引数`と呼び、サブルーチンのコール時に引数を指定することを`引数を渡す`と表現します。

eatサブルーチンを定義する時に利用された`@_`は、**引数が格納された特殊な配列**です。**とにかく`@_`は覚えましょう。**`@_`です。

# 12. リファレンス

`リファレンス`とは、主に`変数`,`配列`,`ハッシュ`,`ファイルハンドル`,`サブルーチン`についての参照を表現する変数です。

    ## ハッシュを定義する。
    my %human = (name => 'ytnobody', age => 34);
    
    ## ハッシュリファレンスを定義する。
    my $ref = \%human;
    
    ## ハッシュリファレンスの年齢を書き換える。
    $ref->{age} = 35;
    
    ## 元のハッシュに格納されている名前と年齢を表示する。
    printf "%s is %s years old.\n", $human{name}, $human{age};

上記のとき、結果は `ytnobody is 35 years old.` と表示されます。

**ハッシュリファレンスの内容を書き換える**箇所で、**実体であるハッシュの内容が書き換えられる**わけです。

尚、リファレンスの概念は、Perlのオブジェクト指向を習得する上で必須の知識ですので、しっかり体得しましょう。

---

## リファレンスの定義方法とデリファレンス

前述の様に、実体となり得る変数や配列などの前に `\`をつけることで、リファレンスを定義することができます。

一方で、実体を定義せずに直接リファレンスを定義することも可能です。よく使うのは`配列リファレンス`と`ハッシュリファレンス`の２種類です。

なお、各リファレンスから実体をたぐり寄せる時には`デリファレンス`と呼ばれる操作を行います。

デリファレンスは、デリファレンス先の型式に合わせて、リファレンス変数の前に対応するシジルをくっつけるだけです。

    ## 配列リファレンス
    my $array_ref = [1, 1, 2, 3, 5, 8, 13, 21]; 
    
    ## 6th item is 13. と表示。
    printf "6th item is %s.\n", $array_ref->[6];
    
    ## 配列にデリファレンスする
    my @array = @$array_ref;
    
    
    ## ハッシュリファレンス
    my $hash_ref = {name => 'ytnobody', age => 34};
    
    ## My name is ytnobody. と表示。
    printf "My name is %s.\n", $hash_ref->{name};
    
    ## ハッシュにデリファレンスする
    my %hash = %$hash_ref;
