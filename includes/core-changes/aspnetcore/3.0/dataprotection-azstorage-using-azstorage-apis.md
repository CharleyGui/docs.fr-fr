---
ms.openlocfilehash: f6e4c3d5c5fd020562e48515554136e0f8b6785c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440421"
---
### <a name="data-protection-dataprotectionblobs-uses-new-azure-storage-apis"></a>Protection des données : DataProtection. blob utilise les nouvelles API de stockage Azure

`Azure.Extensions.AspNetCore.DataProtection.Blobs` dépend des [bibliothèques de stockage Azure](https://github.com/Azure/azure-storage-net). Ces bibliothèques ont renommé leurs assemblys, leurs packages et leurs espaces de noms. À partir de ASP.NET Core 3,0, `Azure.Extensions.AspNetCore.DataProtection.Blobs` utilise les nouvelles `Azure.Storage.` API et les packages préfixés.

Pour toute question sur les API de stockage Azure, utilisez <https://github.com/Azure/azure-storage-net> . Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le package a référencé le `WindowsAzure.Storage` package NuGet.
Le package fait référence au `Microsoft.Azure.Storage.Blob` package NuGet.

#### <a name="new-behavior"></a>Nouveau comportement

Le package fait référence au `Azure.Storage.Blob` package NuGet.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification permet `Azure.Extensions.AspNetCore.DataProtection.Blobs` de migrer vers les packages de stockage Azure recommandés.

#### <a name="recommended-action"></a>Action recommandée

Si vous avez encore besoin d’utiliser les anciennes API de stockage Azure avec ASP.NET Core 3,0, ajoutez une dépendance directe au package [WindowsAzure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) ou [Microsoft. Azure. Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/). Ce package peut être installé avec les nouvelles `Azure.Storage` API.

Dans de nombreux cas, la mise à niveau implique uniquement la modification des `using` instructions pour utiliser les nouveaux espaces de noms :

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
- using Microsoft.Azure.Storage;
- using Microsoft.Azure.Storage.Blob;
+ using Azure.Storage;
+ using Azure.Storage.Blobs;
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
