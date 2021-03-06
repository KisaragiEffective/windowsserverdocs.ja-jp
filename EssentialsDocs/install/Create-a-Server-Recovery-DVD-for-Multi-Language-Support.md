---
title: 複数言語サポート用のサーバー回復 DVD の作成
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.topic: article
ms.assetid: c7da0f6c-9732-4784-9c28-7dad72c4071d
author: daveba
ms.author: daveba
ms.openlocfilehash: 59d8d41e5836ba88b405a058c8340f454b081c06
ms.sourcegitcommit: 2082335e1260826fcbc3dccc208870d2d9be9306
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69980246"
---
# <a name="create-a-server-recovery-dvd-for-multi-language-support"></a>複数言語サポート用のサーバー回復 DVD の作成

>適用先:Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

##  <a name="BKMK_MLHeadedRecovery"></a>ローカルで管理されているサーバーで複数の言語をサポートするためのサーバーセットアップとサーバー回復 DVD の作成  
  
> [!NOTE]
>  まず、 [チュートリアル「」の説明に従って、多言語の Windows イメージを作成する必要があります。Windows Server Essentials install.wim](https://technet.microsoft.com/library/jj126995) pack をインストールする前に、多言語の windows イメージを作成します。  
  
 セットアップには、Windows プレインストール環境 (Windows PE) と初期構成という 2 つのフェーズがあります。 既定では、初期構成には言語選択ページは表示されません。  
  
- OEM リモート管理インストールまたは OEM プレインストール シナリオでは、次のコマンドを使用してレジストリ キーを追加し、初期構成で言語選択ページを表示する必要があります。  
  
  ```  
  %systemroot%\system32\reg.exe add "HKLM\Software\microsoft\windows server\setup" /v ShowPreinstallPages /t REG_SZ /d true /f  
  ```  
  
  > [!IMPORTANT]
  >  OEM は実験環境でイメージを作成する際、セットアップの Windows PE フェーズで言語として **英語** を選択する必要があります。  
  
- ROK (Reseller Option Kit) シナリオでは、顧客には DVD と場合によりハードウェアが納品されます。 顧客は、Windows PE セットアップ中に言語を選択できるため、初期構成中に言語選択ページは表示されません。  
  
  複数の言語を含む 1 枚の 2 層 DVD の出荷を選択することができます。  
  
  ここでは、言語サポートを Windows セットアップに追加する方法について説明します。 Windows PE 3.0 をカスタマイズするための主要なツールは、展開イメージのサービスと管理 (DISM) というコマンド ライン ツールです。 このソリューションでは、次のシナリオが可能になります。  
  
1.  多言語インストールの作成  
  
2.  配布可能なメディアの作成  
  
### <a name="prerequisites"></a>前提条件  
 多言語サポートを Windows セットアップに追加するには、次のものが必要です。  
  

-   カスタマイズした WinPE イメージの作成に必要なツールとソース ファイルのすべてを提供するテクニシャン コンピューター。 詳細については、「 [Prepare the Technician Computer](Prepare-the-Technician-Computer.md)」を参照してください。  

-   カスタマイズした WinPE イメージの作成に必要なツールとソース ファイルのすべてを提供するテクニシャン コンピューター。 詳細については、「 [Prepare the Technician Computer](../install/Prepare-the-Technician-Computer.md)」を参照してください。  

  
-   Windows Server Essentials DVD。  
  
-   Windows Server Essentials 言語パック DVD。  
  
###  <a name="BKMK_Steps"></a>複数言語サポートの追加  
 Windows セットアップに複数の言語サポートを追加するには、Windows Server 2012 および Windows Server Essentials 言語パックを追加して、インストール .wim を更新します。  
  
#### <a name="update-installwim"></a>Install.wim の更新  
 この手順では、Windows Server 2012 および Windows Server Essentials 言語パックをインストール .wim に追加します。  
  
> [!NOTE]
>  Windows Server 2012 の言語パックがインストールされていることを確認します。 これで適切なブランド化を取得できます。 Windows Server 2012 多言語ユーザーインターフェイス言語パックは、 [Microsoft.com](https://www.microsoft.com/OEM/en/installation/downloads/Pages/technical-downloads.aspx)で入手できます。 [チュートリアル「」で説明されている手順に従ってください。Windows Server Essentials 言語パックをインストールする](https://technet.microsoft.com/library/jj126995.aspx)前に、多言語 windows イメージの作成に関する多言語の windows イメージを作成します。  
>   
>  Windows Server Essentials 言語パックは、言語パックメディア () の言語パックメディア\\で利用でき\>ます。この言語パックは、< の選別します。  
  
> [!NOTE]
>  Windows Server 2012 のリリース以前は、すべての言語パックを利用できない場合があります。  
  
###### <a name="to-add-language-packs-to-installwim"></a>言語パックを Install.wim に追加するには  
  
1.  次のようにオペレーティング システムと製品の言語パックを install.wim に追加します (この例では、フランス語を使用します)。  
  
    ```  
    Dism /Mount-Wim /WimFile:C:\my_distribution\sources\install.wim /index:1 /MountDir:C:\InstallMount  
    Mkdir c:\temp_Scratch  
    Dism /Image:C:\InstallMount /ScratchDir:C:\temp_Scratch /Add-Package /PackagePath:<path_to_OS_language_packs>\fr-fr\lp.cab  
    Dism /Image:C:\InstallMount /ScratchDir:C:\temp_Scratch /Add-Package /PackagePath:<OCD\Language Packs\FR-FR\lp.cab  
  
    ```  
  

2.  「[複数言語のクライアント復元メディアの作成](Build-Multi-Language-Client-Restore-Media.md)」で説明されている手順に従って、クライアントバックアップ復元 USB フラッシュドライブの作成をサポートする言語固有のファイルを追加します。  

2.  「[複数言語のクライアント復元メディアの作成](../install/Build-Multi-Language-Client-Restore-Media.md)」で説明されている手順に従って、クライアントバックアップ復元 USB フラッシュドライブの作成をサポートする言語固有のファイルを追加します。  

  
3.  `DISM /Gen-LangINI` コマンドを使用して、追加の言語サポートを反映するようにルーズ メディア内の Lang.ini ファイルを再作成します。次に例を示します。  
  
    ```  
    Dism /image:C:\InstallMount /Gen-LangINI /distribution:C:\my_distribution  
  
    ```  
  
4.  `DISM /unmount /commit` コマンドを使用して、変更をイメージに保存し直します。次に例を示します。  
  
    ```  
    Dism /Unmount-Wim /MountDir:C:\InstallMount /Commit  
    ```  
  
## <a name="see-also"></a>関連項目  

 [イメージの作成とカスタマイズ](Creating-and-Customizing-the-Image.md)   
 [追加のカスタマイズ](Additional-Customizations.md)   
 [展開のためのイメージの準備](Preparing-the-Image-for-Deployment.md)   
 [カスタマー エクスペリエンスのテスト](Testing-the-Customer-Experience.md)

 [イメージの作成とカスタマイズ](../install/Creating-and-Customizing-the-Image.md)   
 [追加のカスタマイズ](../install/Additional-Customizations.md)   
 [展開のためのイメージの準備](../install/Preparing-the-Image-for-Deployment.md)   
 [カスタマー エクスペリエンスのテスト](../install/Testing-the-Customer-Experience.md)

