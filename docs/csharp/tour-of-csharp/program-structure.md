---
title: Structure des programmes C# - Visite guidée du langage C#
description: Découvrez les composantes élémentaires d’un programme C#
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 5e095e71549ed3eec6c73e6a134fdb5a64fb63c0
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884382"
---
# <a name="program-structure"></a>Structure du programme

Les concepts clés d’organisation en C# sont les ***programmes***, ***espaces de noms***, ***types***, ***membres*** et ***assemblys***. Les programmes C++, comme les programmes C, se composent d'un ou plusieurs fichiers sources. Les programmes déclarent des types qui contiennent des membres et peuvent être organisés en espaces de noms. Les classes et les interfaces sont des exemples de types. Les champs, méthodes, propriétés et événements sont des exemples de membres. Lorsque les programmes C# sont compilés, ils sont physiquement empaquetés dans des assemblys. Les assemblys ont généralement l’extension de fichier `.exe` ou `.dll`, selon qu’elles implémentent des ***applications*** ou des ***bibliothèques***, respectivement.

L’exemple déclare une classe nommée `Stack` dans un espace de noms appelé `Acme.Collections` :

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Le nom qualifié complet de cette classe est `Acme.Collections.Stack`. La classe contient plusieurs membres : un champ nommé `top`, deux méthodes nommées `Push` et `Pop`, et une classe imbriquée nommée `Entry`. La classe `Entry` contient trois membres en plus : un champ nommé `next`, un autre nommé `data` et un constructeur. En supposant que le code source de l’exemple est stocké dans le fichier `acme.cs`, la ligne de commande

```console
csc /t:library acme.cs
```

compile l’exemple en tant que bibliothèque (code sans point d’entrée `Main`) et produit un assembly nommé `acme.dll`.

> [!IMPORTANT]
> Les exemples ci-dessus utilisent `csc` en tant que compilateur de ligne de commande C#. Ce compilateur est un exécutable Windows. Pour utiliser C# sur d’autres plateformes, vous devez utiliser les outils pour .NET Core. L’écosystème .NET Core utilise l’interface graphique `dotnet` pour gérer les versions en ligne de commande. Cela inclut la gestion des dépendances et l’appel du compilateur C#. Consultez [ce didacticiel](../../core/tutorials/cli-create-console-app.md) pour obtenir une description complète de ces outils sur les plateformes prises en charge par .NET Core.

Les assemblys contiennent le code exécutable sous forme d’instructions de langage intermédiaire (IL) et des informations symboliques sous la forme de métadonnées. Avant son exécution, le code de langage intermédiaire dans un assembly est automatiquement converti en code spécifique au processeur par le compilateur juste à temps (JIT) du Common Language Runtime .NET.

Comme un assembly est une unité de fonctionnalité autodescriptive contenant du code et des métadonnées, les directives `#include` et les fichiers d’en-tête ne sont pas nécessaires en C#. Les membres et types publics contenus dans un assembly particulier sont disponibles dans un programme C# par simple référence à cet assembly lors de la compilation du programme. Par exemple, ce programme utilise la classe `Acme.Collections.Stack` à partir de l’assembly `acme.dll` :

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Si le programme est stocké dans le fichier `example.cs`, lorsque `example.cs` est compilé, l’assembly acme.dll peut être référencé à l’aide de l’option de compilateur /r :

```console
csc /r:acme.dll example.cs
```

Cela permet de créer un assembly exécutable nommé `example.exe`, qui, lors de l’exécution, produit la sortie :

```console
100
10
1
```

C# permet le stockage du texte source d’un programme dans plusieurs fichiers source. Lorsqu’un programme C# multifichier est compilé, tous les fichiers source sont traités ensemble et les fichiers source peuvent librement se référencer mutuellement. Sur le plan conceptuel, c’est comme si tous les fichiers source étaient concaténés en un seul fichier volumineux avant d’être traités. Déclarations anticipées ne sont jamais nécessaires en C#, car, à de très rares exceptions près, l’ordre de déclaration n’a pas d’importance. C# ne limite pas un fichier source à la déclaration d’un seul type public et ne nécessite pas non plus que le nom du fichier source corresponde à un type déclaré dans ce fichier.

>[!div class="step-by-step"]
>[Précédent](index.md)
>[Suivant](types-and-variables.md)
