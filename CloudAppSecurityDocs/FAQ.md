---
title: よく寄せられる質問 - Cloud App Security | Microsoft ドキュメント
description: この記事では、Cloud App Security に関するよく寄せられる質問と回答を示します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 53477b78350b2377e71780769cf50c1df48bcbdf
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176673"
---
# <a name="frequently-asked-questions"></a>よく寄せられる質問

*適用対象:Microsoft Cloud App Security*

この記事では、Cloud App Security に関するよく寄せられる質問と回答を示します。

## <a name="what-kind-of-permissions-do-i-need-to-access-cloud-app-security"></a>Cloud App Security にアクセスするには、どのようなアクセス許可が必要ですか?

Azure Active Directory での全体管理者、コンプライアンス管理者、またはセキュリティ管理者である必要があります。 Office 365 セキュリティ/コンプライアンス センターでこれらのロールを持っているだけでは十分ではありません。 Azure Active Directory でユーザーを全体管理者、コンプライアンス管理者、またはセキュリティ管理者として設定するには、PowerShell を使用できます。 次のコマンドレットを実行します。

```powershell

 $cred = Get-Credential
 Connect-MsolService -credential $cred
 Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
```

 または

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>次の手順  
クラウド アプリの使用を制御するポリシーを設定して使用する方法については、「[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)」をご覧ください。   

Premier サポートをご利用のお客様は、[Premier ポータル](https://premier.microsoft.com/)から直接 Cloud App Security を選択することもできます。  
