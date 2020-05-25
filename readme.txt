この素材は、Scripts.rvdata2をRubyテキストファイルに変換するものです。
Scripts.rvdata2が.rbファイルに展開されることで、AtomやEclipse等の外部エディタで
RGSS3スクリプトの編集ができるようになります。

要するにツクールMVのようなスクリプト編集形態がとれるようになります。


<使用方法>
[Scripts.rvdata2をRubyテキストファイルに変換する]
①RGSSConvertorのプロジェクトファイル内に変換したいScripts.rvdata2を格納します。
②RGSSConvertorをGame.exeから起動し、「to-text」を選択します。
③変換結果としてプロジェクト内にscriptsディレクトリが作成されます。


[Rubyテキストファイルを編集する]
RGSSConvertorプロジェクト内に作成されたscripts内のsrcディレクトリにRubyファイルは格納されています。

＊Rubyファイルを追加/削除する
①scripts/src内でRubyファイルを追加/削除します。
②scripts内のscriptslist.txtを開き、対象のRubyファイル名を追加/削除します。
scriptslist.txtは、Scripts.rvdata2内でのスクリプトの順番を保持するために使用されています。
なお、scriptslist.txtの中で▼から始まるスクリプト名、半角スペースのみのスクリプト名、名前なしのスクリプト名は
変換の際には無視され、Rubyファイルとしてsrc下に作成されません。


[RubyテキストファイルをScripts.rvdata2に変換する]
①RGSSConvertorのプロジェクトファイル内にscriptsディレクトリを格納します。
②RGSSConvertorをGame.exeから起動し、「to-bin」を選択します。
③変換結果としてプロジェクト内にScripts.rvdata2が作成されます。


[Rubyテキストファイルをゲームから直接読み込む]
出力されたRubyファイルをいちいちScripts.rvdata2に変換するのは面倒なので、
RGSSConvertorプロジェクトの素材にあるscripts.txtをRGSS3スクリプトとしてコピペすると、
Rubyファイルをゲームから直接読み込むことができるようになり便利です。


<おまけ>
素材にあるファイルのrgss_convertor.rbはそのままRubyのライブラリとして使用することができます。
その場合、VXAceだけでなくVXとXPでもスクリプト変換を行うことができます。

[使用例(VXでの変換を行う場合)]
require_relative "rgss_convertor"

#引数１でScriptsファイルのあるディレクトリを指定
#引数２でscriptsディレクトリのあるディレクトリを指定
#引数３でScriptsの拡張子を指定
cvtr = RGSS_Convertor("Data", ".", "rvdata")

#ScriptsファイルをRubyファイルに変換する場合
cvtr.to_text

#scriptsディレクトリ内のRubyファイルからScriptsファイルを作成場合
cvtr.to_bin
