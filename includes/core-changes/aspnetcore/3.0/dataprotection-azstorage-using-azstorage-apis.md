---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902019"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Protection des données : DataProtection. AzureStorage utilise les nouvelles API de stockage Azure

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>dépend des [bibliothèques de stockage Azure](https://github.com/Azure/azure-storage-net). Ces bibliothèques ont renommé leurs assemblys, leurs packages et leurs espaces de noms. À partir de ASP.NET Core 3,0 `Microsoft.AspNetCore.DataProtection.AzureStorage` , utilise les `Microsoft.Azure.Storage.`nouvelles API et les packages préfixés.

Pour toute question sur les API de stockage Azure <https://github.com/Azure/azure-storage-net>, utilisez. Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 8472](https://github.com/dotnet/aspnetcore/issues/8472).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le package a référencé le `WindowsAzure.Storage` package NuGet.

#### <a name="new-behavior"></a>Nouveau comportement

Le package fait référence `Microsoft.Azure.Storage.Blob` au package NuGet.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification permet `Microsoft.AspNetCore.DataProtection.AzureStorage` de migrer vers les packages de stockage Azure recommandés.

#### <a name="recommended-action"></a>Action recommandée

Si vous avez encore besoin d’utiliser les anciennes API de stockage Azure avec ASP.NET Core 3,0, ajoutez une dépendance directe au package [WindowsAzure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) . Ce package peut être installé avec les nouvelles `Microsoft.Azure.Storage` API.

Dans de nombreux cas, la mise à niveau implique `using` uniquement la modification des instructions pour utiliser les nouveaux espaces de noms :

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
