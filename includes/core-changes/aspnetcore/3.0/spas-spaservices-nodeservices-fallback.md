---
ms.openlocfilehash: 1017801346e65940e4dc075ef72f7a00d7e6bcd9
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394476"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>SPAs : SpaServices et NodeServices ne sont plus renvoyés à l’enregistreur de console

<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> et <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> n’affichent pas les journaux de la console, sauf si la journalisation est configurée.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

`Microsoft.AspNetCore.SpaServices` et `Microsoft.AspNetCore.NodeServices` permettent de créer automatiquement un journal de console lorsque la journalisation n’est pas configurée. 

#### <a name="new-behavior"></a>Nouveau comportement

`Microsoft.AspNetCore.SpaServices` et `Microsoft.AspNetCore.NodeServices` n’affichent pas les journaux de la console, sauf si la journalisation est configurée.

#### <a name="reason-for-change"></a>Motif de modification

Il est nécessaire de s’aligner sur la manière dont les autres packages d’ASP.NET Core implémentent la journalisation.

#### <a name="recommended-action"></a>Action recommandée

Si l’ancien comportement est requis, pour configurer la journalisation de la console, ajoutez `services.AddLogging(builder => builder.AddConsole())` à votre méthode `Setup.ConfigureServices`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
