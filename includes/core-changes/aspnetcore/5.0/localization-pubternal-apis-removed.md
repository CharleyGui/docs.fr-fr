---
ms.openlocfilehash: 62a5f56bb7fffc453623a2c3202f288a19110158
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539468"
---
### <a name="localization-pubternal-apis-removed"></a>Localisation : API « Pubternal » supprimées

Pour mieux gérer la surface de l’API publique de ASP.NET Core, certaines :::no-loc text="\"pubternal\""::: API de localisation ont été supprimées. Une :::no-loc text="\"pubternal\""::: API a un `public` modificateur d’accès et est définie dans un espace de noms qui implique une intention [interne](../../../../docs/csharp/language-reference/keywords/internal.md) .

Pour plus d’informations, consultez [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 6

#### <a name="old-behavior"></a>Ancien comportement

Les API suivantes étaient `public` :

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` les surcharges de constructeur acceptant l’un des types de paramètres suivants :
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a>Nouveau comportement

La liste suivante présente les modifications :

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper` devient `Microsoft.Extensions.Localization.AssemblyWrapper` et est maintenant `internal` .
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` devient `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` et est maintenant `internal` .
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` les surcharges de constructeur acceptant l’un des types de paramètres suivants sont désormais `internal` :
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a>Motif de modification

Expliquée plus en détail dans [ASPNET/annonces # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: les types ont été supprimés de la surface de l' `public` API. Ces modifications adaptent plus de classes à cette décision de conception. Les classes en question étaient conçues comme des points d’extension pour les tests internes de l’équipe.

#### <a name="recommended-action"></a>Action recommandée

Bien que cela soit peu probable, certaines applications peuvent intentionnellement ou accidentellement dépendre des :::no-loc text="\"pubternal\""::: types. Consultez les sections [nouveau comportement](#new-behavior) pour déterminer comment migrer à partir des types.

Si vous avez identifié un scénario pour lequel l’API publique est autorisée avant cette modification mais ne le fait pas maintenant, signalez un problème dans [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
