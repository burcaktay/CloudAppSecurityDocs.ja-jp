---
title: Azure での Docker を使用した自動ログ アップロードを構成する
description: この記事では、Azure での Ubuntu または RHEL 上で Docker を使用して、Cloud App Security の継続的レポート用にログの自動アップロードを構成するプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/27/2019
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9c51b888-54c0-4132-9c00-a929e42e7792
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9d3d0aad417050011a5a5780e5563ac3d040eb37
ms.sourcegitcommit: c24732bc40350c3cf416640b7d15f3c6f7be371d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55086449"
---
# <a name="set-up-and-configuration-on-ubuntu-or-rhel-in-azure"></a>Azure での Ubuntu または RHEL 上での設定および構成

*適用対象: Microsoft Cloud App Security*

Azure での Ubuntu または Red Hat Enterprise Linux (RHEL) 上で Docker を使用して、Cloud App Security の継続的レポート用にログの自動アップロードを構成することができます。 この記事では、自動ログ アップロードを設定する方法について説明します。 

## <a name="technical-requirements"></a>技術要件

- OS:Ubuntu 14.04 および 16.04 (新しいバージョンについては、サポートにお問い合わせください)、または RHEL 7.2 以降

- ディスク領域:250 GB

- CPU:2 で保護されたプロセスとして起動されました

- RAM:4 GB

- [ネットワーク要件](network-requirements.md#log-collector)で説明されているとおりにファイアウォールを設定する

## <a name="log-collector-performance"></a>ログ コレクターのパフォーマンス

ログ コレクターは、1 時間あたり最大 50 GB の容量のログを処理できます。 ログ収集プロセスの主なボトルネックは次のとおりです。

- ネットワーク帯域幅 - ネットワーク帯域幅によって、ログのアップロード速度が決まります。

- 仮想マシンの I/O パフォーマンス - ログ コレクターのディスクにログが書き込まれる速度が決まります。 ログ コレクターには、ログの収集速度を監視して、アップロード速度と比較する安全メカニズムが組み込まれています。 輻輳の場合、ログ コレクターは、ログ ファイルの削除を開始します。 1 時間あたり 50 GB を超えるのが普通である場合は、複数のログ コレクターにトラフィックを分割することをお勧めします。

## <a name="set-up-and-configuration"></a>セットアップと構成  

### <a name="step-1--web-portal-configuration-define-data-sources-and-link-them-to-a-log-collector"></a>ステップ 1: Web ポータルの構成: データ ソースを定義し、それをログ コレクターにリンクする

1. **[自動ログ アップロード]** 設定ページに移動します。 

     」を参照します。 Cloud App Security ポータルで、設定アイコンをクリックした後、**[ログ コレクター]** をクリックします。

      ![設定アイコン](./media/settings-icon.png)

2. ログをアップロードするファイアウォールまたはプロキシそれぞれに対応するデータ ソースを作成します。

     」を参照します。 **[データ ソースの追加]** をクリックします。

      ![データ ソースを追加する](./media/add-data-source.png)
          
     b. プロキシまたはファイアウォールの **[名前]** を付けます。
      
      ![ubuntu1](./media/ubuntu1.png)

     c. **[ソース]** リストからアプライアンスを選択します。 一覧に表示されていないネットワーク アプライアンスを使用するために **[カスタム ログ形式]** を選ぶ場合、構成方法の詳細については[カスタム ログ パーサーの使用](custom-log-parser.md)に関するページをご覧ください。

     d. 予想されるログ形式のサンプルとログを比較します。 ログ ファイルの形式がこのサンプルと一致しない場合は、データ ソースを **[その他]** として追加する必要があります。

     e. **[レシーバーの種類]** を、**[FTP]**、**[FTPS]**、**[Syslog – UDP]**、**[Syslog – TCP]**、または **[Syslog – TLS]** に設定します。
     
     >[!NOTE]
     >多くの場合、セキュリティで保護された転送プロトコル (FTPS、Syslog – TLS) と統合するには、ファイアウォール/プロキシの追加設定が必要です。

     f. ネットワークのトラフィックを検出するために使用できるログの取得先であるファイアウォールおよびプロキシそれぞれに対して、この手順を繰り返します。 ネットワーク デバイスごとに専用のデータ ソースを設定することをお勧めします。これにより、次のことができるようになります。
     - 調査目的で、各デバイスの状態を個別に監視する。
     - 各デバイスが異なるユーザー セグメントで使用されている場合、デバイスごとに Shadow IT Discovery を調べる。

     
3. 画面上部の **[ログ コレクター]** タブに移動します。

     」を参照します。 **[ログ コレクターを追加]** をクリックします。

     b. ログ コレクターに **[名前]** を付けます。

     c. Docker の展開に使用するコンピューターの **[ホスト IP アドレス]** を入力します。 ホスト名を解決する DNS サーバー (または同等の機能) がある場合、ホスト IP アドレスをコンピューター名で置換できます。

     d. コレクターに接続するすべての**データ ソース**を選び、**[更新]** をクリックして構成を保存します。次の展開手順を参照してください。

      ![ubuntu2](./media/ubuntu2.png)

     > [!NOTE]
     > - 1 つのログ コレクターで複数のデータ ソースを処理できます。
     > - Cloud App Security と通信するようにログ コレクターを構成するときに情報が必要になるため、画面の内容をコピーします。 Syslog を選択した場合、この情報には、Syslog リスナーがリッスンするポートに関する情報が含まれます。

4. 展開の詳細が表示されます。 ダイアログから実行コマンドを**コピー**します。 [クリップボードにコピー] アイコンを使用できます。 ![クリップボードにコピー アイコン](./media/copy-icon.png)

5. 予想されるデータ ソース構成を**エクスポート**します。 この構成では、アプライアンスでログのエクスポートを設定する方法を記述します。

     ![ログ コレクターを作成する](./media/windows7.png)

### <a name="step-2--deployment-of-your-machine-in-azure"></a>ステップ 2 – Azure でのマシンの展開

> [!NOTE]
> 次の手順は、Ubuntu での展開について説明したものです。 他のプラットフォームの展開手順は若干異なります。


1. Azure 環境内で新しい Ubuntu マシンを作成します。 
2. マシンが起動したら、次の手順でポートを開きます。

     」を参照します。 マシン ビューで、**[ネットワーク]** に移動して、関連するインターフェイスをダブルクリックして選択します。

     b. **[ネットワーク セキュリティ グループ]** に移動して、関連するネットワーク セキュリティ グループを選択します。

     c. **[受信セキュリティ規則]** に移動して **[追加]** をクリックします。
      
      ![Ubuntu Azure](./media/ubuntu-azure.png)
    
     d. 次の規則を追加します (**詳細設定**モード)。

      |名前|宛先ポートの範囲|プロトコル|ソース|Destination|
      |----|----|----|----|----|
      |caslogcollector_ftp|21|TCP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
      |caslogcollector_ftp_passive|20000-20099|TCP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
      |caslogcollector_syslogs_tcp|601-700|TCP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
      |caslogcollector_syslogs_udp|514-600|UDP|<ご使用のアプライアンスの IP アドレスのサブネット>|Any|
      
      ![Ubuntu Azure の規則](./media/inbound-rule.png)

3. マシンに戻って、**[接続]** をクリックし、マシン上のターミナルを開きます。

4. `sudo -i` を使ってルート権限に変更します。

5. [ソフトウェア ライセンス条項](https://go.microsoft.com/fwlink/?linkid=862492)に同意したら、古いバージョンをアンインストールし、次のコマンドを実行して Docker CE をインストールします。
        
       curl -o /tmp/MCASInstallDocker.sh https://adaprodconsole.blob.core.windows.net/public-files/MCASInstallDocker.sh && chmod +x /tmp/MCASInstallDocker.sh; /tmp/MCASInstallDocker.sh

     ![Ubuntu Azure のコマンド](./media/ubuntu-azure-command.png)

6. Cloud App Security ポータルの **[Create new log collector] \(新しいログ コレクターの作成\)** ウィンドウで、ホスト マシンでコレクター構成をインポートするコマンドをコピーします。

      ![Ubuntu Azure](./media/windows7.png)

7. ログ コレクターを展開するコマンドを実行します。
     
        (echo db3a7c73eb7e91a0db53566c50bab7ed3a755607d90bb348c875825a7d1b2fce) | docker run --name MyLogCollector -p 21:21 -p 20000-20099:20000-20099 -e "PUBLICIP='192.168.1.1'" -e "PROXY=192.168.10.1:8080" -e "CONSOLE=mod244533.us.portal.cloudappsecurity.com" -e "COLLECTOR=MyLogCollector" --security-opt apparmor:unconfined --cap-add=SYS_ADMIN --restart unless-stopped -a stdin -i microsoft/caslogcollector starter

     ![Ubuntu プロキシ](./media/ubuntu-proxy.png)

8. コマンド `Docker logs <collector_name>` を実行して、ログ コレクターが正しく動作していることを確認します。 次のような結果を受け取ります:**"Finished successfully!" (正常に終了しました)**

   ![ubuntu8](./media/ubuntu8.png)

### <a name="step-3---on-premises-configuration-of-your-network-appliances"></a>ステップ 3 - ネットワーク機器のオンプレミス構成

ネットワーク ファイアウォールとプロキシを、ダイアログの指示に従って FTP ディレクトリの専用 Syslog ポートにログが定期的にエクスポートされるように構成します。 たとえば、次のように入力します。

    BlueCoat_HQ - Destination path: \<<machine_name>>\BlueCoat_HQ\

### <a name="step-4---verify-the-successful-deployment-in-the-cloud-app-security-portal"></a>ステップ 4 - Cloud App Security ポータルで正常に展開されたことを確認する

**[ログ コレクター]** の表でコレクターの状態をチェックし、状態が **[接続済み]** であることを確認します。 **[作成済み]** の場合は、ログ コレクターの接続と解析が完了していない可能性があります。

 ![ubuntu9](./media/ubuntu9.png)

**ガバナンス ログ**に移動して、ログがポータルに定期的にアップロードされていることを確認することもできます。

展開中に問題が発生した場合は、「[Troubleshooting Cloud Discovery](troubleshooting-cloud-discovery.md)」(Cloud Discovery のトラブルシューティング) を参照してください。

### <a name="optional---create-custom-continuous-reports"></a>省略可能 - カスタムの継続的レポートを作成する

ログが Cloud App Security にアップロードされていること、およびレポートが生成されることを確認します。 検証の後、カスタム レポートを作成します。 Azure Active Directory ユーザー グループに基づいて、カスタム検出レポートを作成できます。 たとえば、マーケティング部門のクラウドの使用状況を確認する場合、ユーザー グループのインポート機能を使用してマーケティング グループをインポートします。 次に、このグループに対するカスタム レポートを作成します。 また、IP アドレス タグや IP アドレスの範囲に基づいてレポートをカスタマイズすることもできます。

1. Cloud App Security ポータルの設定歯車アイコンで、Cloud Discovery の設定を選択して、**[継続的レポート]** を選択します。 
2. **[レポートの作成]** ボタンをクリックし、フィールドに入力します。
3. **[フィルター]** では、データ ソース、[インポートされたユーザー グループ](user-groups.md)、または [IP アドレスのタグと範囲](ip-tags.md)を指定してフィルターすることができます。 

     ![カスタムの継続的レポート](./media/custom-continuous-report.png)

## <a name="next-steps"></a>次の手順
[Cloud Discovery の Docker の展開に関するトラブルシューティング](troubleshoot-docker.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます](https://premier.microsoft.com/)

