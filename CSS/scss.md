#Sassを使うには
まずコマンドラインで`gem install sass`とする必要がある。
単に`<link rel="stylesheet" href="stylesheet.scss">`として読み込んでもファイルが読み込まれることはない。

これはブラウザはCSSしか読み込むことが出来ないからである。
##SassをCSSに変換する方法
変換を行うためにはターミナルでの作業が必要になってくる。
`$ sass stylesheet.scss stylesheet.css`
ファイルの名前は任意である。
このやり方だとファイルを変更するたびに変換の作業が必要になってくるので**https://prepros.io/**などのツールを活用していくのがいい
