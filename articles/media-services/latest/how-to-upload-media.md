---
title: メディアをアップロードする
titleSuffix: Azure Media Services
description: ストリーミングまたはエンコードのためにメディアをアップロードする方法について説明します。
services: media-services
documentationcenter: ''
author: IngridAtMicrosoft
manager: femila
editor: ''
ms.service: media-services
ms.workload: ''
ms.topic: tutorial
ms.date: 08/11/2020
ms.author: inhenkel
ms.openlocfilehash: a046a3caba9a0909d873356bda8d1fa6cf1f9860
ms.sourcegitcommit: 6fc156ceedd0fbbb2eec1e9f5e3c6d0915f65b8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2020
ms.locfileid: "88719259"
---
# <a name="upload-media-for-streaming-or-encoding"></a>ストリーミングまたはエンコードのためにメディアをアップロードする

Media Services で、アセットに関連付けられている BLOB コンテナーにデジタル ファイル (メディア) をアップロードします。 [Asset](/rest/api/media/operations/asset) エンティティには、ビデオ、オーディオ、画像、サムネイル コレクション、テキスト トラック、クローズド キャプション ファイル (各ファイルのメタデータを含む) を格納できます。 ファイルをアセットのコンテナーにアップロードすると、コンテンツがクラウドに安全に保存され、処理したりストリーミングしたりできるようになります。

ただし、作業を開始する前に、いくつかの値を収集するか、検討する必要があります。

1. アップロードするファイルへのローカル ファイル パス
1. アセット (コンテナー) のアセット ID
1. 拡張子を含む、アップロードしたファイルに使用する名前
1. 使用しているストレージ アカウントの名前
1. ストレージ アカウントのアクセス キー

## <a name="portal"></a>[ポータル](#tab/portal/)

[!INCLUDE [Upload files with the portal](./includes/task-upload-file-to-asset-portal.md)]

## <a name="cli"></a>[CLI](#tab/cli/)

[!INCLUDE [Upload files with the portal](./includes/task-upload-file-to-asset-cli.md)]

## <a name="rest"></a>[REST](#tab/rest/)

[Postman やその他の REST 方法を使用してアセットを作成し、そのアセットの SAS URL を取得](how-to-create-asset.md?tabs=rest)したら、Azure Storage API または SDK ([Storage REST API](../../storage/common/storage-rest-api-auth.md) や [.NET SDK](../../storage/blobs/storage-quickstart-blobs-dotnet.md) など) を使用します。

---
<!-- add these to the tabs when available -->
その他の方法については、[.NET](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-dotnet)、[Java](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-java)、[Python](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-python)、[JavaScript (Node.js)](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-nodejs) での BLOB の操作に関する [Azure Storage のドキュメント](https://docs.microsoft.com/azure/storage/blobs/)を参照してください。

## <a name="next-steps"></a>次のステップ

> [Media Services の概要](media-services-overview.md)
