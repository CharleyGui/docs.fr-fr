---
title: 'Modification avec rupture : éblouissant : les champs publics ReadOnly RenderTreeFrame sont devenus des propriétés'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée éblouissant : les champs publics ReadOnly RenderTreeFrame sont devenus des propriétés'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: e9da9c538cc0a8ed4f138ef64ece0c7d144f28d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760843"
---
# <a name="blazor-rendertreeframe-readonly-public-fields-have-become-properties"></a>Éblouissant : les champs publics ReadOnly RenderTreeFrame sont devenus des propriétés

Dans ASP.NET Core 3,0 et 3,1, la <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame> structure expose différents `readonly public` champs, notamment <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.FrameType> , <xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame.Sequence> et d’autres. Dans ASP.NET Core version 5,0 RC1 et les versions ultérieures, tous les `readonly public` champs sont modifiés en `readonly public` Propriétés.

Cette modification n’affecte pas de nombreux développeurs, car :

* Toute application ou bibliothèque qui utilise simplement des `.razor` fichiers (ou même des <xref:Microsoft.AspNetCore.Components.Rendering.RenderTreeBuilder> appels manuels) pour définir ses composants ne référence pas directement ce type.
* Le `RenderTreeFrame` type lui-même est considéré comme un détail d’implémentation, non destiné à être utilisé en dehors de l’infrastructure. ASP.NET Core 3,0 et versions ultérieures incluent un analyseur qui émet des avertissements du compilateur si le type est utilisé directement.
* Même si vous référencez `RenderTreeFrame` directement, cette modification est une rupture binaire, mais pas une rupture de source. Autrement dit, votre code source existant se compilera et se comportera correctement. Vous ne rencontrerez un problème que si vous compilez par rapport à un Framework .NET Core 3. x et que vous exécutez ensuite ces fichiers binaires sur .NET 5,0 RC1 et Framework ultérieur.

Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25727](https://github.com/dotnet/aspnetcore/issues/25727).

## <a name="version-introduced"></a>Version introduite

5,0 RC1

## <a name="old-behavior"></a>Ancien comportement

Les membres publics sur `RenderTreeFrame` sont définis en tant que champs. Par exemple : `renderTreeFrame.Sequence` et `renderTreeFrame.ElementName`.

## <a name="new-behavior"></a>Nouveau comportement

Les membres publics sur `RenderTreeFrame` sont définis en tant que propriétés portant le même nom qu’avant. Par exemple : `renderTreeFrame.Sequence` et `renderTreeFrame.ElementName`.

Si un code précompilé ancien n’a pas été recompilé depuis cette modification, il peut lever une exception similaire à *MissingFieldException : champ introuvable : « Microsoft. AspNetCore. Components. RenderTree. RenderTreeFrame. Frame »*.

## <a name="reason-for-change"></a>Motif de modification

Cette modification était nécessaire pour implémenter des améliorations de performances à fort impact dans le rendu des composants éblouissants dans ASP.NET Core 5,0. Les mêmes niveaux de sécurité et d’encapsulation sont conservés.

## <a name="recommended-action"></a>Action recommandée

La plupart des développeurs éblouissants ne sont pas affectés par cette modification. La modification est plus susceptible d’affecter les auteurs de bibliothèque et de package, mais uniquement dans de rares cas. Plus précisément, si vous développez :

* Une application et l’utilisation de ASP.NET Core 3. x ou la mise à niveau vers 5,0 RC1 ou version ultérieure, vous n’avez pas besoin de modifier votre propre code. Toutefois, si vous dépendez d’une bibliothèque mise à niveau pour tenir compte de cette modification, vous devez effectuer une mise à jour vers une version plus récente de cette bibliothèque.
* Une bibliothèque et souhaitez prendre en charge uniquement ASP.NET Core 5,0 RC1 ou une version ultérieure, aucune action n’est nécessaire. Assurez-vous simplement que votre fichier projet déclare une `<TargetFramework>` valeur `net5.0` ou une version ultérieure.
* Une bibliothèque et souhaitez prendre en charge les ASP.NET Core 3. x *et* 5,0, déterminez si votre code lit les `RenderTreeFrame` membres. Par exemple, l’évaluation de `someRenderTreeFrame.FrameType` .
  * La plupart des bibliothèques ne lisent pas `RenderTreeFrame` les membres, y compris les bibliothèques qui contiennent des `.razor` composants. Dans ce cas, aucune action n’est nécessaire.
  * Toutefois, si votre bibliothèque le fait, vous devez disposer de plusieurs cibles pour prendre en charge `netstandard2.1` et `net5.0` . Appliquez les modifications suivantes dans votre fichier projet :
    * Remplacez l' `<TargetFramework>` élément existant par `<TargetFrameworks>netstandard2.0;net5.0</TargetFrameworks>` .
    * Utilisez une `Microsoft.AspNetCore.Components` référence de package conditionnel pour prendre en compte les deux versions que vous souhaitez prendre en charge. Par exemple :

        ```xml
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="3.0.0" Condition="'$(TargetFramework)' == 'netstandard2.0'" />
        <PackageReference Include="Microsoft.AspNetCore.Components" Version="5.0.0-rc.1.*" Condition="'$(TargetFramework)' != 'netstandard2.0'" />
        ```

Pour plus d’informations, consultez ce [diff illustrant la façon dont @jsakamoto la `Toolbelt.Blazor.HeadElement` bibliothèque a déjà été mise à niveau](https://github.com/jsakamoto/Toolbelt.Blazor.HeadElement/commit/090df430ba725f9420d412753db8104e8c32bf51).

## <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.Components.RenderTree.RenderTreeFrame`

-->
