---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901703"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Localisation: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete

La [classe ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) et le membre de [l’interface WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) sont souvent `IStringLocalizer` des sources de confusion pour les utilisateurs de localisation, en particulier lors de la création de leur propre implémentation. Ces éléments donnent à l’utilisateur l’impression qu’une `IStringLocalizer` instance est « par langue, par ressource ». En réalité, les cas ne devraient être que des « ressources ». Le langage recherché est déterminé `CultureInfo.CurrentUICulture` par le moment de l’exécution. Pour éliminer la source de confusion, les API ont été marquées comme obsolètes dans ASP.NET Core 3.0 Aperçu 3. Les API seront supprimées dans une version future.

Pour le contexte, voir [dotnet/aspnetcore 3324](https://github.com/dotnet/aspnetcore/issues/3324). Pour discussion, voir [dotnet/aspnetcore 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Méthodes n’ont `Obsolete`pas été marqués comme .

#### <a name="new-behavior"></a>Nouveau comportement

Les méthodes `Obsolete`sont marquées .

#### <a name="reason-for-change"></a>Raison du changement

Les API représentaient un cas d’utilisation qui n’est pas recommandé. Il y avait confusion au sujet de la conception de la localisation.

#### <a name="recommended-action"></a>Action recommandée

La recommandation est `ResourceManagerStringLocalizer` d’utiliser à la place. Que la culture soit `CurrentCulture`définie par le . Si ce n’est pas une option, créez et utilisez une copie de [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

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
