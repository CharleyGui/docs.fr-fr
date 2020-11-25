---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031999"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a>Les propriétés UriBuilder n’ajoutent plus de caractères de début

<xref:System.UriBuilder.Fragment?displayProperty=nameWithType> n’ajoute plus de caractère de début `#` et <xref:System.UriBuilder.Query?displayProperty=nameWithType> n’ajoute plus de `?` caractère de début lorsqu’il est déjà présent.

#### <a name="change-description"></a>Description de la modification

Dans .NET Framework, les <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> Propriétés et ajoutent <xref:System.UriBuilder.Query?displayProperty=nameWithType> toujours `#` un `?` caractère ou, respectivement, à la valeur stockée. Ce comportement peut entraîner `#` `?` la valeur stockée sur plusieurs ou caractères si la chaîne contient déjà l’un de ces caractères de début. Par exemple, la valeur de <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> peut devenir `##main` .

À compter de .NET Core 1,0, ces propriétés n’ajouteront plus les `#` `?` caractères ou à la valeur stockée si celle-ci est déjà présente au début de la chaîne.

#### <a name="version-introduced"></a>Version introduite

1.0

#### <a name="recommended-action"></a>Action recommandée

Vous n’avez plus besoin de supprimer explicitement ces caractères de début lors de la définition des valeurs de propriété. Cela s’avère particulièrement utile lorsque vous ajoutez des valeurs, car vous n’avez plus besoin de supprimer le de début `#` ou `?` chaque fois que vous ajoutez.

Par exemple, l’extrait de code suivant montre la différence de comportement entre .NET Framework et .NET Core.

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- Dans .NET Framework, la sortie est `????one=1&two=2&three=3&four=4` .
- Dans .NET Core, la sortie est `?one=1&two=2&three=3&four=4` .

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
