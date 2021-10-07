---
layout: post
title: OSS Gateオンボーディング第一回を実施 - Debianコントリビューターを1人増やせた！ #oss_gate
categories: report on-boarding
---

*この記事は「[OSS Gateオンボーディング第一回を実施 - Debianコントリビューターを1人増やせた！](https://www.clear-code.com/blog/2021/10/8/on-boarding-2021-08.html)」がオリジナルです。
OSS Gateのサイトにあわせてマークアップを一部修正してあります。*

Debian開発者としてDebianのコミュニティーで活動している林です。

2021年8月から10月にかけて、[OSS Gateオンボーディング](https://oss-gate.github.io/on-boarding/)という取り組みを実施しました。
OSS Gateオンボーディングはより深く継続的にOSSを開発する人を増やすことが目的です。

この目的を実現するために、OSS Gateオンボーディングでは「開発者が増えて欲しい」先輩役と「開発に参加したい」新人さんをマッチングし、「開発に参加したい」人が「継続的に開発に参加する人」になれるように支援することにしました。

今回は、OSS Gateオンボーディングの第一回として[「debパッケージのメンテナンスやそれを支えるシステムの開発」](https://oss-gate.github.io/on-boarding/proposals/2021-08/kenhys-maintain-debian-packages/)という内容で参加者を募集し、実際に支援をした内容を紹介します。

* ToC
{:toc}

## 先輩役を務めることにした動機とは

Debianのローカルコミュニティーとして毎月1回 [東京エリア・関西合同Debian勉強会](https://tokyodebian-team.pages.debian.net/)が開催されています。
オンラインでの開催になったことで、地理的制約に縛られなくなり[^geo]、これまでよりも参加しやすくなりました。
ただ、(勉強会に限らず)もっと新しく参加してくれる人が増えて活性化するといいなと思っていました。

[^geo]: これまでオフラインだと参加できなかったけど、オンラインになったので鹿児島から参加してます、という人がいました。

そこで、Debianに興味を持ってはいるものの、まわりに教えてくれる人がいないなど困っている人を支援できないか、ということで先輩役をやってみる[^mentor]ことにしました。
結果として、Debianコミュニティーにより深く関わってもらえたらいいなという思いもありました。

[^mentor]: かつて、[Debian開発者のやまね](https://twitter.com/henrich)さんにいろいろ教えてもらって助かったという体験があったので、同じようなことができないかという気持ちでいました。やまねさんは[Software Design](https://gihyo.jp/magazine/SD)でDebian Hot Topicsを連載されています。

## 支援のはじまり 新人さんの募集

まずは、興味を持って参加してくれる新人さんがいないとどうしようもありません。

そこで、[募集要項](https://oss-gate.github.io/on-boarding/proposals/2021-08/kenhys-maintain-debian-packages/)を詰めた上で、7月17日のDebian勉強会でこれから実施しようとしている取り組みの紹介をしました。

<div class="rabbit-slide">
  <iframe src="https://slide.rabbit-shocker.org/authors/kenhys/tokyodebian-oss-gate-onboarding-20210717/viewer.html"
          width="640" height="404"
          frameborder="0"
          marginwidth="0"
          marginheight="0"
          scrolling="no"
          style="border: 1px solid #ccc; border-width: 1px 1px 0; margin-bottom: 5px"
          allowfullscreen> </iframe>
  <div style="margin-bottom: 5px">
    <a href="https://slide.rabbit-shocker.org/authors/kenhys/tokyodebian-oss-gate-onboarding-20210717/" title="OSS Gateオンボーディング - Debianプロジェクトを題材にした取り組みの紹介"></a>
  </div>
</div>

また、Debian/Ubuntu関連に興味を持っている人ならメーリングリストに登録しているだろうということで、メーリングリストにて募集の告知を行いました。

* [\[debian-users 00739\] Debianプロジェクトに継続的に関わりたい新人さんの募集のお知らせ](https://lists.debian.or.jp/pipermail/debian-users/2021-July/000738.html)
* [\[ubuntu-jp:6452\] Debian/Ubuntuプロジェクトに継続的に関わり始めたい人募集のお知らせ](https://lists.ubuntu.com/archives/ubuntu-jp/2021-July/006451.html)

ただ、どういうニーズがあるかはよくわからなかったので、いくつかパターンを用意して募集をかけてみました。
具体的には次の3つのコースを用意しました。

* Aコース: 新規Debianパッケージング作業
* Bコース: 既存のdebパッケージの不具合報告や修正作業
* Cコース: [mentors.debian.net](https://mentors.debian.net)の改善

Aコースはパッケージ化したいソフトウェアがあるけどどうしたらいいかよくわかっていない人を支援する目的で用意しました。
Bコースは、Aコースよりはやや知識や経験のある人向けです。
Cコースは、やや異色の内容になっています。mentors.debian.netというのは、Debianパッケージを一時的にアップロードしてスポンサーを探したりするのによく使われているサイトです。
パッケージングだけでなく、そういった作業を支えるシステムに興味を持つ人がいるかもしれないということで、テーマの1つとして取り上げてみました。フロントエンドにより興味がある人なら向いているのではと考えたためです。

## 募集締め切りと応募者の選考

告知してから約2週間後、7/31日に応募を締め切りました。
1件応募があればいいな、くらいのつもりでいました。

さいわいなことに5件の応募があり、そのなかから1件を採択しました。
使っているソフトウェアをパッケージングしたいという明確な動機が全面にでていたこと、
スケジュール感があいそうということで [@sivchari](https://github.com/sivchari) さんと一緒にAコースの新規Debianパッケージングの作業をすることにしました。

なお応募者のなかで圧倒的に希望が多かったのは、Aコースの新規Debianパッケージングでした。
また、知ったきっかけについてはdebian-usersではなくて、ubuntu-jpでの告知がほとんどでした。

締切直前の応募が多かったので、選考期間は少し長めにとっておくのがよさそうという知見[^application]を得ました。

[^application]: 7/31(土)に締め切り、8/2(月)に選考・連絡する予定にしていました。1件来たらそのまま採用、ぐらいの想定をしていました。

## 支援開始と初回のミーティング(8/11)

8/11に[初回のミーティング](https://oss-gate.github.io/on-boarding/proposals/2021-08/kenhys-maintain-debian-packages/meeting-2021-08-11.html)を実施しました。

@sivchari さんは普段はmacOSを使っていて、DebianはConoHaのVPSで使ったりしているとのことでした。
使い慣れた環境がよかろうということで、オンボーディングの支援期間中は、Debian unstableなインスタンスを用意してもらってそこで一緒に作業することにしました。

パッケージングの題材は希望のあった[slack-term](https://github.com/erroneousboat/slack-term)としました。
ただ、依存するライブラリーはその時点ではまだすべてパッケージ化されていませんでした。

依存パッケージも順にパッケージングしていきたいという意向だったので、その方針ですすめることにしました。
なお、支援期間内にパッケージング作業がすべては終わらなそうであることは見えて[^dh-make-golang-estimate]いたので、
目標はすべてパッケージングを終わらせることではなく、それ以降も継続して進められるようになっていればよいことを確認して作業に着手することにしました。

その後も、オンボーディングは週1回、2時間のペースで実施しました。

[^dh-make-golang-estimate]: Goのパッケージングの場合、dh-make-golang estimateというコマンドを実行するとパッケージングされていない依存ライブラリーがわかる。

## オンボーディング前半実施(8/17-8/24)

事前にConoHaのVPSでセットアップしてもらいたい内容を[共有](https://github.com/oss-gate/on-boarding/issues/17)しておいて、パッケージングの流れ[^blogs]を説明したりしました。
今回パッケージングしたい内容は、Go言語のプロダクトなので、Goのパッケージングのお作法をDebian Go teamの既存のドキュメントをもとに説明[^off-topics]しつつ進めました。

Goパッケージングではdh-make-golangコマンドを使うのですが、不具合があることがわかったので、フィードバックをしたりもしました。

* [dh-make-golang fails when upstream uses "../.." in import path](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=992610)

なお報告した不具合はdh-make-golang 0.5.0-1ですでに修正済みです。

オンボーディングの前半では、Debianプロジェクトの説明だったり、パッケージングのお作法を理解してもらうなど、どちらかというと実際に手を動かしてもらうよりは、解説する機会が多めでした。

[^blogs]: これまで公開していた[Debian関連の記事](https://oss-gate.github.io/on-boarding/proposals/2021-08/kenhys-maintain-debian-packages/references-2021-08.html#debian) が役に立つときが来ました。

[^off-topics]: ほかにもDebianプロジェクトの運営や、DPL選挙の話など、雑談でいろいろ話をしたりもしました。

## 途中でのふりかえり(8/31)

8月の終わりに途中までの[ふりかえりミーティングを実施](https://oss-gate.github.io/on-boarding/proposals/2021-08/kenhys-maintain-debian-packages/meeting-2021-08-31.html)しました。
オンボーディングの本来の目的である、「OSS Gateオンボーディング後も新人が対象OSSの開発に継続的に参加する」ことができる流れになっているかどうかを再確認するプロセスです。
方向性はぶれてなさそうだったのでそのまま進めていくことにしました。

この後しばらくして、オンボーディングのその後について、続報をメーリングリストに流しました。

* [\[debian-users 00741\] Re: Debianプロジェクトに継続的に関わりたい新人さんの募集のお知らせ](https://lists.debian.or.jp/pipermail/debian-users/2021-September/000740.html)
* [\[ubuntu-jp:6467\] Re: Debian/Ubuntuプロジェクトに継続的に関わり始めたい人募集のお知らせ](https://lists.ubuntu.com/archives/ubuntu-jp/2021-September/006466.html)

## オンボーディング後半実施(9/2-9/29)

オンボーディングの後半では、引き続き依存するライブラリーのパッケージング作業をすすめました。

* ITP(パッケージングはじめる意思の表明)が済んでいないものを終わらせる
* パッケージングするにあたりアップストリームで直してもらうべきものをフィードバックする
* 必要に応じてパッケージングに必要なパッチを作成する
* パッケージの体裁を整える
* パッケージのテストでコケてはまる

パッケージングをする上でありがちな問題などはひととおり体験してもらえたのではないかと思います。
パッケージの体裁が整ったのでスポンサーアップロードして、ftp-master待ちの状態までいくつかこぎつけることもできました。

依存しているライブラリーのうちの1つであるgolang-github-lithammer-fuzzysearchがDebian入りしたあと、新しいバージョンが出ました。
更新のやり方もあわせて体験してもらえたのは、その後も継続して開発するという観点から有意義でした。

## まとめミーティング実施(10/6)

最終回では、まとめミーティング(ふりかえり)を実施しました。

手探りの状態で実施したため、いくつか課題はありましたが、おおむね新人と先輩双方にメリット[^merit]のある支援期間にできたのではないかと考えています。

[^merit]: 先輩にとっても古くなっていた知識をアップデートすることができたり、Goパッケージングのツールの改善につながるフィードバックができたりしたため。

## OSS Gateオンボーディングでのやりとり

すでに述べたとおり、OSS Gateオンボーディングで目指したのはパッケージング作業が支援期間内に終わることではありません。
新人さんがすべてひとりでできるようになる必要はなく、作業を相談しながら継続してすすめられるようになればOKです。

とはいえ支援期間中にどれくらい進められたのかは今後の参考になるかもしれないので紹介すると、次のような具合でした。

* slack-term (もともとパッケージングしたい!と希望があったもの) [ITP #994283](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=994283)済み
  * golang-github-lithammer-fuzzysearch [ITP #992838](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=992838) Debian unstable入り
  * golang-github-0xax-notificator [ITP #993842](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=993842) ftp-masterの審査待ち
  * golang-github-erroneousboart-termui [ITP #994282](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=994282)済み。パッケージの体裁を整えている途中
  * golang-github-slack-go-slack [ITP #993615](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=993615)済み。パッケージの体裁を整えている途中
  
slack-termはITPまで、その他の依存ライブラリーは一部Debian unstableにすでに入った状態になりました。

![DDPOのスクリーンショット]({{ site.baseurl }}/images/posts/2021-10-08-on-boarding-2021-08-kenhys/20211006_qa.png)

毎回のオンボーディングでやることなどはissueを作成して記録を残していました。作業状況を確認して、その日にやろうとしていることを共有[^sharing-todo]するためです。

* [2021-08 debian slack-term オンボーディングのissue](https://github.com/oss-gate/on-boarding/issues?q=is%3Aissue+is%3Aclosed+project%3Aoss-gate%2Fon-boarding%2F1)

[^sharing-todo]: もちろん作業をすすめていくうちに、必ずしも予定通りにいかないことはあります。向き不向きはあるでしょうが、ゴールがわかりやすくなるのでそのようにしました。

解決すべきことなどはsalsa.debian.orgの各リポジトリごとのissueでやりとりしたり、マージリクエストをだしてもらったりしました。普段のOSSの開発のやりかたをそのまま実践しています。

* [slack-termに関するissue](https://salsa.debian.org/go-team/packages/slack-term/-/issues?scope=all&state=all)
* [golang-github-lithammer-fuzzysearchに関するissue](https://salsa.debian.org/go-team/packages/golang-github-lithammer-fuzzysearch/-/issues?scope=all&state=all)
* [golang-github-0xax-notificatorに関するissue](https://salsa.debian.org/go-team/packages/golang-github-0xax-notificator/-/issues?scope=all&state=all)
* [golang-github-erroneousboart-termuiに関するissue](https://salsa.debian.org/go-team/packages/golang-github-erroneousboat-termui/-/issues?scope=all&state=all)
* [golang-github-slack-go-slackに関するissue](https://salsa.debian.org/go-team/packages/golang-github-slack-go-slack/-/issues?scope=all&state=all)

また、毎回終わりにその日の日報を作成(一緒に作業していない日も記録)するようにしていました。
これは、オンボーディングのプロセスの改善につなげられるように、その材料となる情報を残しておく意味合いで実践しました。(ふりかえりはこの記録をもとに行いました。)

* [先輩の日報](https://oss-gate.github.io/on-boarding/proposals/2021-08/kenhys-maintain-debian-packages/daily-report-kenhys.html)
* [新人の日報](https://oss-gate.github.io/on-boarding/proposals/2021-08/kenhys-maintain-debian-packages/daily-report-sivchari.html)

時間が経過するとどんどん忘れていくので、作業記録はとても重要でした。

* [支援期間中に紹介した記事や設定のまとめ](https://oss-gate.github.io/on-boarding/proposals/2021-08/kenhys-maintain-debian-packages/references-2021-08.html)

支援期間中に紹介した記事や設定等もまとめておいたので、今後参考になる[^setting]かも知れません。

[^setting]: 端末の共有などは、今回はscreenで行いましたが、もっといいやりかたがあるかもしれないです。

## OSS Gateオンボーディングを終えて

第一回のOSS Gateオンボーディングを終えてみてよかったことは、先輩役を楽しんでできたことです。
今回はGoで書かれたソフトウェアのパッケージであり、Goのパッケージングはそれほどしたことがなかったので、これまで知らなかったことを知るよい機会となりました。
古くなっていた知識をアップデートすることもできました。

新人さんがつまるところを知れたので、今後のドキュメントの改善などで新しく入ってくる人のフォローをできたらいいなと考えています。

## OSS Gateオンボーディングはどんな人に向いている?

今回はDebianをテーマとしてオンボーディングを実施しました。
より一般的な話にすると、次のような人におすすめできるのではないかと思います。

* どこから手をつけてやるといいのかよくわからなくて不安な人(先輩が作業の交通整理をしてくれるはず)
* ドキュメントを読んだが挫折した人(先輩がそのあたりを解説してフォローしてくれるはず)
* プロジェクトの背景など雑多な話も聞きたい・楽しめる人(先輩が雑談としていろいろ話してくれるはず)

次回以降開催されるにしても、先輩役の人ごとに実施するテーマは変わるはずです。
ただ、突っ込んで話を聞いたり知見を深めたりしたい、好奇心旺盛な人が向いているのではないでしょうか。

一方の先輩役をする人はこんな人が向いていそうです。

* マイナーであってもいいから伝えたい知識を持っている(自分の持っている知識が新人さんの役に立って嬉しい)
* ほかにあまり先輩役になれるひとが界隈に少ない(できるひとがそもそもすくないので希少価値がある)
* 人にものを教えたりした機会が少ない(新人さんに教えることで、新たな知見が得られたり、古い知識をアップデートする機会になったりします)

## さいごに

今回はOSS Gateオンボーディングの第一回として、「debパッケージのメンテナンスやそれを支えるシステムの開発」という内容で参加者を募集し、実際に支援をした内容を紹介しました。

短期ではありましたが、今後継続していくうえで必要な知識や経験を伝授できたのではないかと考えています。

まだ手探りな部分も多いのですが、この取り組みをぜひ継続していきたいです。
第二回がいずれ開催されるはず(内容は先輩役次第)なので、その際には新人さんはぜひ応募してみてください。
