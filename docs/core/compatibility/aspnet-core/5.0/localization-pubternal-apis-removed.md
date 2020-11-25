---
title: 'Modification avec rupture : API Pubternal supprimées'
description: En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 où certaines API de localisation pubternal ont été supprimées
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: ae647d66b716175536edb3c978b027ebb7d3ddac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760895"
---
# <a name="localization-pubternal-apis-removed"></a>Localisation : API « Pubternal » supprimées

Pour mieux gérer la surface de l’API publique de ASP.NET Core, certaines :::no-loc text="\"pubternal\""::: API de localisation ont été supprimées. Une :::no-loc text="\"pubternal\""::: API a un `public` modificateur d’accès et est définie dans un espace de noms qui implique une intention [interne](../../../../csharp/language-reference/keywords/internal.md) .

Pour plus d’informations, consultez [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).

## <a name="version-introduced"></a>Version introduite

5,0 Preview 6

## <a name="old-behavior"></a>Ancien comportement

Les API suivantes étaient `public` :

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` les surcharges de constructeur acceptant l’un des types de paramètres suivants :
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a>Nouveau comportement

La liste suivante présente les modifications :

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper` devient `Microsoft.Extensions.Localization.AssemblyWrapper` et est maintenant `internal` .
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` devient `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` et est maintenant `internal` .
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` les surcharges de constructeur acceptant l’un des types de paramètres suivants sont désormais `internal` :
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a>Motif de modification

Expliquée plus en détail dans [ASPNET/annonces # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: les types ont été supprimés de la surface de l' `public` API. Ces modifications adaptent plus de classes à cette décision de conception. Les classes en question étaient conçues comme des points d’extension pour les tests internes de l’équipe.

## <a name="recommended-action"></a>Action recommandée

Bien que cela soit peu probable, certaines applications peuvent intentionnellement ou accidentellement dépendre des :::no-loc text="\"pubternal\""::: types. Consultez les sections [nouveau comportement](#new-behavior) pour déterminer comment migrer à partir des types.

Si vous avez identifié un scénario pour lequel l’API publique est autorisée avant cette modification mais ne le fait pas maintenant, signalez un problème dans [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).

## <a name="affected-apis"></a>API affectées

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
