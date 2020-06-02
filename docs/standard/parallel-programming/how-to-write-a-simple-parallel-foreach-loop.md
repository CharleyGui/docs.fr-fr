---
title: Écrire un programme parallèle simple à l’aide de Parallel.ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 717a04790de27c5ae2aade44d29e4e9ff3fd93cc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290718"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Comment : écrire une boucle Parallel. ForEach simple

Cet exemple montre comment utiliser une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pour activer le parallélisme des données sur n’importe quelle source de données <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.

> [!NOTE]
> Cette documentation utilise des expressions lambda pour définir les délégués en PLINQ. Si vous n’êtes pas familiarisé avec les expressions lambda en C# ou Visual Basic, consultez [expressions lambda en PLINQ et tpl](lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Exemple

Cet exemple part du principe que vous disposez de plusieurs fichiers .jpg dans un dossier *C:\Users\Public\Pictures\Sample Pictures*, et crée un sous-dossier nommé *Modified* (Modifié). Lorsque vous exécutez l’exemple, il fait pivoter chaque image .jpg dans *Sample Pictures* (Exemples d’images) et les enregistre dans le sous-dossier *Modified*. Vous pouvez modifier les deux chemins d’accès en fonction des besoins.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

Une boule <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> fonctionne comme une boucle <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>. Les boucles partitionnent la collection source et planifient le travail sur plusieurs threads en fonction de l’environnement système. Plus il y a de processeurs sur le système, plus la méthode parallèle s’exécute rapidement. Pour certaines collections sources, une boucle séquentielle peut être plus rapide, selon la taille de la source et le type de travail exécuté par la boucle. Pour plus d’informations sur les performances, consultez [pièges potentiels dans le parallélisme des données et des tâches](potential-pitfalls-in-data-and-task-parallelism.md).

Pour plus d’informations sur les boucles parallèles, consultez [Comment : écrire une boucle Parallel. for simple](how-to-write-a-simple-parallel-for-loop.md).

Pour utiliser <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> avec une collection non générique, vous pouvez utiliser la méthode d’extension <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> pour convertir la collection en une collection générique, comme indiqué dans l’exemple suivant :

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Vous pouvez également utiliser PLINQ (Parallel LINQ) pour paralléliser le traitement des sources de données <xref:System.Collections.Generic.IEnumerable%601>. PLINQ vous permet d’utiliser la syntaxe de requête déclarative pour exprimer le comportement de la boucle. Pour plus d’informations, consultez [PLINQ (Parallel LINQ)](introduction-to-plinq.md).

## <a name="compile-and-run-the-code"></a>Compiler et exécuter le code

Vous pouvez compiler le code en tant qu’application de console pour .NET Framework ou en tant qu’application de console pour .NET Core.

Dans Visual Studio, il existe des modèles d’application de console Visual Basic et C# pour Windows Desktop et .NET Core.

À partir de la ligne de commande, vous pouvez utiliser les commandes CLI .NET Core (par exemple, `dotnet new console` ou `dotnet new console -lang vb` ), ou vous pouvez créer le fichier et utiliser le compilateur de ligne de commande pour une application .NET Framework.

Pour un projet .NET Core, vous devez référencer le package NuGet **System.Drawing.Common**. Dans Visual Studio, utilisez le gestionnaire de package NuGet pour installer le package. Vous pouvez aussi ajouter une référence au package dans votre fichier \*.csproj ou \*.vbproj :

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Pour exécuter une application de console .NET Core depuis la ligne de commande, utilisez `dotnet run` depuis le dossier qui contient votre application.

Pour exécuter votre application de console depuis Visual Studio, appuyez sur **F5**.

## <a name="see-also"></a>Voir aussi

- [Parallélisme des données](data-parallelism-task-parallel-library.md)
- [Programmation parallèle](index.md)
- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
