---
title: Cloud App Security を Zscaler と統合する
description: この記事では、シームレスな Cloud Discovery と承認されていないアプリの自動ブロックのために Microsoft Cloud App Security と Zscaler を統合する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8abeab8e-3b7a-46a7-bbec-9aaf26f778a8
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d26ba74ff95df4fc2def9cfff0acd41dcef358a4
ms.sourcegitcommit: c24732bc40350c3cf416640b7d15f3c6f7be371d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55086398"
---
# <a name="integrate-cloud-app-security-with-zscaler"></a>Cloud App Security を Zscaler と統合する

*適用対象:Microsoft Cloud App Security*

Cloud App Security と Zscaler の両方を使用する場合、2 つの製品を統合することでセキュリティの Cloud Discovery エクスペリエンスを強化することができます。 Zscaler は、スタンドアロン クラウド プロキシとして、組織のトラフィックを監視します。これによりトランザクションをブロックするためのポリシーの設定が可能になります。 Cloud App Security と Zscaler を同時に使用することで、次の機能が提供されます。

- Cloud Discovery のシームレスな展開 - Zscaler を使用してトラフィックをプロキシし Cloud App Security に送信することで、ネットワーク エンドポイントにログ コレクターをインストールして Cloud Discovery を有効にする必要がなくなります。
- Zscaler のブロック機能は、Cloud App Security で "承認されていない" として設定したアプリに自動的に適用されます。
- Cloud App Security のリスク評価を使用して Zscaler のポータルが強化されます。200 の主要なクラウド アプリに対するリスク評価を、Zscaler のポータルで直接表示できます。

## <a name="prerequisites"></a>前提条件

- Microsoft Cloud App Security の有効なライセンス
- Zscaler Cloud 5.6 の有効なライセンス
- Zscaler NSS のアクティブなサブスクリプション 

## <a name="deployment"></a>展開

1. Zscaler のポータルで、[Zscaler パートナーの Microsoft Cloud App Security との統合](https://help.zscaler.com/zia/configuring-mcas-integration)を完了するための手順を実行します。
2. Cloud App Security ポータルで、次の統合の手順を行います。
    1. 設定の歯車アイコンをクリックして、**[Cloud Discovery 設定]** を選択します。 
    2. **[ログの自動アップロード]** タブをクリックした後、**[データ ソースの追加]** をクリックします。
    3. **[データ ソースの追加]** ページで、次の設定を入力します。

       - 名前 = NSS
       - ソース = Zscaler QRadar LEEF
       - レシーバーの種類 = Syslog - UDP

         ![データ ソースの Zscaler](./media/data-source-zscaler.png)

    4. **[期待されるログ ファイルのサンプルを表示]** をクリックします。 次に **[サンプル ログのダウンロード]** をクリックして、サンプルの検出ログを表示し、自身のログと一致していることを確認します。<br>

3. ネットワーク上で検出されたクラウド アプリを調査します。 詳しい情報と調査手順については、「[Working with Cloud Discovery](working-with-cloud-discovery-data.md)」(Cloud Discovery での作業) をご覧ください。

4. Cloud App Security で "承認されていない" として設定したすべてのアプリは、2 時間ごとに Zscaler によって ping され、Zscaler によって自動的にブロックされます。 承認されていないアプリについて詳しくは、「[アプリの承認/非承認](governance-discovery.md#BKMK_SanctionApp)」をご覧ください。

## <a name="next-steps"></a>次の手順

[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  