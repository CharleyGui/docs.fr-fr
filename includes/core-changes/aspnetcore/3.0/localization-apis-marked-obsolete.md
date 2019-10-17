---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394419"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Localisation : ResourceManagerWithCultureStringLocalizer et WithCulture marqués comme obsolètes

Les membres de la classe [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) et de l’interface [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) sont souvent des sources de confusion pour les utilisateurs de localisation, en particulier lors de la création de leur propre implémentation `IStringLocalizer`. Ces éléments donnent à l’utilisateur l’impression qu’une instance `IStringLocalizer` est « par langue, par ressource ». En réalité, les instances doivent uniquement être « par ressource ». La langue recherchée est déterminée par la `CultureInfo.CurrentUICulture` au moment de l’exécution. Pour éliminer la source de confusion, les API ont été marquées comme obsolètes dans ASP.NET Core 3,0 Preview 3. Les API seront supprimées dans une version ultérieure.

Pour le contexte, consultez [ASPNET/AspNetCore # 3324](https://github.com/aspnet/AspNetCore/issues/3324). Pour plus d’informations, consultez [ASPNET/AspNetCore # 7756](https://github.com/aspnet/AspNetCore/issues/7756).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Les méthodes n’ont pas été marquées comme `Obsolete`.

#### <a name="new-behavior"></a>Nouveau comportement

Les méthodes sont marquées `Obsolete`.

#### <a name="reason-for-change"></a>Motif de modification

Les API représentaient un cas d’usage qui n’est pas recommandé. Il y a eu une confusion concernant la conception de la localisation.

#### <a name="recommended-action"></a>Action recommandée

Il est recommandé d’utiliser à la place `ResourceManagerStringLocalizer`. Laissez la culture définie par le `CurrentCulture`. Si ce n’est pas une option, créez et utilisez une copie de [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
