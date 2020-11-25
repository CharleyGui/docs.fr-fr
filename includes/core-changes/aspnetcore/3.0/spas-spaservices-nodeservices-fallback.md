---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032683"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>SPAs : SpaServices et NodeServices ne sont plus renvoyés à l’enregistreur de console

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> et <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> n’affichent pas les journaux de la console, sauf si la journalisation est configurée.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`Microsoft.AspNetCore.SpaServices` et `Microsoft.AspNetCore.NodeServices` permettent de créer automatiquement un journal de console lorsque la journalisation n’est pas configurée.

#### <a name="new-behavior"></a>Nouveau comportement

`Microsoft.AspNetCore.SpaServices` et `Microsoft.AspNetCore.NodeServices` n’affichent pas les journaux de la console, sauf si la journalisation est configurée.

#### <a name="reason-for-change"></a>Motif de modification

Il est nécessaire de s’aligner sur la manière dont les autres packages d’ASP.NET Core implémentent la journalisation.

#### <a name="recommended-action"></a>Action recommandée

Si l’ancien comportement est requis, pour configurer la journalisation de la console, ajoutez `services.AddLogging(builder => builder.AddConsole())` à votre `Setup.ConfigureServices` méthode.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!--

#### Affected APIs

Not detectable via API analysis

-->
