---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901588"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR: Le nom du forfait client JavaScript modifié

Dans ASP.NET Core 3.0 Preview 7, le nom du `@aspnet/signalr` client `@microsoft/signalr`SignalR JavaScript est passé de . Le changement de nom reflète le fait que SignalR est utile dans plus de ASP.NET applications Core, grâce au service SignalR Azure.

Pour réagir à ce changement, modifiez les `require` références dans *vos* fichiers, relevés et instructions ECMAScript. `import` Aucune API ne changera dans le cadre de ce changement.

Pour discussion, voir [dotnet/aspnetcore 11637](https://github.com/dotnet/aspnetcore/issues/11637).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le paquet client `@aspnet/signalr`a été nommé .

#### <a name="new-behavior"></a>Nouveau comportement

Le forfait client `@microsoft/signalr`est nommé .

#### <a name="reason-for-change"></a>Raison du changement

Le changement de nom précise que SignalR est utile au-delà de ASP.NET applications Core, grâce au service SignalR Azure.

#### <a name="recommended-action"></a>Action recommandée

Passez au nouveau `@microsoft/signalr`paquet .

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
