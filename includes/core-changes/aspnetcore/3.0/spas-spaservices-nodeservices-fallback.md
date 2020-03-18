---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522656"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>SPAs: SpaServices et NodeServices ne retomberent plus à l’enregistreur de console

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>et <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> n’affichera pas les journaux de console à moins que la connexion ne soit configurée.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`Microsoft.AspNetCore.SpaServices`et `Microsoft.AspNetCore.NodeServices` utilisé pour créer automatiquement un enregistreur de console lors de la connexion n’est pas configuré.

#### <a name="new-behavior"></a>Nouveau comportement

`Microsoft.AspNetCore.SpaServices`et `Microsoft.AspNetCore.NodeServices` n’affichera pas les journaux de console à moins que la connexion ne soit configurée.

#### <a name="reason-for-change"></a>Raison du changement

Il est nécessaire de s’aligner sur la façon dont d’autres paquets ASP.NET Core implémentent l’enregistrement.

#### <a name="recommended-action"></a>Action recommandée

Si l’ancien comportement est nécessaire, pour `services.AddLogging(builder => builder.AddConsole())` configurer l’enregistrement de console, ajouter à votre `Setup.ConfigureServices` méthode.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!--

#### Affected APIs

Not detectable via API analysis

-->
