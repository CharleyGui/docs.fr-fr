---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901703"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Localisation : ResourceManagerWithCultureStringLocalizer et WithCulture marqués comme obsolètes

La classe [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) et le membre d’interface [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) sont souvent des sources de confusion pour les utilisateurs de localisation, en particulier lors de la création de leur propre implémentation de `IStringLocalizer`. Ces éléments donnent à l’utilisateur l’impression qu’une `IStringLocalizer` instance est « par langue, par ressource ». En réalité, les instances doivent uniquement être « par ressource ». La langue recherchée est déterminée par la `CultureInfo.CurrentUICulture` au moment de l’exécution. Pour éliminer la source de confusion, les API ont été marquées comme obsolètes dans ASP.NET Core 3,0 Preview 3. Les API seront supprimées dans une version ultérieure.

Pour le contexte, consultez [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Pour plus d’informations, consultez [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les méthodes n’ont pas été marquées comme `Obsolete`.

#### <a name="new-behavior"></a>Nouveau comportement

Les méthodes sont marquées `Obsolete`.

#### <a name="reason-for-change"></a>Motif de modification

Les API représentaient un cas d’usage qui n’est pas recommandé. Il y a eu une confusion concernant la conception de la localisation.

#### <a name="recommended-action"></a>Action recommandée

La recommandation consiste à utiliser `ResourceManagerStringLocalizer` à la place. Laissez la culture définie par l' `CurrentCulture`. Si ce n’est pas une option, créez et utilisez une copie de [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
