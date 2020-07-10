---
ms.openlocfilehash: ca369c4e3f78648c6e8e0bcb5d54711d3009a769
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174259"
---
### <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a>Éblouissante : espace blanc non significatif tronqué des composants au moment de la compilation

À compter de ASP.NET Core 5,0 Preview 7, le compilateur Razor omet les espaces blancs non significatifs dans les composants éblouissants (fichiers *. Razor* ) au moment de la compilation. Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 7

#### <a name="old-behavior"></a>Ancien comportement

Dans les versions 3. x du serveur éblouissant et du webassembly éblouissant, l’espace blanc est respecté dans le code source d’un composant. Les nœuds de texte avec espaces blancs sont rendus dans le Document Object Model du navigateur (DOM), même s’il n’y a aucun effet visuel.

Considérez le code du composant éblouissant suivant :

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

L’exemple précédent restitue deux nœuds d’espace blanc :

* En dehors du `@foreach` bloc de code.
* Autour de l' `<li>` élément.
* Autour de la `@item.Text` sortie.

Une liste contenant 100 éléments génère des nœuds 402 espaces blancs. Il s’agit de la moitié de tous les nœuds rendus, même si aucun des nœuds d’espace blanc n’affecte visuellement la sortie rendue.

Lors du rendu de code HTML statique pour les composants, les espaces à l’intérieur d’une balise n’ont pas été conservés. Par exemple, affichez la source du composant suivant :

```razor
<foo        bar="baz"     />
```

Les espaces blancs ne sont pas conservés. La sortie prérendue est la suivante :

```razor
<foo bar="baz" />
```

#### <a name="new-behavior"></a>Nouveau comportement

Sauf `@preservewhitespace` si la directive est utilisée avec la valeur `true` , les nœuds d’espace blanc sont supprimés s’ils :

* Sont de début ou de fin dans un élément.
* Sont de début ou de fin dans un `RenderFragment` paramètre. Par exemple, le contenu enfant est passé à un autre composant.
* Précédez ou suivez un bloc de code C# tel que `@if` et `@foreach` .

#### <a name="reason-for-change"></a>Motif de modification

L’objectif de éblouissant dans ASP.NET Core 5,0 est d’améliorer les performances de rendu et de comparaison. Les nœuds d’arbre d’espace blanc non significatifs consommaient jusqu’à 40% du temps de rendu dans les tests d’évaluation.

#### <a name="recommended-action"></a>Action recommandée

Dans la plupart des cas, la disposition visuelle du composant rendu n’est pas affectée. Toutefois, la suppression de l’espace blanc peut affecter la sortie rendue lors de l’utilisation d’une règle CSS telle que `white-space: pre` . Pour désactiver cette optimisation des performances et conserver l’espace blanc, effectuez l’une des actions suivantes :

* Ajoutez la `@preservewhitespace true` directive en haut du fichier *. Razor* pour appliquer la préférence à un composant spécifique.
* Ajoutez la `@preservewhitespace true` directive à l’intérieur d’un fichier *_Imports. Razor* pour appliquer la préférence à un sous-répertoire ou à l’ensemble du projet.

Dans la plupart des cas, aucune action n’est requise, car les applications continuent de se comporter normalement (mais plus rapidement). Si la suppression des espaces blancs provoque des problèmes pour un composant particulier, utilisez `@preservewhitespace true` dans ce composant pour désactiver cette optimisation.

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!--

#### Affected APIs

Not detectable via API analysis

-->
