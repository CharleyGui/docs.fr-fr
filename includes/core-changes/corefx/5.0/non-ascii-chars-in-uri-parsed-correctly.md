---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720188"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a>Les chemins d’accès URI avec des caractères non-ASCII sont analysés correctement sur UNIX

Un bogue a été corrigé dans la <xref:System.Uri?displayProperty=fullName> classe de telle sorte que les chemins d’accès d’URI absolus qui contiennent des caractères non-ASCII sont désormais correctement analysés sur les plateformes UNIX.

#### <a name="change-description"></a>Description de la modification

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

#### <a name="version-introduced"></a>Version introduite

5,0

#### <a name="recommended-action"></a>Action recommandée

Si vous avez du code qui attend et compte les segments de chemin d’accès dupliqués, vous pouvez supprimer ce code.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
