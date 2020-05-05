---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394381"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel : un assembly HTTPs vide a été supprimé

L’assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> a été supprimé.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Motif de modification

Dans ASP.NET Core 2,1, le contenu de `Microsoft.AspNetCore.Server.Kestrel.Https` a été déplacé <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>vers. Cette modification a été effectuée de manière non-critique à `[TypeForwardedTo]` l’aide d’attributs.

#### <a name="recommended-action"></a>Action recommandée

- Les bibliothèques `Microsoft.AspNetCore.Server.Kestrel.Https` référençant 2,0 doivent mettre à jour toutes les dépendances de ASP.NET Core à 2,1 ou version ultérieure. Dans le cas contraire, ils peuvent s’arrêter lorsqu’ils sont chargés dans une application ASP.NET Core 3,0.
- Les applications et les bibliothèques qui ciblent ASP.NET Core 2,1 et versions ultérieures doivent `Microsoft.AspNetCore.Server.Kestrel.Https` supprimer toutes les références directes au package NuGet.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
