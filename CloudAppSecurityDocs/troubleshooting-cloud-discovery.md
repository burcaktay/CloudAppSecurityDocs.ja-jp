---
title: Cloud Discovery エラーのトラブルシューティング - Cloud App Security | Microsoft Docs
description: この記事では、Cloud Discovery でよく起こるエラー一覧と、各エラーの推奨される解決策について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 76dfaebb-d477-4bdb-b3d7-04cc3fe6431d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 17890e4b54b4ed6447b274dc7e266011f8be236d
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176928"
---
# <a name="troubleshooting-cloud-discovery"></a>クラウド検出のトラブル シューティング

*適用対象:Microsoft Cloud App Security*

この記事では、Cloud Discovery のエラー一覧と、各エラーの推奨される解決策について説明します。

## <a name="log-parsing-errors"></a>ログ解析エラー

ガバナンス ログを使用して Cloud Discovery ログの処理を追跡できます。 この記事では、表示される可能性がある各エラーに対する解決方法について説明します。

### <a name="governance-log-errors"></a>ガバナンス ログ エラー

|Error|[説明]|解決方法|
|----|----|----|
|サポートされていないファイルの種類|アップロードしたファイルが有効なログ ファイルではありません (画像ファイルなど)。|ファイアウォールまたはプロキシから直接エクスポートされた **text**、**zip、または **gzip** ファイルをアップロードします。|
|ログ形式が予期される形式と一致しません|アップロードしたログの形式が、このデータ ソースで予期されるログの形式と一致しませんでした。|1.ログが破損していないことを確認します。 <br /> 2.ログと、アップロード ページに表示されるサンプル形式とを比較し、照合します。|
|Transactions are more than 90 days old (トランザクションは 90 日より前のものです)|すべてのトランザクションは 90 日よりも前のもので、無視されます。|最近のイベントが含まれる新しいログをエクスポートし、アップロードし直します。|
|No transactions to cataloged cloud apps (カタログ化されたクラウド アプリに対するトランザクションがありません)|認識されているクラウド アプリに対するトランザクションがログに見つかりません。|ログに送信トラフィック情報が含まれていることを確認します。|
|サポートされていないログの種類|**[データ ソース] = [その他 (サポートされていません)]** の場合、ログは解析されません。 代わりに、Cloud App Security テクニカル チームに送信され、レビューされます。|Cloud App Security テクニカル チームは、データ ソースごとに専用のパーサーを構築しています。 よく使用されているデータ ソースは、[既にサポートされています](set-up-cloud-discovery.md)。 サポートされないデータ ソースの各アップロードはレビューされ、新しいデータ ソース パーサーのパイプラインに追加されます。 新しいパーサーの通知は、Cloud App Security [リリース ノート](release-notes.md)の一部として公開されます。|

## <a name="log-collector-errors"></a>ログ コレクターのエラー

|問題 | 解決方法 |
|--------|--|
|FTP でログ コレクターに接続できません| 1.SSH の資格情報ではなく、FTP の資格情報を使用していることを確認します。 <br />2.使用している FTP クライアントが SFTP に設定されていないことを確認します。  |
|コレクター構成を更新できませんでした | 1.最新のアクセス トークンを入力したことを確認します。 <br />2.ファイアウォールで、ログ コレクターがポート 443 で送信トラフィックを開始することが許可されていることを確認します。|
|コレクターに送信されたログがポータルに表示されません | 1.ガバナンス ログに失敗した解析タスクがあるかどうかを確認します。  <br />  &nbsp;&nbsp;&nbsp;&nbsp;ある場合は、上記のログ解析エラー一覧を参照してエラーを解決してください。<br /> 2.ない場合は、ポータルでデータ ソースとログ コレクターの構成を確認します。 <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. [データ ソース] ページで、使用しているデータ ソースが正確に構成されていることを確認します。 <br />&nbsp;&nbsp;&nbsp;&nbsp;b. [ログ コレクター] ページで、データ ソースが正しいログ コレクターにリンクされていることを確認します。 <br /> 3.オンプレミス ログ コレクター コンピューターのローカル構成を確認します。  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. SSH でログ コレクターにログインし、collector_config ユーティリティを実行します。<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. 定義したプロトコル (Syslog/TCP、Syslog/UDP、または FTP) を使用してファイアウォールまたはプロキシがログをログ コレクターに送信していること、および正しいポートとディレクトリに送信していることを確認します。<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. コンピューターで netstat を実行し、ファイアウォールまたはプロキシからの接続を受信していることを確認します <br /> 4. ログ コレクターがポート 443 で送信トラフィックを開始することが許可されていることを確認します。 |
|ログ コレクターの状態:作成日 | ログ コレクターの展開が完了していませんでした。 展開ガイドに従って、オンプレミスの展開手順を完了します。|
|ログ コレクターの状態:Disconnected | リンクされているどのデータ ソースからも、過去 24 時間以内にデータを受信していません。 |


## <a name="discovery-dashboard-errors"></a>Discovery ダッシュボードのエラー

|問題|解決方法|
|----|----|
|Discovery データのアップロードと解析は成功しましたが、Cloud Discovery ダッシュボードの表示が空です|ダッシュボードは、ログに含まれていないデータでフィルターされているため、表示されるデータがない場合があります。 Cloud Discovery ダッシュボードのフィルターを変更して、別の種類のデータが結果に表示されるようにします。|

## <a name="next-steps"></a>次の手順
  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  

