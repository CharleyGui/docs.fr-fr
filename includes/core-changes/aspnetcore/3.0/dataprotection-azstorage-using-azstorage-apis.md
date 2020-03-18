---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902019"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Protection des données : DataProtection.AzureStorage utilise de nouvelles API de stockage Azure

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>dépend des [bibliothèques de stockage Azure](https://github.com/Azure/azure-storage-net). Ces bibliothèques ont rebaptisé leurs assemblages, forfaits et espaces de noms. À partir de ASP.NET Core `Microsoft.AspNetCore.DataProtection.AzureStorage` 3.0, `Microsoft.Azure.Storage.`utilise les nouvelles API et les paquets préfixés.

Pour des questions sur les API de stockage Azure, utilisez <https://github.com/Azure/azure-storage-net>. Pour discussion sur cette question, voir [dotnet/aspnetcore 8472](https://github.com/dotnet/aspnetcore/issues/8472).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le paquet faisait `WindowsAzure.Storage` référence au paquet NuGet.

#### <a name="new-behavior"></a>Nouveau comportement

Le paquet `Microsoft.Azure.Storage.Blob` fait référence au package NuGet.

#### <a name="reason-for-change"></a>Raison du changement

Ce changement `Microsoft.AspNetCore.DataProtection.AzureStorage` permet de migrer vers les paquets de stockage Azure recommandés.

#### <a name="recommended-action"></a>Action recommandée

Si vous avez encore besoin d’utiliser les anciennes API de stockage Azure avec ASP.NET Core 3.0, ajoutez une dépendance directe au package [WindowsAzure.Storage.](https://www.nuget.org/packages/WindowsAzure.Storage/) Ce paquet peut être installé `Microsoft.Azure.Storage` aux côtés des nouvelles API.

Dans de nombreux cas, la `using` mise à niveau ne consiste qu’à modifier les instructions pour utiliser les nouveaux espaces de noms :

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
