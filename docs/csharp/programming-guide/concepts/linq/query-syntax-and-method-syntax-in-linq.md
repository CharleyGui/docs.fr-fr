---
title: Syntaxe de requête et syntaxe de méthode dans LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], query syntax vs. method syntax
- queries [LINQ in C#], syntax comparisons
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
ms.openlocfilehash: 17280daaf98010245bbd019652a2a46d7f66ab59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635494"
---
# <a name="query-syntax-and-method-syntax-in-linq-c"></a>Syntaxe de requête et syntaxe de méthode dans LINQ (C#)
La plupart des requêtes dans la documentation d’introduction de la requête intégrée linguistique (LINQ) sont rédigées à l’aide de la syntaxe de requête déclarative linQ. Toutefois, la syntaxe de requête doit être traduite en appels de méthode pour le Common Langage Runtime (CLR) .NET lorsque le code est compilé. Ces appels de méthode appellent les opérateurs de requête standard, qui ont des noms tels que `Where`, `Select`, `GroupBy`, `Join`, `Max` et `Average`. Vous pouvez les appeler directement en utilisant la syntaxe de méthode à la place de la syntaxe de requête.  
  
 La syntaxe de requête et la syntaxe de méthode sont identiques sémantiquement, mais de nombreuses personnes trouvent la syntaxe de requête plus simple et plus facile à lire. Certaines requêtes doivent être exprimées en tant qu’appels de méthode. Par exemple, vous devez utiliser un appel de méthode pour exprimer une requête qui récupère le nombre d’éléments qui correspondent à une condition spécifiée. Vous devez également utiliser un appel de méthode pour une requête qui récupère dans une séquence source l’élément qui a la valeur maximale. En général, la documentation de référence des opérateurs de requête standard dans l’espace de noms <xref:System.Linq> utilise la syntaxe de méthode. Par conséquent, même lorsque vous commencerez à écrire des requêtes LINQ, il est utile de connaître la façon d’utiliser la syntaxe de méthode dans les requêtes et dans les expressions de requête elles-mêmes.  
  
## <a name="standard-query-operator-extension-methods"></a>Méthodes d’extension d’opérateur de requête standard  
 L’exemple suivant présente une *expression de requête* simple et la requête sémantiquement équivalente écrite en tant que *requête fondée sur une méthode*.  
  
 [!code-csharp[csLINQGettingStarted#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#22)]  
  
 La sortie des deux exemples est identique. Vous pouvez voir que le type de la variable de requête est le même dans les deux formes : <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Pour comprendre la requête basée sur une méthode, examinons-la de plus près. Du côté droit de l’expression, remarquez que la clause `where` est maintenant exprimée comme une méthode d’instance sur l’objet `numbers`, qui, comme vous vous en rappelez, a un type `IEnumerable<int>`. Si vous êtes connaissez bien l’interface <xref:System.Collections.Generic.IEnumerable%601> générique, vous savez qu’elle n’a pas de méthode `Where`. Toutefois, si vous appelez la liste de saisie semi-automatique IntelliSense dans l’IDE de Visual Studio, vous ne verrez pas seulement une méthode `Where`, mais de nombreuses autres méthodes telles que `Select`, `SelectMany`, `Join` et `Orderby`. Il s’agit de tous les opérateurs de requête standard.  
  
 ![Capture d’écran montrant tous les opérateurs de requête standard dans Intellisense.](./media/query-syntax-and-method-syntax-in-linq/standard-query-operators.png)  
  
 Même s’il semble que <xref:System.Collections.Generic.IEnumerable%601> a été redéfini pour inclure ces méthodes supplémentaires, ce n’est pas le cas, en réalité. Les opérateurs de requête standard sont implémentés comme un nouveau type de méthode, appelé *méthodes d’extension*. Les méthodes d’extension « étendent » un type existant. Elles peuvent être appelées comme s’il s’agissait de méthodes d’instance sur le type. Les opérateurs de requête standard étendent <xref:System.Collections.Generic.IEnumerable%601>, si bien que vous pouvez écrire `numbers.Where(...)`.  
  
 Pour commencer à utiliser LINQ, tout ce que vous devez vraiment savoir sur les méthodes `using` d’extension est de savoir comment les mettre en portée dans votre application en utilisant les directives correctes. Du point de vue de votre application, une méthode d’extension et une méthode d’instance normale sont identiques.  
  
 Pour plus d’informations sur les méthodes d’extension, consultez [Méthodes d’extension](../../classes-and-structs/extension-methods.md). Pour plus d’informations sur les opérateurs de requête standard, consultez [Présentation des opérateurs de requête standard (C#)](./standard-query-operators-overview.md). Certains fournisseurs de LINQ, tels que [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mettre en œuvre leurs propres opérateurs de requête standard et des méthodes d’extension supplémentaires pour d’autres types en outre <xref:System.Collections.Generic.IEnumerable%601>.  
  
## <a name="lambda-expressions"></a>Expressions lambda  
 Dans l’exemple précédent, notez que l’expression conditionnelle (`num % 2 == 0`) est passée comme argument de ligne à la méthode `Where` : `Where(num => num % 2 == 0).` Cette expression inline est appelée expression lambda. C’est un moyen pratique d’écrire du code qui devrait autrement être écrit sous une forme plus fastidieuse, comme une méthode anonyme, un délégué générique ou une arborescence d’expressions. En C#, `=>` est l’opérateur lambda, qui se lit « conduit à ». Le `num` situé à gauche de l’opérateur est la variable d’entrée qui correspond à `num` dans l’expression de requête. Le compilateur peut déduire le type de `num`, car il sait que `numbers` est un type <xref:System.Collections.Generic.IEnumerable%601> générique. Le corps de l’expression lambda est identique à l’expression dans la syntaxe de requête ou dans toute autre expression ou instruction C#. Il peut inclure des appels de méthode et une autre logique complexe. La « valeur de retour » est simplement le résultat de l’expression.  
  
 Pour commencer à utiliser LINQ, vous n’avez pas à utiliser lambdas intensivement. Toutefois, certaines requêtes peuvent être exprimées uniquement dans la syntaxe de méthode. Parmi elles, certaines nécessitent des expressions lambda. Une fois que vous vous familiariserez avec les lambdas, vous constaterez qu’ils sont un outil puissant et flexible dans votre boîte à outils LINQ. Pour plus d’informations, voir [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).  
  
## <a name="composability-of-queries"></a>Composabilité des requêtes  
 Dans l’exemple de code précédent, notez que la méthode `OrderBy` est appelée à l’aide de l’opérateur point sur l’appel à `Where`. `Where` produit une séquence filtrée, puis `Orderby` agit sur cette séquence en la triant. Étant donné que les requêtes retournent un `IEnumerable`, vous les composez dans la syntaxe de méthode en chaînant les appels de méthode ensemble. Le compilateur effectue cette opération en arrière-plan lorsque vous écrivez des requêtes à l’aide de la syntaxe de requête. De plus, étant donné qu’une variable de requête ne stocke pas les résultats de la requête, vous pouvez la modifier ou l’utiliser à tout moment comme base d’une nouvelle requête, même après son exécution.  
