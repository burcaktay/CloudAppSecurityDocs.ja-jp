---
title: Dropbox を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に Dropbox アプリを接続する方法に関する情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4acd93f4-b885-4e1f-a385-43b5db02a3ee
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: afb9ac560478bda35d2556cd9382a99478aa91d2
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176503"
---
# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Dropbox を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存の Dropbox アカウントに接続する方法を説明します。 この接続により、Dropbox の使用状況を視覚化して制御できるようになります。 
 
 
Dropbox ではサインインしなくても共有リンクからファイルにアクセスできるため、Cloud App Security はこのようなユーザーを非認証ユーザーとして登録します。 Dropbox の非認証ユーザーが表示された場合、組織外のユーザーであることを示しているか、あるいは組織内のサインインしていないユーザーと認識されている可能性があります。

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Dropbox を Cloud App Security に接続する方法  
  
1.  Cloud App Security コンソールで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
2.  **[アプリ コネクタ]** ページで、[+] ボタン、**[Dropbox]** の順にクリックします。  
  
     ![Dropbox の接続](./media/connect-dropbox.png "Dropbox の接続")  
  
3.  ポップアップで、管理者アカウントの電子メール アドレスを入力します。  
  
4.  **[リンクを生成]** をクリックします。  
  
5.  **[リンクに移動]** をクリックします。  
  
     Dropbox のサインイン ページが開きます。 Cloud App Security がチームの Dropbox インスタンスにアクセスできるように、資格情報を入力します。  
  
6.  Cloud App Security がチームの情報やアクティビティ ログにアクセスし、チーム メンバーと同様にアクティビティを実行することを許可するかどうか確認するメッセージが Dropbox で表示されます。 続行するには、**[許可]** をクリックします。  
  
7.  Cloud App Security コンソールに戻ると、Dropbox が正常に接続されたことを通知するメッセージが届いています。  
  
8.  **[API のテスト]** をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功通知を受信したら、**[閉じる]** をクリックします。  
  
Dropbox を接続すると、接続までの 60 日間のイベントを受け取ります。

> [!NOTE] 
> ファイルを追加する Dropbox のすべてのイベントは、アップロード ファイルとして Cloud App Security に表示され、Cloud App Security に接続された他のすべてのアプリと並べられます。 
 
## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  