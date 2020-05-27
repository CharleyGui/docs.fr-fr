---
ms.openlocfilehash: 6deeb7debce9b731f3871b7de0ad8df8a8cdafea
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728285"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a>Localisation : classe ResourceManagerWithCultureStringLocalizer et membre d’interface WithCulture supprimé

La classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) et la méthode [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) ont été supprimées dans .net 5,0 Preview 1.

Pour le contexte, consultez [ASPNET/announcements # 346](https://github.com/aspnet/Announcements/issues/346) et [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Pour plus d’informations sur cette modification, consultez [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 1

#### <a name="old-behavior"></a>Ancien comportement

La `ResourceManagerWithCultureStringLocalizer` classe et la `ResourceManagerStringLocalizer.WithCulture` méthode sont [obsolètes dans .net Core 3,0 Preview 3 et versions ultérieures](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).

#### <a name="new-behavior"></a>Nouveau comportement

La `ResourceManagerWithCultureStringLocalizer` classe et la `ResourceManagerStringLocalizer.WithCulture` méthode ont été supprimées dans .net 5,0 Preview 1. Pour obtenir un inventaire des modifications apportées, consultez la demande de tirage (pull request) à l’adresse [dotnet/extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files).

#### <a name="reason-for-change"></a>Motif de modification

La classe [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) et la méthode [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) étaient souvent des sources de confusion pour les utilisateurs de la localisation. La confusion était particulièrement élevée lors de la création d’une <xref:Microsoft.Extensions.Localization.IStringLocalizer> implémentation personnalisée. Cette classe et cette méthode donnent aux consommateurs l’impression qu’une `IStringLocalizer` instance est supposée être « par langue, par ressource ». En réalité, l’instance doit uniquement être « par ressource ». Au moment de l’exécution, la <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> propriété détermine la langue à utiliser.

#### <a name="recommended-action"></a>Action recommandée

Arrêtez l’utilisation de la `ResourceManagerWithCultureStringLocalizer` classe et de la `ResourceManagerStringLocalizer.WithCulture` méthode.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
