---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032585"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel : un assembly HTTPs vide a été supprimé

L’assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> a été supprimé.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Motif de modification

Dans ASP.NET Core 2,1, le contenu de `Microsoft.AspNetCore.Server.Kestrel.Https` a été déplacé vers <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName> . Cette modification a été effectuée de manière non-critique à l’aide d' `[TypeForwardedTo]` attributs.

#### <a name="recommended-action"></a>Action recommandée

- Les bibliothèques référençant `Microsoft.AspNetCore.Server.Kestrel.Https` 2,0 doivent mettre à jour toutes les dépendances de ASP.net core à 2,1 ou version ultérieure. Dans le cas contraire, ils peuvent s’arrêter lorsqu’ils sont chargés dans une application ASP.NET Core 3,0.
- Les applications et les bibliothèques qui ciblent ASP.NET Core 2,1 et versions ultérieures doivent supprimer toutes les références directes au `Microsoft.AspNetCore.Server.Kestrel.Https` package NuGet.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
