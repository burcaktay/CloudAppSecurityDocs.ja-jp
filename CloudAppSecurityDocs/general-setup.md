---
title: Cloud App Security で組織の設定を入力する
description: この記事では、Cloud App Security に組織の情報を入力する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2e7e57b0-db54-4d75-896c-4700dd9abe48
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 74816bcdd872d000e56f61431bfb26cc04386901
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176656"
---
# <a name="basic-setup-for-cloud-app-security"></a>Cloud App Security の基本セットアップ

*適用対象:Microsoft Cloud App Security*

ここでは、Microsoft Cloud App Security ポータルをカスタマイズする手順について説明します。

## <a name="prerequisites"></a>前提条件 
ポータル アクセスの場合、次の IP アドレスをファイアウォールのホワイトリストに追加し、Cloud App Security ポータルにアクセスできるようにする必要があります。  
  
- 104.42.231.28  
  
> [!NOTE]  
>  URL および IP アドレスが変更されときに更新されるようにするには、「[Office 365 の URL および IP アドレス範囲](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)」で説明されているように RSS を購読します。  
  
## <a name="set-up-the-portal"></a>ポータルのセットアップ  
  
1. Cloud App Security ポータルのメニュー バーで、設定の歯車アイコン ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックし、**[設定]** を選択して組織の詳細を構成します。     

2. **[組織の詳細]** に自社の**組織の表示名**を指定することは重要です。 これは、システムから送信される電子メールや Web ページに表示されます。  
  
3. **環境名** (テナント) を指定します。 この情報は、複数のテナントを管理する場合に特に重要です。  
  
4. システムから送信されるメールや Web ページで表示される**ロゴ**を指定することもできます。 ロゴには、150 x 50 ピクセル以下のサイズで背景が透明色の png ファイルを使用する必要があります。  

5. **マネージド ドメイン**のリストを追加します。 マネージド ドメインの追加は非常に重要な手順です。 マネージド ドメインは、Cloud App Security により、内部ユーザーと外部ユーザー、およびファイルの共有の可否を判別する際に使用されます。 この情報は、レポートとアラートに使用されます。  
   
    - 内部として構成されていないドメイン内のユーザーは、外部とマークされます。 外部ユーザーについては、アクティビティまたはファイルはスキャンされません。

6. Azure Information Protection の統合により統合を行う場合は、「[Azure Information Protection の統合](azip-integration.md)」を参照してください。 

    - Azure Information Protection の統合を行うには、[Office 365 用アプリ コネクタ](connect-office-365-to-microsoft-cloud-app-security.md)を有効にする必要があります。
  
7. ポータル設定は、この画面からいつでもバックアップできます。 **[ポータル設定をエクスポート]** をクリックすると、ポリシー規則やユーザー グループ、IP アドレス範囲などのポータル設定がすべて記述された json ファイルが作成されます。  
  
   
> [!NOTE] 
> ExpressRoute を使用している場合は、Cloud App Security は Azure に展開され、[ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) に完全に統合されます。 検出ログのアップロードを含む、Cloud App Security アプリとのすべての通信、および Cloud App Security に送信されるトラフィックは、ExpressRoute の**パブリック ピアリング**経由でルーティングされるため、待機時間、パフォーマンス、およびセキュリティが改善されます。 お客様側で設定を行う必要はありません。 <br></br>パブリック ピアリングの詳細については、「[ExpressRoute 回線とルーティング ドメイン](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/)」を参照してください。  
    
## <a name="next-steps"></a>次の手順  
[Cloud Discovery のセットアップ](set-up-cloud-discovery.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  