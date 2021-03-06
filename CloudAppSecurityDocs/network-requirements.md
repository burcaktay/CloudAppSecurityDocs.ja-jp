---
title: ネットワークの要件 - Cloud App Security | Microsoft Docs
description: この記事では、Cloud App Security で作業するために開く必要があるポートと IP アドレスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: df90f8a2b2a52f9dbaacac3e317b1354bdbe1d8a
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176605"
---
# <a name="network-requirements"></a>ネットワーク要件

*適用対象:Microsoft Cloud App Security*

この記事では、Microsoft Cloud App Security で作業するために許可し、ホワイトリストに追加する必要があるポートと IP アドレスの一覧を提供します。 

## <a name="view-your-data-center"></a>データ センターを表示する

以下の要件の一部は、接続しているデータ センターによって異なります。 

接続しているデータ センターを表示するには、次の手順を行います。

1. Cloud App Security ポータルで、メニュー バーの**疑問符のアイコン**をクリックします。 次に、**[バージョン情報]** を選択します。 

    ![[バージョン情報] をクリックします。](./media/about-menu.png)

2. Cloud App Security のバージョン画面で、リージョンとデータ センターを確認できます。

    ![データ センターを表示する](./media/data-center.png)

## <a name="portal-access"></a>ポータル アクセス

Cloud App Security ポータルにアクセスするには、次の IP アドレスと DNS 名について、ファイアウォールのホワイトリストに**発信ポート 443** を追加します。  

    portal.cloudappsecurity.com
    *.portal.cloudappsecurity.com
    cdn.cloudappsecurity.com
    https://adaproddiscovery.azureedge.net 
    *.s-microsoft.com
    *.msecnd.net
    dev.virtualearth.net
    *.cloudappsecurity.com
    flow.microsoft.com
    static2.sharepointonline.com
    dc.services.visualstudio.com
    *.blob.core.windows.net

さらに、使用するデータ センターに応じて、次の項目をホワイトリストに追加する必要があります。
> [!div class="mx-tableFixed"]
> 
> |データ センター|IP アドレス|DNS 名|
> |----|----|----|
> |US|13.80.125.22<br></br>52.183.75.62<br></br>13.91.91.243|\*.us.portal.cloudappsecurity.com|
> |US2|13.80.125.22<br></br>52.183.75.62<br></br>52.184.165.82|\*.us2.portal.cloudappsecurity.com<br></br>|
> |US3|13.80.125.22<br></br>52.183.75.62<br></br>40.90.218.198<br></br>40.90.218.196|*.us3.portal.cloudappsecurity.com<br></br>|
> |EU|13.80.125.22<br></br>52.183.75.62<br></br>52.174.56.180|\*.eu.portal.cloudappsecurity.com<|
> |EU2|13.80.125.22<br></br>52.183.75.62<br></br>40.81.156.154<br></br>40.81.156.156|*.eu2.portal.cloudappsecurity.com|


> 
> [!NOTE]
> ワイルドカード (\*) の代わりに、特定のテナント URL のみを開くことができます。たとえば、上記のスクリーンショットでは、mod244533.us.portal.cloudappsecurity.com を開くことができます。

## <a name="siem-agent-connection"></a>SIEM エージェントの接続

Cloud App Security が SIEM に接続できるようにするには、ファイアウォールのホワイトリストに対する次の IP アドレスに**発信ポート 443** を追加します。  


> [!div class="mx-tableFixed"]
> 
> |データ センター|IP アドレス|  
> |----|----|
> |US|13.91.91.243|
> |US2|52.184.165.82|
> |US3|40.90.218.198<br>40.90.218.196|
> |EU|52.174.56.180|
> |EU2|40.81.156.154<br>40.81.156.156|

> [!NOTE]
> Cloud App Security SIEM エージェントを設定するときにプロキシを指定していなかった場合は、ポート 80 でhttp 接続を http://ocsp.msocsp.com/ に許可する必要があります。 これは、Cloud App Security ポータルに接続するときに証明書失効ステータスを確認するために使用されます。

## <a name="app-connector"></a>アプリ コネクタ

一部のサードパーティ製のアプリに Cloud App Security からアクセスする場合、これらの IP アドレスが使用される可能性があります。 これらの IP アドレスによって、Cloud App Security によるログ収集や、Cloud App Security コンソールへのアクセスが可能になります。 

> [!NOTE]
>Cloud App Security は上記の IP アドレスからガバナンス アクションとスキャンを実行するため、ベンダーからのアクティビティ ログにこの IP アドレスが表示される場合があります。 

サードパーティ製のアプリに接続するには、Cloud App Security を有効にして次の IP アドレスから接続します。


> [!div class="mx-tableFixed"]
> 
> |データ センター|IP アドレス|  
> |----|----|
> |US|13.91.91.243 <br></br> 104.209.35.177 <br></br> 13.91.98.185 <br></br> 40.118.211.172 <br></br> 13.93.216.68 <br></br> 13.91.61.249 <br></br> 13.93.233.42 <br></br> 13.64.196.27 <br></br> 13.64.198.97 <br></br> 13.64.199.41 <br></br> 13.64.198.19|
> |US2|52.184.165.82<br></br> 40.84.4.93 <br></br> 40.84.4.119 <br></br> 40.84.2.83 |
> |US3|40.90.218.197<br>40.90.218.203|
> |EU|52.174.56.180<br></br>13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|
> |EU2|40.81.156.155<br>40.81.156.153|


## <a name="third-party-dlp-integration"></a>サード パーティ DLP との統合

Cloud App Security で stunnel 経由でデータを ICAP サーバーに送信できるようにするには、動的ソース ポート番号を使用して、これらの IP アドレスに DMZ ファイアウォールを開きます。 

1. **ソースのアドレス**: 上記で API コネクタのサードパーティ製アプリについて記載したように、これらのアドレスはホワイトリストに追加する必要があります
2. **ソース TCP ポート**: 動的
3. **宛先アドレス**: 外部 ICAP サーバーに接続されている stunnel の 1 つまたは 2 つの IP アドレス
4. **宛先 TCP ポート**: ご利用のネットワークに定義されているもの

> [!NOTE] 
> -  既定では、stunnel ポート番号は 11344 に設定されます。 これは必要に応じて別のポートに変更できますが、新しいポート番号を必ず書き留めてください。
> - Cloud App Security は上記の IP アドレスからガバナンス アクションとスキャンを実行するため、ベンダーからのアクティビティ ログにこの IP アドレスが表示される場合があります。 

サードパーティ製のアプリに接続し、外部 DLP ソリューションと統合するには、Cloud App Security を有効にして次の IP アドレスから接続します。

> [!div class="mx-tableFixed"]
> 
> |データ センター|IP アドレス|  
> |----|----|
> |US|13.91.91.243 <br></br> 104.209.35.177 <br></br> 13.91.98.185 <br></br> 40.118.211.172 <br></br> 13.93.216.68 <br></br> 13.91.61.249 <br></br> 13.93.233.42 <br></br> 13.64.196.27 <br></br> 13.64.198.97 <br></br> 13.64.199.41 <br></br> 13.64.198.19|
> |US2|52.184.165.82<br></br> 40.84.4.93 <br></br> 40.84.4.119 <br></br> 40.84.2.83 |
> |US3|40.90.218.197<br>40.90.218.203|
> |EU|52.174.56.180<br></br>13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|
> |EU2|40.81.156.155<br>40.81.156.153|

## <a name="mail-server"></a>メール サーバー

既定のテンプレートと設定から通知が送信されるようにするには、スパム対策のホワイトリストにこれらの IP アドレスを追加します。 Cloud App Security 専用の電子メールの IP アドレスは次のとおりです。 

- 65.55.234.192/26
- 207.46.200.0/27
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.50.192/26

メール送信者の ID をカスタマイズする場合、Microsoft Cloud App Security では、サード パーティ製の電子メール サービス MailChimp® を使用してカスタマイズすることができます。 この操作を行うには、Microsoft Cloud App Security ポータルの **[設定]** に移動します。 **[メールの設定]** を選択して、MailChimp のサービス使用条件とプライバシー ポリシーを確認します。 次に、あなたの代理として MailChimp を使用する権限を Microsoft に与えます。

送信者の ID をカスタマイズしない場合、電子メールの通知はすべての既定の設定を使用して送信されます。

MailChimp を使用するには、スパム対策のホワイトリストに次の IP アドレスを追加して、通知の送信を可能にします。198.2.134.139 (mail1.cloudappsecurity.com)


## <a name="log-collector"></a>ログ コレクター 

Cloud Discovery 機能がログ コレクターを使って組織内のシャドウ IT を検出できるようにするには、以下の項目を開きます。

- ログ コレクターが着信 FTP および Syslog トラフィックを受信できる。
- ログ コレクターがポート 443 でポータル (contoso.cloudappsecurity.com など) への発信トラフィックを開始できる。
- ログ コレクターがポート 443 で Azure Blob Storage への送信トラフィックを開始できる。


  | データ センター |                        URL                        |
  |-------------|---------------------------------------------------|
  |     US      |   https://adaprodconsole.blob.core.windows.net/   |
  |     US2     | https://prod03use2console1.blob.core.windows.net/ |
  |     US3     |https://prod5usw2console1.blob.core.windows.net/   |
  |     EU      | https://prod02euwconsole1.blob.core.windows.net/  |
  |     EU2     |https://prod4uksconsole1.blob.core.windows.net/    |

> [!NOTE]
> - ファイアウォールが静的 IP アドレスのアクセス リストを必要としていて、URL に基づくホワイト リストをサポートしていない場合は、ログ コレクターで [Microsoft Azure データセンターのポート 443 上の IP 範囲](https://www.microsoft.com/download/details.aspx?id=41653)への送信トラフィックを開始できるようにします。
>- ログ コレクターが Cloud App Security ポータルへの送信トラフィックを開始できるようにします。
>- ログ コレクターを設定するときにプロキシを指定していなかった場合は、ポート 80 でhttp 接続を http://ocsp.msocsp.com/ に許可する必要があります。 これは、Cloud App Security ポータルに接続するときに証明書失効ステータスを確認するために使用されます。

## <a name="next-steps"></a>次の手順
 
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  

