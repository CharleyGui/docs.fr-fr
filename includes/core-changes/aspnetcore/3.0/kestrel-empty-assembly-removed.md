---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394381"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel: L’assemblage HTTPS vide supprimé

L’assemblage <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> a été supprimé.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Raison du changement

Dans ASP.NET Core 2.1, le `Microsoft.AspNetCore.Server.Kestrel.Https` contenu de <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>ont été déplacés à . Ce changement a été fait d’une manière non-rupture en utilisant des `[TypeForwardedTo]` attributs.

#### <a name="recommended-action"></a>Action recommandée

- Les bibliothèques `Microsoft.AspNetCore.Server.Kestrel.Https` faisant référence à 2.0 devraient mettre à jour toutes les dépendances ASP.NET Core à 2,1 ou plus tard. Sinon, ils peuvent se briser lorsqu’ils sont chargés dans une application ASP.NET Core 3.0.
- Les applications et les bibliothèques ciblant ASP.NET Core 2.1 et `Microsoft.AspNetCore.Server.Kestrel.Https` ultérieurement devraient supprimer toute référence directe au paquet NuGet.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
