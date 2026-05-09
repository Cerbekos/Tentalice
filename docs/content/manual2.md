# 日本語配列対応
##　1.概要
日本で使用するPCのOSの設定は日本語配列キーボードに対応していますが、これはキーボードから送信されるキーコードをOS側で日本語配列のコードと理解し対応する文字に変換しているため[^8]です。例えば、日本語配列の**"（ダブルコーテーション）**は**0x1F**ですが、英語配列の**0x1F**は**@（アットマーク）**です。
上記のキーマップ変更ツールは英語配列を前提に作成されていますので、ダブルコーテーションを入力したい場合、アットマークを設定する必要があります。
そこで**Tentlaice**では、英語配列のコードを日本語配列としてマクロ化しました。

```dts tentalice.keymap
        `jp_dquote: `jp_dquote {
            compatible = "zmk,behavior-macro";
            #binding-cells = <0>;
            label = "`jp_DQUOTE";
            bindings = <&kp AT>;
        };
```

これにより、キーマップ変更ツールの`Behavior`から日本語のコードとして選択可能にしています。
~ |             |             |
~ | :---:       | :---:       |
~ | [~g1]       | [~g2]       |
:::warp g1
![zmkkeymapeditor2](../images/zmkkeymapeditor2_20260419.jpg)

ZMK keymap editor
:::

:::warp g2
![zmkkeymapeditor3](../images/zmkkeymapeditor3_20260419.jpg)

ZMK keymap editor
:::

## 2.一覧
Tentaliceでマクロ化している日本語配列の一覧[^9]は以下の通りです。

| マクロ名 | バインディング | 出力 |
| --- | --- |
| `jp_dquote` | `&kp AT` | " |
| `jp_amp` | `&kp CARET` | & |
| `jp_quote` | `&kp AMPERSAND` | ' |
| `jp_equal` | `&kp UNDER` | = |
| `jp_caret` | `&kp EQUAL` | ^ |
| `jp_yen` | `&kp 0x89` | \\ |
| `jp_plus` | `&kp COLON` | + |
| `jp_tilde` | `&kp PLUS` | ~ |
| `jp_pipe` | `&kp LS(0x89)` | ｜ |
| `jp_at` | `&kp LEFT_BRACKET` | @ |
| `jp_colon` | `&kp SINGLE_QUOTE` | : |
| `jp_aster` | `&kp DOUBLE_QUOTES` | * |
| `jp_baqt` | `&kp LEFT_BRACE` | ` |
| `jp_under` | `&kp LS(0x87)` | _ |
| `jp_lbrkt` | `&kp RIGHT_BRACKET` | [ |
| `jp_rbrkt` | `&kp BACKSLASH` | ] |
| `jp_lpar` | `&kp ASTERISK` | ( |
| `jp_rpar` | `&kp LEFT_PARENTHESIS` | ) |
| `jp_lbrace` | `&kp RIGHT_BRACE` | { |
| `jp_rbrace` | `&kp PIPE` | } |
| `jp_kana` | `&kp LANGUAGE_1` | かな |
| `jp_eisu` | `&kp LANGUAGE_2` | 英数 |
| `jp_hanzen` | `&kp GRAVE` | 半角/全角|

[^8]:**日本語配列**などは、 [キー配列について（株式会社アーキサイト）](https://archisite.co.jp/pick-up/key-layout/) がイラスト付きで解説してありわかりやすいです。
[^9]:**日本語配列の一覧**作成は、 [【ZMK】OS設定を日本語キーボードのまま使う](https://note.com/kloir_z/n/n314e739f03a1) を参考にさせていただきました。