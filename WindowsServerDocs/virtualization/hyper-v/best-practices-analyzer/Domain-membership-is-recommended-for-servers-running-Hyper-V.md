---
title: ドメインメンバーシップは、Hyper-v を実行するサーバーに推奨されます。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 2f4578e5-0848-46b4-a50b-7dbd480b80bf
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 48ea52e962f2f476d1428a69bab6c6e38c4ec005
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71364918"
---
# <a name="domain-membership-is-recommended-for-servers-running-hyper-v"></a>ドメインメンバーシップは、Hyper-v を実行するサーバーに推奨されます。

>適用先:Windows Server 2016


  
*ベストプラクティスとスキャンの詳細については、「* [ベストプラクティスアナライザー](https://go.microsoft.com/fwlink/?LinkId=122786)」を参照してください。  
  
|プロパティ|詳細|  
|-|-|  
|**オペレーティング システム**|Windows Server 2016|  
|**製品/機能**|Hyper-V|  
|**順**|警告|  
|**カテゴリ**|構成|  
  
次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。  
  
## <a name="issue"></a>問題  
  
*このサーバーは、ワークグループのメンバーです。*  
  
## <a name="impact"></a>影響  
  
*このサーバーの一元管理はありません。*  
  
このコンピューターをドメインに参加させることで、id、セキュリティ、および監査に関するポリシーを使用して一元管理を行うことができます。  
  
## <a name="resolution"></a>解決方法  
  
*使用可能なドメイン環境がある場合は、このサーバーをそのドメインに参加させます。*  
  
> [!IMPORTANT]  
> このコンピューターの仮想マシンで実行されているワークロードを確認し、このコンピューターをドメインに参加させることによるセキュリティへの影響があるかどうかを判断することをお勧めします。 仮想マシンのいずれかが仮想化ドメインコントローラーである場合は、「[仮想化ドメインコントローラーの計画に関する考慮事項](https://go.microsoft.com/fwlink/?LinkId=190192)(https://go.microsoft.com/fwlink/?LinkId=190192) 」を参照してください。  
  
コンピューターをドメインに参加させるには、コンピューターとドメインに対するアクセス許可が必要です。   
- コンピューターには、Administrators グループのメンバーであるユーザーアカウントが必要です。 この種類のアカウントでログオンするか、メッセージが表示されたらアカウントのユーザー名とパスワードを入力します。   
- ドメインでは、ドメインにコンピューターを参加させる権限を持つユーザーアカウントが必要になります。 ユーザー名とパスワードの入力を求められます。  
  
手順については、「[コンピューターをドメインに参加](https://go.microsoft.com/fwlink/?LinkId=190193)させる (https://go.microsoft.com/fwlink/?LinkId=190193) 」を参照してください。  
  


