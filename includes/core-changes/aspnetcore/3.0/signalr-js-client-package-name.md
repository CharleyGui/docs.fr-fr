---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901588"
---
### <a name="signalr-javascript-client-package-name-changed"></a>Signalr : nom du package client JavaScript modifié

Dans ASP.NET Core 3,0 Preview 7, le nom du package client JavaScript Signalr est `@aspnet/signalr` passé `@microsoft/signalr`de à. Le changement de nom reflète le fait que Signalr est utile dans les applications plus que simplement ASP.NET Core, grâce au service Azure Signalr.

Pour réagir à cette modification, modifiez les références dans vos fichiers *Package. JSON* , `require` les instructions et `import` les instructions ECMAScript. Aucune API ne changera dans le cadre de ce changement de nom.

Pour plus d’informations, consultez [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le package client a été `@aspnet/signalr`nommé.

#### <a name="new-behavior"></a>Nouveau comportement

Le package client est nommé `@microsoft/signalr`.

#### <a name="reason-for-change"></a>Motif de modification

Le changement de nom clarifie que Signalr est utile au-delà de ASP.NET Core applications, grâce au service Azure Signalr.

#### <a name="recommended-action"></a>Action recommandée

Basculez vers le nouveau `@microsoft/signalr`package.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
