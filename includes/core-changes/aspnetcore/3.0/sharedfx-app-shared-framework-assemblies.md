---
ms.openlocfilehash: a8146db1fb54d63d4716b879ce793f7d817cef59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937287"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Cadre partagé : Assemblées supprimées de Microsoft.AspNetCore.App

À partir de ASP.NET Core 3.0, le cadre partagé`Microsoft.AspNetCore.App`ASP.NET Core () ne contient que des assemblages de premier parti qui sont entièrement développés, pris en charge et utilisables par Microsoft.

#### <a name="change-description"></a>Description de la modification

Considérez le changement comme la redéfinition des limites pour la ASP.NET «plateforme» de base. Le cadre partagé sera [source-buildable par n’importe qui via GitHub](https://github.com/dotnet/source-build) et continuera d’offrir les avantages existants de .NET Core cadres partagés à vos applications. Certains avantages comprennent une plus petite taille de déploiement, un patching centralisé et un temps de démarrage plus rapide.

Dans le cadre du changement, certains `Microsoft.AspNetCore.App`changements de rupture notables sont introduits dans .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Projets `Microsoft.AspNetCore.App` référencés par un `<PackageReference>` élément du dossier du projet.

En `Microsoft.AspNetCore.App` outre, contenait les sous-compactes suivantes :

- Json.NET (`Newtonsoft.Json`)
- Entity Framework Core (assemblages `Microsoft.EntityFrameworkCore.`préfixés avec )
- Roslyn`Microsoft.CodeAnalysis`( )

#### <a name="new-behavior"></a>Nouveau comportement

Une référence `Microsoft.AspNetCore.App` à ne `<PackageReference>` plus nécessite un élément dans le dossier du projet. Le .NET Core SDK prend `<FrameworkReference>`en charge un `<PackageReference>`nouvel élément appelé , qui remplace l’utilisation de .

Pour plus d’informations, voir [dotnet/aspnetcore 3612](https://github.com/dotnet/aspnetcore/issues/3612).

Entity Framework Core navires comme paquets NuGet. Cette modification aligne le modèle d’expédition avec toutes les autres bibliothèques d’accès aux données sur .NET. Il fournit Entity Framework Core la voie la plus simple pour continuer à innover tout en soutenant les différentes plates-formes .NET. Le transfert de Entity Framework Core hors du cadre partagé n’a aucun impact sur son statut de bibliothèque développée, soutenue et utilisable par Microsoft. La [politique de soutien de base .NET](https://www.microsoft.com/net/platform/support-policy) continue de la couvrir.

Json.NET et le noyau cadre d’entité continuent de travailler avec ASP.NET Core. Ils ne seront toutefois pas inclus dans le cadre commun.

Pour plus d’informations, voir [L’avenir de JSON dans .NET Core 3.0](https://github.com/dotnet/announcements/issues/90). Voir également [la liste complète des binaires retirés](https://github.com/dotnet/aspnetcore/issues/3755) du cadre partagé.

#### <a name="reason-for-change"></a>Raison du changement

Ce changement simplifie `Microsoft.AspNetCore.App` la consommation et réduit les chevauchements entre les paquets NuGet et les cadres partagés.

Pour plus d’informations sur la motivation de ce changement, voir [ce blog](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="recommended-action"></a>Action recommandée

Il ne sera pas nécessaire pour les `Microsoft.AspNetCore.App` projets de consommer des assemblages en tant que paquets NuGet. Pour simplifier le ciblage et l’utilisation du cadre partagé ASP.NET Core, de nombreux paquets NuGet expédiés depuis ASP.NET Core 1.0 ne sont plus produits. Les API que ces paquets fournissent `<FrameworkReference>` sont `Microsoft.AspNetCore.App`toujours disponibles pour les applications en utilisant un à . Kestrel, MVC et Razor sont des exemples courants d’API.

Ce changement ne s’applique pas à `Microsoft.AspNetCore.App` tous les binaires référencés via dans ASP.NET Core 2.x. Les exceptions notables comprennent :

- `Microsoft.Extensions`bibliothèques qui continuent à cibler .NET Standard sera https://github.com/dotnet/extensions)disponible sous forme de forfaits NuGet (voir .
- API produite par l’équipe ASP.NET Core qui `Microsoft.AspNetCore.App`ne font pas partie de . Par exemple, les composants suivants sont disponibles sous forme de forfaits NuGet :
  - Entity Framework Core
  - API qui assurent l’intégration de tiers
  - Fonctionnalités expérimentales
  - API avec des dépendances qui ne pouvaient pas [répondre aux exigences d’être dans le cadre partagé](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- Extensions à MVC qui maintiennent le soutien pour Json.NET. Une API sera fournie sous forme de forfait NuGet à prendre en charge à l’aide de Json.NET et de MVC.
- Le client SignalR .NET continuera à prendre en charge .NET Standard et à expédier sous forme de forfait NuGet. Il est destiné à une utilisation sur de nombreux runtimes .NET, tels que Xamarin et UWP.

Pour plus d’informations, voir [Arrêtez de produire des paquets pour les assemblages-cadres partagés en 3.0](https://github.com/dotnet/aspnetcore/issues/3756). Pour discussion, voir [dotnet/aspnetcore 3757](https://github.com/dotnet/aspnetcore/issues/3757).

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
