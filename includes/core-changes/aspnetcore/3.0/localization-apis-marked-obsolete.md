---
ms.openlocfilehash: d70a8d2a3031a5b3d47ab3fb7f40193dce6e311e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032595"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Localisation : ResourceManagerWithCultureStringLocalizer et WithCulture marqués comme obsolètes

La classe [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) et le membre d’interface [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) sont souvent des sources de confusion pour les utilisateurs de localisation, en particulier lors de la création de leur propre `IStringLocalizer` implémentation. Ces éléments donnent à l’utilisateur l’impression qu’une `IStringLocalizer` instance est « par langue, par ressource ». En réalité, les instances doivent uniquement être « par ressource ». La langue recherchée est déterminée par le `CultureInfo.CurrentUICulture` au moment de l’exécution. Pour éliminer la source de confusion, les API ont été marquées comme obsolètes dans ASP.NET Core 3,0 Preview 3. Les API seront supprimées dans une version ultérieure.

Pour le contexte, consultez [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Pour plus d’informations, consultez [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les méthodes n’ont pas été marquées comme `Obsolete` .

#### <a name="new-behavior"></a>Nouveau comportement

Les méthodes sont marquées `Obsolete` .

#### <a name="reason-for-change"></a>Motif de modification

Les API représentaient un cas d’usage qui n’est pas recommandé. Il y a eu une confusion concernant la conception de la localisation.

#### <a name="recommended-action"></a>Action recommandée

Il est recommandé d’utiliser à la `ResourceManagerStringLocalizer` place. Laissez la culture définie par `CurrentCulture` . Si ce n’est pas une option, créez et utilisez une copie de [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.0)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.0)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
