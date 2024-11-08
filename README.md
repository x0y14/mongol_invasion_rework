# Mongol Invasion Rework

## ヴァニラと同名のファイルについて
本来ow_プレフィックスを付けるべきだが, 挙動の確認ができていないのでそのままになってます.  
例えば２重起動してしまうなどが起こり得るので調査完了までそのままになります.

## ow_と付くコード, ファイルについて
ゲームのヴァニラコード, ファイルを上書きしています.

## mir_と付くコード, ファイルについて
modで追加したコード, ファイルです.

## mir_と付くコメントについて
| tag | mean |
| --- | --- |
| mir_add | modで新たに追加したコードの開始地点 |
| mir_rep | modで置換したコードの開始地点 |
| mir_end | mir_add, mir_repなどで編集した範囲の末端地点 |

使用例
```txt
on_setup = {
    story_owner = { # Start conquest of all of Mongolia
        start_wars_for_mongolia_effect = yes
        # mir_add
        if = {
            limit = { has_trait = greatest_of_khans }
            mir_add_the_great_khan_modifier = yes
        }
        # mir_end
    }
    set_variable = {
        name = succession_counter
        value = 0
    }
}
```
において以下がmodで新たに追加されたコード
```txt
# mir_add
if = {
    limit = { has_trait = greatest_of_khans }
    mir_add_the_great_khan_modifier = yes
}
# mir_end
```
ヴァニラでは以下のようなコードであったことになります
```txt
on_setup = {
    story_owner = { # Start conquest of all of Mongolia
        start_wars_for_mongolia_effect = yes
    }
    set_variable = {
        name = succession_counter
        value = 0
    }
}
```