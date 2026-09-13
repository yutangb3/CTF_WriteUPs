## category
General skills
## probrem
The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee?

Download the Rust code here
.
## 難しさ
簡単
## 解法
rustファイルを見て修正箇所を見つけていく。
```
fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &String){ // How do we pass values to a function that we want to change?

    // Key for decryption
    let key = String::from("CSUCKS");

    // Editing our borrowed value
    borrowed_string.push_str("PARTY FOUL! Here is your flag: ");

```
borrowed_stringが読み取りなので&mutで書き換え可能にする。
```
let party_foul = String::from("Using memory unsafe languages is a: "); // Is this variable changeable?
    decrypt(encrypted_buffer, &party_foul); // Is this the correct way to pass a value to a function so that it can be changed?
}
```
ここも同様に直すと
```

    let mut party_foul = String::from("Using memory unsafe languages is a: "); // Is this variable changeable?
    decrypt(encrypted_buffer, &mut party_foul); // Is this the correct way to pass a value to a function so that it can be changed?
}
```
するとフラグが出現
## 使用コマンド
## 答え
```picoCTF{4r3_y0u_h4v1n5_fun_y31?}```
## ここから学んだこと
mutはmutableで可変からきている。
その代わり一個しか使えない。
&mutは可変参照。
## つぎに考えること
rustの基本的な考えを身に着ける。
