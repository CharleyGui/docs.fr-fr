---
ms.openlocfilehash: acef6d7177ee5ad7e18dc8ba1e383d6f76263623
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394445"
---
### <a name="signalr-javascript-client-package-name-changed"></a>Signalr : nom du package client JavaScript modifié

Dans ASP.NET Core 3,0 Preview 7, le nom du package client JavaScript Signalr est passé de `@aspnet/signalr` à `@microsoft/signalr`. Le changement de nom reflète le fait que Signalr est utile dans les applications plus que simplement ASP.NET Core, grâce au service Azure Signalr.

Pour réagir à cette modification, modifiez les références dans vos fichiers *Package. JSON* , `require` et les instructions ECMAScript `import`. Aucune API ne changera dans le cadre de ce changement de nom.

Pour plus d’informations, consultez [ASPNET/AspNetCore # 11637](https://github.com/aspnet/AspNetCore/issues/11637).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Le package client a été nommé `@aspnet/signalr`.

#### <a name="new-behavior"></a>Nouveau comportement

Le package client est nommé `@microsoft/signalr`.

#### <a name="reason-for-change"></a>Motif de modification

Le changement de nom clarifie que Signalr est utile au-delà de ASP.NET Core applications, grâce au service Azure Signalr.

#### <a name="recommended-action"></a>Action recommandée

Basculez vers le nouveau package `@microsoft/signalr`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
