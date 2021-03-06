---
title: shrink
description: 'Windows コマンドに関するトピック * * * *- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec87cc7c-9846-465e-a10d-4ee10db4f4e6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f0e5caa0103018c94671d7441a6d2349ab734be6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370901"
---
# <a name="shrink"></a>shrink

>適用先:Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Diskpart の [圧縮] コマンドを使用すると、指定した量だけ選択したボリュームのサイズが縮小されます。 このコマンドでは、ボリュームの最後に、未使用の領域から使用可能な空きディスク領域を作成します。

## <a name="syntax"></a>構文
```
shrink [desired=<n>] [minimum=<n>] [nowait] [noerr]
shrink querymax [noerr]
```
## <a name="parameters"></a>パラメーター

|  パラメーター  |                                                                                             説明                                                                                              |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 必要な = <n> |                                                     メガバイト (MB)、ボリュームのサイズを小さく領域の必要な量を指定します。                                                     |
| 最小値 = <n> |                                                           (Mb) ではボリュームのサイズを小さくには、領域の最小容量を指定します。                                                           |
|  querymax   |                       ボリュームを削減できます (mb) の領域の最大量を返します。 アプリケーションは、ボリュームを現在アクセスしている場合、この値を変更できます。                        |
|   nowait    |                                                       圧縮処理がまだ進行中のときに、直ちにコマンドを返します。                                                        |
|    noerr    | スクリプトの場合のみ。 エラーが発生した場合、DiskPart はエラーが発生しなかったかのようにコマンドを処理し続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="remarks"></a>コメント
- NTFS ファイル システムでフォーマットされている場合またはファイル システムがあるない場合にのみ、ボリュームのサイズを小さくことができます。
- このコマンドは、ベーシック ボリュームとシンプル ボリュームまたはスパン ダイナミック ボリュームは機能します。
- 目的の量が指定されていない場合、ボリュームは最小値 (指定されている場合) によって縮小されます。
- 最小量が指定されていない場合は、必要な量だけボリュームが減少します (指定されている場合)。
- 最小量も目的の量も指定されていない場合、ボリュームはできるだけ小さくなります。
- 最小量が指定されていても、十分な空き領域がない場合、コマンドは失敗します。
- この操作を成功させるのには、ボリュームを選択してください。 使用して、 **ボリュームを選択して** コマンドのボリュームを選択し、それにフォーカスをします。
- このコマンドは、相手先ブランド供給業者 (OEM) パーティション、拡張ファームウェア インターフェイス (EFI) システム パーティション、または回復パーティションについては動作しません。
  ## <a name="BKMK_examples"></a>例
  選択したボリュームのサイズを減らすためを 250 および 500 件のメガバイト数の間で最大の可能な量には、次のように入力します。
  ```
  shrink desired=500 minimum=250
  ```
  削減されることができます、ボリュームを mb 単位の最大数を表示するには、次のように入力します。
  ```
  shrink querymax
  ```

[サイズ変更-パーティション](https://technet.microsoft.com/library/hh848680.aspx)
