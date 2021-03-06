---
title: 非ドメイン メンバー ファイル サーバーでハッシュの発行を有効にする
description: このトピックは、BranchCache 展開ガイドの Windows Server 2016、ブランチ オフィスに WAN 帯域幅使用量を最適化するために分散され、ホスト型キャッシュ モードで BranchCache を展開する方法を示しますの一部
manager: brianlic
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 11584b73-f9e2-4530-afa5-b8df970e6b24
ms.author: pashort
author: shortpatti
ms.openlocfilehash: e870863b497c17b4b56265d99d91274e34690767
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71356542"
---
# <a name="enable-hash-publication-for-non-domain-member-file-servers"></a>非ドメイン メンバー ファイル サーバーでハッシュの発行を有効にする

>適用対象:Windows Server (半期チャネル)、Windows Server 2016

次の手順を使用して、Windows Server 2016 を実行しているファイルサーバーで、ファイルサービスサーバーの役割がインストールされている**ネットワークファイル用 branchcache**役割サービスを使用して、ローカルコンピューターグループポリシーを使用して BranchCache のハッシュの発行を構成できます。  
  
この手順は、ドメインメンバー以外のファイルサーバーでの使用を目的としています。 ドメインメンバーファイルサーバーでこの手順を実行し、ドメイングループポリシーを使用して BranchCache を構成した場合、ドメイングループポリシーの設定はローカルのグループポリシー設定よりも優先されます。  
  
メンバーシップ **管理者**, 、または同等がこの手順を実行するために必要な最小値。  
  
> [!NOTE]  
> 1つまたは複数のドメインメンバーファイルサーバーがある場合は、それらを Active Directory Domain Services の組織単位 (OU) に追加し、グループポリシーを使用して、個別に構成するのではなく、一度にすべてのファイルサーバーに対してハッシュの発行を構成することができます。各ファイルサーバー。 詳細については、「 [ドメイン メンバー ファイル サーバーでハッシュの発行を有効にする
](../../branchcache/deploy/Enable-Hash-Publication-for-Domain-Member-File-Servers.md)」を参照してください。  
  
### <a name="to-enable-hash-publication-for-one-file-server"></a>1つのファイルサーバーでハッシュの発行を有効にするには  
  
1.  Windows PowerShell を開き、「 **mmc**」と入力して、Enter キーを押します。 Microsoft 管理コンソール (MMC) が開きます。  
  
2.  MMC で、 **[ファイル]** メニューの **[スナップインの追加と削除]** をクリックします。 **[スナップインの追加と削除]** ダイアログボックスが表示されます。  
  
3.  **[スナップインの追加と削除]** の **[使用できるスナップ]** イン で、 **[グループポリシーオブジェクトエディター]** をダブルクリックします。 [ローカルコンピューター] オブジェクトが選択された状態で、グループポリシーウィザードが開きます。 **[完了]** をクリックし、 **[OK]** をクリックします。  
  
4.  ローカルグループポリシーエディター MMC で、次のパスを展開します。**ローカルコンピューターポリシー**、**コンピューターの構成**、**管理用テンプレート**、**ネットワーク**、 **Lanman サーバー**。 **[Lanman サーバー]** をクリックします。  
  
5.  詳細ウィンドウで、 **[BranchCache のハッシュの発行]** をダブルクリックします。 **[BranchCache のハッシュの発行]** ダイアログボックスが開きます。  
  
6.  **[BranchCache のハッシュの発行]** ダイアログボックスで、 **[有効]** をクリックします。  
  
7.  **[オプション]** で、 **[すべての共有フォルダーに対してハッシュの発行を許可する]** をクリックし、次のいずれかをクリックします。  
  
    1.  このコンピューター上のすべての共有フォルダーに対してハッシュの発行を有効にするには、[**すべての共有フォルダーでハッシュの発行を許可**する] をクリックします。  
  
    2.  BranchCache が有効になっている共有フォルダーに対してのみハッシュの発行を有効にするには、[ **branchcache が有効になっている共有フォルダーに対してのみハッシュの発行を許可**する] をクリックします。  
  
    3.  ファイル共有で BranchCache が有効になっている場合でも、コンピューター上のすべての共有フォルダーでハッシュの発行を許可しない場合は、[**すべての共有フォルダーでハッシュの発行を許可**しない] をクリックします。  
  
8.  **[OK]** をクリックします。  
  


