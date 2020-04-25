---
title: Structure des programmes C# - Visite guidée du langage C#
description: Découvrez les composantes élémentaires d’un programme C#
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c0a4dcaed7b53a7da7008d6000b3bec2ffe3ee7b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141010"
---
# <a name="program-structure"></a>Structure du programme

Les concepts clés d’organisation en C# sont les ***programmes***, ***espaces de noms***, ***types***, ***membres*** et ***assemblys***. Les programmes C++, comme les programmes C, se composent d'un ou plusieurs fichiers sources. Les programmes déclarent des types qui contiennent des membres et peuvent être organisés en espaces de noms. Les classes et les interfaces sont des exemples de types. Les champs, méthodes, propriétés et événements sont des exemples de membres. Lorsque les programmes C# sont compilés, ils sont empaquetés physiquement dans des assemblys. Les assemblys ont généralement l’extension de fichier `.exe` ou `.dll`, selon qu’elles implémentent des ***applications*** ou des ***bibliothèques***, respectivement.

Vous pouvez créer un projet de bibliothèque nommé *Acme* à `dotnet new` l’aide de la commande :

```dotnetcli
dotnet new classlib -o acme
```

Dans ce projet, déclarez une classe `Stack` nommée dans un espace `Acme.Collections`de noms appelé :

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

Le nom qualifié complet de cette classe est `Acme.Collections.Stack`. La classe contient plusieurs membres : un champ nommé `top`, deux méthodes nommées `Push` et `Pop`, et une classe imbriquée nommée `Entry`. La classe `Entry` contient trois membres en plus : un champ nommé `next`, un autre nommé `data` et un constructeur. Commande :

```dotnetcli
dotnet build
```

compile l’exemple en tant que bibliothèque (code sans point d’entrée `Main`) et produit un assembly nommé `acme.dll`.

Les assemblys contiennent le code exécutable sous forme d’instructions de langage intermédiaire (IL) et des informations symboliques sous la forme de métadonnées. Avant son exécution, le compilateur juste-à-temps (JIT) du Common Language Runtime .NET convertit le code IL dans un assembly en code spécifique au processeur.

Étant donné qu’un assembly est une unité autodescriptive de fonctionnalité contenant à la fois du code et des métadonnées, il n’est pas nécessaire d’utiliser des `#include` directives et des fichiers d’en-tête en C#. Les membres et types publics contenus dans un assembly particulier sont disponibles dans un programme C# par simple référence à cet assembly lors de la compilation du programme. Par exemple, ce programme utilise la classe `Acme.Collections.Stack` à partir de l’assembly `acme.dll` :

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Le fichier *csproj* pour le projet précédent du programme doit inclure un nœud de référence pour que le compilateur C# résolve les références aux classes `acme.dll` de l’assembly :

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

Après cet ajout, `dotnet build` crée un assembly exécutable nommé `example.exe`, qui, lorsqu’il est exécuté, produit la sortie :

```dotnetcli
100
10
1
```

C# permet le stockage du texte source d’un programme dans plusieurs fichiers source. Lorsqu’un programme C# multifichier est compilé, tous les fichiers source sont traités ensemble et les fichiers source peuvent librement se référencer mutuellement. Sur le plan conceptuel, c’est comme si tous les fichiers source étaient concaténés en un seul fichier volumineux avant d’être traités. Les déclarations anticipées ne sont jamais nécessaires en C#, car, à quelques exceptions près, l’ordre de déclaration n’est pas significatif. C# ne limite pas un fichier source à la déclaration d’un seul type public et ne nécessite pas non plus que le nom du fichier source corresponde à un type déclaré dans ce fichier.

>[!div class="step-by-step"]
>[Précédent](index.md)
>[suivant](types-and-variables.md)
