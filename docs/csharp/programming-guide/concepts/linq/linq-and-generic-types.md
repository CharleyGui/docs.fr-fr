---
title: LINQ et types génériques (C#)
description: Découvrez les concepts de base des types génériques en C# qui prennent en charge les requêtes.  Les requêtes LINQ sont basées sur des types génériques.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: a71957eabea788fb06195df1ef026390947f013d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170465"
---
# <a name="linq-and-generic-types-c"></a>LINQ et types génériques (C#)

Les requêtes LINQ sont basées sur des types génériques, qui ont été introduits dans la version 2,0 de .NET Framework. Vous ne devez pas avoir une connaissance approfondie des génériques avant de commencer à écrire des requêtes. Il peut cependant être important de comprendre deux concepts de base :  
  
1. Quand vous créez une instance d’une classe de collection générique comme <xref:System.Collections.Generic.List%601>, vous remplacez le « T » par le type des objets contenus dans la liste. Par exemple, une liste de chaînes est exprimée sous la forme `List<string>`, et une liste d’objets `Customer` est exprimée sous la forme `List<Customer>`. Une liste générique est fortement typée et offre de nombreux avantages par rapport aux collections qui stockent leurs éléments en tant que <xref:System.Object>. Si vous essayez d’ajouter un `Customer` à un `List<string>`, vous obtenez une erreur à la compilation. Il est facile d’utiliser des collections génériques, car vous ne devez pas effectuer un cast de type à l’exécution.  
  
2. <xref:System.Collections.Generic.IEnumerable%601> est l’interface qui permet l’énumération des classes de collection génériques avec l’instruction `foreach`. Les classes de collection génériques prennent en charge <xref:System.Collections.Generic.IEnumerable%601> de la même façon que les classes de collection non génériques telles que <xref:System.Collections.ArrayList> prennent en charge <xref:System.Collections.IEnumerable>.  
  
 Pour plus d’informations sur les génériques, consultez [Génériques](../../generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>Variables IEnumerable<T\> dans les requêtes LINQ  

 Les variables de requête LINQ sont typées comme <xref:System.Collections.Generic.IEnumerable%601> ou un type dérivé tel que <xref:System.Linq.IQueryable%601> . Quand vous voyez une variable de requête typée en `IEnumerable<Customer>`, cela signifie simplement que la requête génère à l’exécution une séquence de zéro ou plusieurs objets `Customer`.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Pour plus d’informations, consultez [relations de types dans les opérations de requête LINQ](./type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Laisser le compilateur gérer les déclarations de types génériques  

 Si vous préférez, vous pouvez éviter une syntaxe générique en utilisant le mot clé [var](../../../language-reference/keywords/var.md). Le mot clé `var` indique au compilateur d’inférer le type d’une variable de requête en examinant la source de données spécifiée dans la clause `from`. L’exemple suivant génère le même code compilé que l’exemple précédent :  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 Le mot clé `var` est utile quand le type de la variable est évident ou quand il est particulièrement important de spécifier explicitement des types génériques imbriqués, comme ceux qui sont produits par des requêtes de groupe. D’une façon générale, si vous utilisez `var`, sachez qu’il peut rendre votre code plus difficile à lire par d’autres développeurs. Pour plus d’informations, consultez [Variables locales implicitement typées](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Voir aussi

- [Génériques](../../generics/index.md)
