---
title: Microsoft データ分類サービスを使用した Cloud App Security コンテンツ検査
description: この記事では、Microsoft データ分類サービスを使用して DLP コンテンツ検査を実行する場合に Microsoft Cloud App Security で従うプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: bf25d1e6-e5dc-449f-b50e-1cd4a21b6d3d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d060980768426cbabe0f3c7cb976aadf88037b7d
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53174990"
---
# <a name="microsoft-data-classification-services-integration"></a>Microsoft データ分類サービスの統合

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security では、Microsoft データ分類サービスをネイティブに使用して、クラウド アプリのファイルを分類できます。 Microsoft データ分類サービスには、Office 365、Azure Information Protection、および Microsoft Cloud App Security の間での、統合された情報保護エクスペリエンスが用意されています。 分類サービスでは、Microsoft Cloud App Security によって保護されているサード パーティのクラウド アプリにデータ分類を拡張できます。これにより、さらに多くのアプリ間で既存の決定事項を使用できます。

>[!NOTE]
> この機能は現在、米国、ヨーロッパ (フランスを除く)、および APAC で利用できます。


## <a name="enable-content-inspection-with-data-classification-services"></a>データ分類サービスを使用するコンテンツ検査を有効にする

追加構成なしで、**Microsoft データ分類サービス**を使用するように**検査方法**を設定するためのオプションがあります。 このオプションは、Microsoft Cloud App Security のファイルに対するデータ漏えい保護のポリシーを作成するときに便利です。


1. [ファイル ポリシー](data-protection-policies.md) ページの **[検査方法]** で、**[データ分類サービス]** を選択します。
     ![データ分類サービスの設定](./media/dcs-enable.png)
2. ポリシーを適用するタイミングについて、条件が **1 つ以上**満たされた場合、または**すべて**満たされた場合のいずれかを選択します。
3. **機密情報の種類**を選び、**検査の種類を選択**します。
 ![データ分類サービスの設定](./media/dcs-sensitive-information-type.png)

4. [既定の機密情報の種類](https://support.office.com/article/what-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b)を使用して、Microsoft Cloud App Security で保護されているファイルに対する操作を定義することができます。 [Office 365 のカスタムの機密情報の種類](https://support.office.com/article/create-a-custom-sensitive-information-type-82c382a5-b6db-44fd-995d-b333b3c7fc30)のいずれかを再利用することもできます。

5. 必要に応じて、一致の最後の 4 文字のマスクを解除できます。 既定では、マスクされた一致がコンテキストの中で示され、一致の前後の 40 文字が含まれます。 このチェック ボックスをオンにした場合、一致自体の最後の 4 文字のマスクが解除されます。

6. また、ポリシーのためにアラートとガバナンス アクションを設定することもできます。 詳細については、[ファイル ポリシー](data-protection-policies.md)と[ガバナンス アクション](governance-actions.md)に関するページをご覧ください。

これらのポリシーを設定すると、その他の承認されたクラウド アプリすべてに Office 365 DLP 機能の長所を簡単に拡張できます。また、Microsoft Cloud App Security によって提供されるツールセット (たとえば、[Azure Information Protection 分類ラベルを自動的に適用する](azip-integration.md)機能や、共有アクセス許可を制御する機能) をフルに使用して、アプリに格納されているデータを保護できます。



## <a name="next-steps"></a>次の手順  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  