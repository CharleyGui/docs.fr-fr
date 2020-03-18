---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901689"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC : Outil de précomplification déprécié

Dans ASP.NET Core 1.1, `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` le paquet (outil de précomplation MVC) a été introduit pour ajouter de la prise en charge de la compilation en temps de publication des fichiers Razor (fichiers *.cshtml).* Dans ASP.NET Core 2.1, le [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) a été introduit pour étendre les fonctionnalités de l’outil de précomplation. Le Razor SDK a ajouté un support pour la compilation des fichiers Razor. Le SDK vérifie la justesse des fichiers *.cshtml* au moment de la construction tout en améliorant le temps de démarrage de l’application. Le Razor SDK est allumé par défaut, et aucun geste n’est nécessaire pour commencer à l’utiliser.

Dans ASP.NET Core 3.0, l’outil ASP.NET de précomplation MVC de l’ère Core 1.1 a été supprimé. Les versions plus tôt de paquet continueront à recevoir des corrections importantes de bogue et de sécurité dans la version de correction.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Le `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` paquet a été utilisé pour pré-compiler des vues de rasoir de MVC.

#### <a name="new-behavior"></a>Nouveau comportement

Le Razor SDK prend en charge cette fonctionnalité. Le `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` paquet n’est plus mis à jour.

#### <a name="reason-for-change"></a>Raison du changement

Le Razor SDK fournit plus de fonctionnalités et vérifie la justesse des fichiers *.cshtml* au moment de la construction. Le SDK améliore également le temps de démarrage de l’application.

#### <a name="recommended-action"></a>Action recommandée

Pour les utilisateurs de ASP.NET Core 2.1 ou plus tard, mettre à jour pour utiliser le support natif pour la précomplation dans le [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0). Si des bogues ou des fonctionnalités manquantes empêchent la migration vers le Razor SDK, ouvrez un problème à [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

### Affected APIs

Not detectable via API analysis

-->
