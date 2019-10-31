---
ms.openlocfilehash: 8344fdedcff34f102b73f977b688abc15563bd4c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198429"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Framework partagé : assemblys supprimés de Microsoft. AspNetCore. app

À partir de ASP.NET Core 3,0, l’infrastructure partagée ASP.NET Core (`Microsoft.AspNetCore.App`) contient uniquement les assemblys internes entièrement développés, pris en charge et pouvant être gérés par Microsoft.

#### <a name="change-description"></a>Modifier la description

Considérez la modification comme la redéfinition des limites pour le ASP.NET Core « plateforme ». L’infrastructure partagée sera [source-Buildable par quiconque via github](https://github.com/dotnet/source-build) et continuera à offrir les avantages existants des frameworks partagés .net core à vos applications. Certains avantages incluent une taille de déploiement plus petite, une mise à jour corrective centralisée et un temps de démarrage plus rapide.

Dans le cadre de la modification, certaines modifications importantes notables sont introduites dans `Microsoft.AspNetCore.App`.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Les projets font référence à `Microsoft.AspNetCore.App` via un élément `<PackageReference>` dans le fichier projet.

En outre, `Microsoft.AspNetCore.App` contenait les sous-composants suivants :

- Json.NET (`Newtonsoft.Json`)
- Entity Framework Core (assemblys précédés de `Microsoft.EntityFrameworkCore.`)
- Roslyn (`Microsoft.CodeAnalysis`)

#### <a name="new-behavior"></a>Nouveau comportement

Une référence à `Microsoft.AspNetCore.App` ne requiert plus un élément `<PackageReference>` dans le fichier projet. L’kit SDK .NET Core prend en charge un nouvel élément appelé `<FrameworkReference>`, qui remplace l’utilisation de `<PackageReference>`.

Pour plus d’informations, consultez [ASPNET/AspNetCore # 3612](https://github.com/aspnet/AspNetCore/issues/3612).

Entity Framework Core est fourni sous forme de packages NuGet. Cette modification aligne le modèle d’expédition avec toutes les autres bibliothèques d’accès aux données sur .NET. Il fournit Entity Framework Core le chemin le plus simple pour poursuivre l’innovation tout en prenant en charge les diverses plateformes .NET. Le déplacement de Entity Framework Core hors de l’infrastructure partagée n’a aucun impact sur son état en tant que bibliothèque Microsoft, prise en charge et gérée. La [stratégie de support .net Core](https://www.microsoft.com/net/platform/support-policy) continue à la couvrir.

Json.NET et Entity Framework Core continuent de fonctionner avec ASP.NET Core. Toutefois, ils ne sont pas inclus dans le Framework partagé.

Pour plus d’informations, consultez [l’avenir de JSON dans .net Core 3,0](https://github.com/dotnet/announcements/issues/90). Consultez également [la liste complète des binaires](https://github.com/aspnet/AspNetCore/issues/3755) supprimés de l’infrastructure partagée.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification simplifie la consommation de `Microsoft.AspNetCore.App` et réduit la duplication entre les packages NuGet et les frameworks partagés.

Pour plus d’informations sur la motivation de cette modification, consultez ce billet de [blog](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).

#### <a name="recommended-action"></a>Action recommandée

Il n’est pas nécessaire que les projets utilisent des assemblys dans `Microsoft.AspNetCore.App` en tant que packages NuGet. Pour simplifier le ciblage et l’utilisation de l’infrastructure partagée ASP.NET Core, de nombreux packages NuGet livrés depuis ASP.NET Core 1,0 ne sont plus produits. Les API fournies par ces packages sont toujours disponibles pour les applications en utilisant un `<FrameworkReference>` pour `Microsoft.AspNetCore.App`. Les exemples d’API courants incluent Kestrel, MVC et Razor.

Cette modification ne s’applique pas à tous les fichiers binaires référencés via `Microsoft.AspNetCore.App` dans ASP.NET Core 2. x. Les exceptions notables sont les suivantes :

- les bibliothèques `Microsoft.Extensions` qui continuent de cibler des .NET Standard seront disponibles en tant que packages NuGet (voir https://github.com/aspnet/Extensions).
- API produites par l’équipe ASP.NET Core qui ne font pas partie de `Microsoft.AspNetCore.App`. Par exemple, les composants suivants sont disponibles sous forme de packages NuGet :
  - Entity Framework Core
  - API fournissant une intégration tierce
  - Fonctionnalités expérimentales
  - Les API avec des dépendances qui n’ont pas pu [répondre aux conditions requises pour se trouver dans le Framework partagé](https://github.com/aspnet/AspNetCore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- Les extensions de MVC qui maintiennent la prise en charge de Json.NET. Une API sera fournie en tant que package NuGet pour prendre en charge l’utilisation de Json.NET et MVC.
- Le client .NET Signalr continue à prendre en charge .NET Standard et à être fourni en tant que package NuGet. Elle est destinée à être utilisée sur de nombreux runtimes .NET, tels que Xamarin et UWP.

Pour plus d’informations, consultez [arrêter la production de packages pour les assemblys de Framework partagé dans 3,0](https://github.com/aspnet/AspNetCore/issues/3756). Pour plus d’informations, consultez [ASPNET/AspNetCore # 3757](https://github.com/aspnet/AspNetCore/issues/3757).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
