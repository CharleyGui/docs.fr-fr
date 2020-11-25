---
title: 'Modification avec rupture : les chemins d’accès URI avec des caractères non-ASCII sont analysés correctement sur UNIX'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où les chemins d’accès URI absolus contenant des caractères non-ASCII sont désormais correctement analysés sur les plateformes UNIX.
ms.date: 11/01/2020
ms.openlocfilehash: 94de4e0eb94a11153d873871d4003422a4286a0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760864"
---
# <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a>Les chemins d’accès URI avec des caractères non-ASCII sont analysés correctement sur UNIX

Un bogue a été corrigé dans la <xref:System.Uri?displayProperty=fullName> classe de telle sorte que les chemins d’accès d’URI absolus qui contiennent des caractères non-ASCII sont désormais correctement analysés sur les plateformes UNIX.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, les chemins d’URI absolus qui contiennent des caractères non-ASCII ne sont pas correctement analysés sur les plateformes UNIX et les segments du chemin d’accès sont dupliqués. (Les chemins d’accès absolus sont ceux qui commencent par « / ».) Le problème d’analyse a été résolu pour .NET 5,0. Si vous passez d’une version antérieure de .NET à .NET 5,0 ou version ultérieure, vous obtiendrez des valeurs différentes produites par <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> , <xref:System.Uri.ToString?displayProperty=nameWithType> et d’autres <xref:System.Uri> membres.

Prenez en compte la sortie du code suivant lorsqu’il est exécuté sur UNIX.

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

Sortie sur la version précédente de .NET :

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

Sortie sur .NET 5,0 ou version ultérieure :

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Si vous avez du code qui attend et compte les segments de chemin d’accès dupliqués, vous pouvez supprimer ce code.

## <a name="affected-apis"></a>API affectées

- <xref:System.Uri?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
