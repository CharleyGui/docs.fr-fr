---
ms.openlocfilehash: 641233df165a1c2208a2185f2b6e99077f9a59d3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394225"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC : outil de précompilation déconseillé

Dans ASP.NET Core 1,1, le package `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (outil de précompilation MVC) a été introduit pour ajouter la prise en charge de la compilation au moment de la publication des fichiers Razor (fichiers *. cshtml* ). Dans ASP.NET Core 2,1, le [Kit de développement logiciel (SDK) Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) a été introduit pour s’étendre sur les fonctionnalités de l’outil de précompilation. Le kit de développement logiciel (SDK) Razor a ajouté la prise en charge de la compilation et de la publication des fichiers Razor. Le kit de développement logiciel (SDK) vérifie l’exactitude des fichiers *. cshtml* au moment de la génération, tout en améliorant le temps de démarrage de l’application. Le kit de développement logiciel (SDK) Razor est activé par défaut et aucun geste n’est nécessaire pour commencer à l’utiliser.

Dans ASP.NET Core 3,0, l’outil de précompilation MVC ASP.NET Core 1,1-Era a été supprimé. Les versions antérieures du package continueront de recevoir des correctifs de sécurité et bogues importants dans la version corrective. 

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Le package `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` a été utilisé pour précompiler les vues Razor MVC.

#### <a name="new-behavior"></a>Nouveau comportement

Le kit de développement logiciel (SDK) Razor prend en charge cette fonctionnalité en mode natif. Le package `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` n’est plus mis à jour.

#### <a name="reason-for-change"></a>Motif de modification

Le kit de développement logiciel (SDK) Razor offre plus de fonctionnalités et vérifie l’exactitude des fichiers *. cshtml* au moment de la génération. Le SDK améliore également le temps de démarrage de l’application.

#### <a name="recommended-action"></a>Action recommandée

Pour les utilisateurs de ASP.NET Core 2,1 ou version ultérieure, mettez à jour pour utiliser la prise en charge native pour la précompilation dans le [Kit de développement logiciel (SDK) Razor](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0). Si des bogues ou des fonctionnalités manquantes empêchent la migration vers le kit de développement logiciel (SDK) Razor, ouvrez un problème dans [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

### Affected APIs

Not detectable via API analysis

-->
