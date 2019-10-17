---
ms.openlocfilehash: f103c96588bae167216d09a82973a4a7abfb5cc3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394138"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Protection des données : DataProtection. AzureStorage utilise les nouvelles API de stockage Azure

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> dépend des [bibliothèques de stockage Azure](https://github.com/Azure/azure-storage-net). Ces bibliothèques ont renommé leurs assemblys, leurs packages et leurs espaces de noms. À partir de ASP.NET Core 3,0, `Microsoft.AspNetCore.DataProtection.AzureStorage` utilise les nouvelles API et packages de préfixe @no__t 1-1.

Pour toute question sur les API de stockage Azure, utilisez <https://github.com/Azure/azure-storage-net>. Pour plus d’informations sur ce problème, consultez [ASPNET/AspNetCore # 8472](https://github.com/aspnet/AspNetCore/issues/8472).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Le package a référencé le package NuGet `WindowsAzure.Storage`.

#### <a name="new-behavior"></a>Nouveau comportement

Le package fait référence au package NuGet `Microsoft.Azure.Storage.Blob`.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification permet à `Microsoft.AspNetCore.DataProtection.AzureStorage` de migrer vers les packages de stockage Azure recommandés.

#### <a name="recommended-action"></a>Action recommandée

Si vous avez encore besoin d’utiliser les anciennes API de stockage Azure avec ASP.NET Core 3,0, ajoutez une dépendance directe au package [WindowsAzure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) . Ce package peut être installé avec les nouvelles API `Microsoft.Azure.Storage`.

Dans de nombreux cas, la mise à niveau implique uniquement la modification des instructions `using` pour utiliser les nouveaux espaces de noms :

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
