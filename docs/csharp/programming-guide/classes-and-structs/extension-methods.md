---
title: Méthodes d’extension - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: ce35ef4d4286310aa6c8b6e40c3a448b0d91ea7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937519"
---
# <a name="extension-methods-c-programming-guide"></a>Méthodes d’extension (Guide de programmation C#)
Les méthodes d'extension vous permettent d'« ajouter » des méthodes à des types existants sans créer un type dérivé, ni recompiler ou modifier le type d'origine. Les méthodes d'extension sont un type particulier de méthode statique appelées comme s'il s'agissait de méthodes d'instance sur le type étendu. Pour le code client écrit en C#, F# et Visual Basic, il n’y a aucune différence apparente lors de l’appel entre une méthode d’extension et les méthodes qui sont réellement définies dans un type.  
  
 Les méthodes d’extension les plus courantes sont les opérateurs de <xref:System.Collections.IEnumerable?displayProperty=nameWithType> requête <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> standard LINQ qui ajoutent des fonctionnalités de requête aux existants et aux types. Pour utiliser les opérateurs de requête standard, introduisez-les d'abord dans la portée avec une directive `using System.Linq`. Puis, tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601> semble avoir des méthodes d'instance telles que <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>, etc. Vous pouvez consulter ces méthodes supplémentaires dans la saisie semi-automatique des instructions IntelliSense quand vous tapez un « point » après une instance d’un type <xref:System.Collections.Generic.IEnumerable%601> tel que <xref:System.Collections.Generic.List%601> ou <xref:System.Array>.  
  
 L'exemple suivant indique comment appeler la méthode `OrderBy` d'opérateur de requête standard sur un tableau d'entiers. L'expression entre parenthèses est une expression lambda. De nombreux opérateurs de requête standard prennent des expressions lambda comme paramètres, mais ce n’est pas requis pour les méthodes d’extension. Pour plus d’informations, voir [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]  
  
 Les méthodes d’extension sont définies comme méthodes statiques mais sont appelées en utilisant la syntaxe de méthode d’instance. Leur premier paramètre spécifie les types sur lesquels la méthode s’applique et le paramètre est précédé du modificateur [this](../../language-reference/keywords/this.md). Les méthodes d'extension sont uniquement dans la portée lorsque vous importez explicitement l'espace de noms dans votre code source avec une directive `using`.  
  
 L'exemple suivant présente une méthode d'extension définie pour la classe <xref:System.String?displayProperty=nameWithType>. Notez qu'elle est définie à l'intérieur d'une classe statique, non imbriquée et non générique :  
  
 [!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]  
  
 La méthode d'extension `WordCount` peut être mise à portée avec cette directive `using` :  
  
```csharp  
using ExtensionMethods;  
```  
  
 Elle peut être appelée à partir d'une application à l'aide de cette syntaxe :  
  
```csharp  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 Dans votre code, vous appelez la méthode d'extension avec la syntaxe de méthode d'instance. Toutefois, le langage intermédiaire (IL) généré par le compilateur traduit votre code dans un appel sur la méthode statique. Par conséquent, le principe d'encapsulation n'est pas réellement violé. En fait, les méthodes d’extension ne peuvent pas accéder aux variables privées dans le type qu’elles étendent.  
  
 Pour plus d’informations, voir [Comment implémenter et appeler une méthode d’extension personnalisée](./how-to-implement-and-call-a-custom-extension-method.md).
  
 En général, vous appellerez probablement les méthodes d’extension beaucoup plus souvent que vous n’implémenterez vos propres méthodes. Comme les méthodes d'extension sont appelées à l'aide de la syntaxe de méthode d'instance, aucune connaissance particulière n'est requise pour les utiliser depuis le code client. Pour activer des méthodes d'extension pour un type particulier, ajoutez simplement une directive `using` pour l'espace de noms dans lequel les méthodes sont définies. Par exemple, pour utiliser les opérateurs de requête standard, ajoutez la directive `using` à votre code :  
  
```csharp  
using System.Linq;  
```  
  
 (Vous devrez peut-être également ajouter une référence à System.Core.dll.) Vous remarquerez que les opérateurs de requête standard apparaissent maintenant dans <xref:System.Collections.Generic.IEnumerable%601> IntelliSense comme méthodes supplémentaires disponibles pour la plupart des types.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Liaison de méthodes d’extension à la compilation  
 Vous pouvez utiliser des méthodes d'extension pour étendre une classe ou une interface, mais pas pour les remplacer. Une méthode d'extension avec le même nom et la même signature qu'une méthode d'interface ou de classe ne sera jamais appelée. Au moment de la compilation, les méthodes d'extension ont toujours la priorité la plus faible par rapport aux méthodes d'instance définies dans le type lui-même. En d'autres termes, si un type a une méthode nommée `Process(int i)` et que vous avez une méthode d'extension avec la même signature, le compilateur créera toujours une liaison avec la méthode d'instance. Lorsque le compilateur rencontre un appel de méthode, il recherche d'abord une correspondance dans les méthodes d'instance du type. Si aucune correspondance n'est trouvée, il recherche toutes les méthodes d'extension définies pour le type et crée une liaison avec la première méthode d'extension qu'il trouve. L’exemple suivant montre comment le compilateur détermine quelle méthode d’extension ou méthode d’instance est choisie pour créer une liaison.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre les règles que le compilateur C# suit pour déterminer s’il faut lier un appel de méthode à une méthode d’instance sur le type, ou à une méthode d’extension. Le classe statique `Extensions` contient des méthodes d'extension définies pour tout type qui implémente `IMyInterface`. Les classes `A`, `B` et `C` implémentent toutes l'interface.  
  
 La méthode d'extension `MethodB` n'est jamais appelée car son nom et sa signature correspondent exactement aux méthodes déjà implémentées par les classes.  
  
 Lorsque le compilateur ne trouve pas de méthode d’instance avec une signature correspondante, il crée une liaison avec une méthode d’extension correspondante, s’il en existe une.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]  
  
## <a name="general-guidelines"></a>Instructions générales  
 En général, nous vous recommandons d'implémenter des méthodes d'extension modérément et uniquement lorsque cela est nécessaire. Dès que cela est possible, le code client qui doit étendre un type existant doit le faire en créant un type dérivé du type existant. Pour plus d’informations, consultez [Héritage](./inheritance.md).  
  
 Lors de l’utilisation d’une méthode d’extension pour étendre un type dont le code source ne peut pas être modifié, vous risquez d’interrompre votre méthode d’extension en cas de modification dans l’implémentation du type.  
  
 Si vous implémentez des méthodes d’extension pour un type donné, prenez en compte les points suivants :  
  
- Une méthode d'extension ne sera jamais appelée si elle a la même signature qu'une méthode définie dans le type.  
  
- Les méthodes d'extension sont mises en portée au niveau de l'espace de noms. Par exemple, si vous avez plusieurs classes statiques qui contiennent des méthodes d'extension dans un espace de noms unique nommé `Extensions`, elles seront toutes mises en portée par la directive `using Extensions;`.  
  
 Pour une bibliothèque de classes que vous avez implémentée, vous ne devez pas utiliser de méthodes d'extension pour éviter d'incrémenter le numéro de version d'un assembly. Si vous souhaitez ajouter une fonctionnalité importante à une bibliothèque dont le code source vous appartient, vous devez suivre les directives .NET Framework standard relatives à la gestion de version des assemblys. Pour plus d’informations, consultez [Versioning des assemblys](../../../standard/assembly/versioning.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Exemples de programmation parallèle (il s’agit de nombreux exemples de méthodes d’extension)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Expressions lambda](../statements-expressions-operators/lambda-expressions.md)
- [Vue d’ensemble des opérateurs de requête standard](../concepts/linq/standard-query-operators-overview.md)
- [Règles de conversion pour les paramètres Instance et leur impact](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Interopérabilité des méthodes d’extension entre les langages](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Méthodes d’extension et délégués curryfiés](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Extension method Binding and Error reporting](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
