---
title: Méthodes d’extension - Guide de programmation C#
ms.date: 03/19/2020
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 0b35ad523fc7f0949cb5243edbdc50cd3e927999
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249218"
---
# <a name="extension-methods-c-programming-guide"></a>Méthodes d’extension (Guide de programmation C#)

Les méthodes d'extension vous permettent d'« ajouter » des méthodes à des types existants sans créer un type dérivé, ni recompiler ou modifier le type d'origine. Les méthodes d’extension sont des méthodes statiques, mais elles sont appelées comme si elles étaient des méthodes d’instance sur le type étendu. Pour le code client écrit en C, F et Visual Basic, il n’y a aucune différence apparente entre l’appel d’une méthode d’extension et les méthodes définies dans un type.

Les méthodes d’extension les plus courantes sont les opérateurs de <xref:System.Collections.IEnumerable?displayProperty=nameWithType> requête <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> standard LINQ qui ajoutent des fonctionnalités de requête aux existants et aux types. Pour utiliser les opérateurs de requête standard, introduisez-les d'abord dans la portée avec une directive `using System.Linq`. Puis, tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601> semble avoir des méthodes d'instance telles que <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>, etc. Vous pouvez consulter ces méthodes supplémentaires dans la saisie semi-automatique des instructions IntelliSense quand vous tapez un « point » après une instance d’un type <xref:System.Collections.Generic.IEnumerable%601> tel que <xref:System.Collections.Generic.List%601> ou <xref:System.Array>.

### <a name="orderby-example"></a>Exemple OrderBy

L'exemple suivant indique comment appeler la méthode `OrderBy` d'opérateur de requête standard sur un tableau d'entiers. L'expression entre parenthèses est une expression lambda. De nombreux opérateurs de requête standard prennent les expressions lambda comme paramètres, mais ce n’est pas une exigence pour les méthodes d’extension. Pour plus d’informations, voir [Lambda Expressions](../statements-expressions-operators/lambda-expressions.md).

[!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]

Les méthodes d’extension sont définies comme méthodes statiques mais sont appelées en utilisant la syntaxe de méthode d’instance. Leur premier paramètre précise sur quel type la méthode fonctionne. Le paramètre est précédé par le [modificateur](../../language-reference/keywords/this.md) de ce modificateur. Les méthodes d'extension sont uniquement dans la portée lorsque vous importez explicitement l'espace de noms dans votre code source avec une directive `using`.

L'exemple suivant présente une méthode d'extension définie pour la classe <xref:System.String?displayProperty=nameWithType>. Il est défini à l’intérieur d’une classe statique non imbriquée et non générique :

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

Vous invoquez la méthode d’extension dans votre code avec la syntaxe de méthode d’instance. La langue intermédiaire (IL) générée par le compilateur traduit votre code en un appel sur la méthode statique. Le principe de l’encapsulation n’est pas vraiment violé. Les méthodes d’extension ne peuvent pas accéder aux variables privées dans le type qu’elles étendent.

Pour plus d’informations, voir [Comment implémenter et appeler une méthode d’extension personnalisée](./how-to-implement-and-call-a-custom-extension-method.md).

En général, vous allez probablement appeler des méthodes d’extension beaucoup plus souvent que la mise en œuvre de votre propre. Comme les méthodes d'extension sont appelées à l'aide de la syntaxe de méthode d'instance, aucune connaissance particulière n'est requise pour les utiliser depuis le code client. Pour activer des méthodes d'extension pour un type particulier, ajoutez simplement une directive `using` pour l'espace de noms dans lequel les méthodes sont définies. Par exemple, pour utiliser les opérateurs de requête standard, ajoutez la directive `using` à votre code :

```csharp
using System.Linq;
```

(Vous devrez peut-être également ajouter une référence à System.Core.dll.) Vous remarquerez que les opérateurs de requête standard apparaissent maintenant dans <xref:System.Collections.Generic.IEnumerable%601> IntelliSense comme méthodes supplémentaires disponibles pour la plupart des types.

## <a name="binding-extension-methods-at-compile-time"></a>Liaison de méthodes d’extension à la compilation

Vous pouvez utiliser des méthodes d'extension pour étendre une classe ou une interface, mais pas pour les remplacer. Une méthode d'extension avec le même nom et la même signature qu'une méthode d'interface ou de classe ne sera jamais appelée. Au moment de la compilation, les méthodes d'extension ont toujours la priorité la plus faible par rapport aux méthodes d'instance définies dans le type lui-même. En d'autres termes, si un type a une méthode nommée `Process(int i)` et que vous avez une méthode d'extension avec la même signature, le compilateur créera toujours une liaison avec la méthode d'instance. Lorsque le compilateur rencontre un appel de méthode, il recherche d'abord une correspondance dans les méthodes d'instance du type. Si aucune correspondance n'est trouvée, il recherche toutes les méthodes d'extension définies pour le type et crée une liaison avec la première méthode d'extension qu'il trouve. L’exemple suivant montre comment le compilateur détermine quelle méthode d’extension ou méthode d’instance est choisie pour créer une liaison.

## <a name="example"></a>Exemple

L’exemple suivant montre les règles que le compilateur C# suit pour déterminer s’il faut lier un appel de méthode à une méthode d’instance sur le type, ou à une méthode d’extension. Le classe statique `Extensions` contient des méthodes d'extension définies pour tout type qui implémente `IMyInterface`. Les classes `A`, `B` et `C` implémentent toutes l'interface.

La méthode d'extension `MethodB` n'est jamais appelée car son nom et sa signature correspondent exactement aux méthodes déjà implémentées par les classes.

Lorsque le compilateur ne peut pas trouver une méthode d’instance avec une signature correspondante, il se lie à une méthode d’extension correspondante si l’on existe.

[!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]

## <a name="common-usage-patterns"></a>Modèles d’utilisation courants

### <a name="collection-functionality"></a>Fonctionnalités des collections

Dans le passé, il était courant de créer <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> des « classes de collection » qui implémentait l’interface pour un type donné et contenaient des fonctionnalités qui fonctionnaient sur des collections de ce type. Bien qu’il n’y ait rien de mal à créer ce type d’objet de collection, la même fonctionnalité peut être réalisée en utilisant une extension sur le <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Les extensions ont l’avantage de permettre que la <xref:System.Array?displayProperty=nameWithType> fonctionnalité <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> soit <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> appelée à partir d’une collection telle qu’une ou une telle implémentations sur ce type. Un exemple de ceci utilisant un tableau d’Int32 peut être trouvé [plus tôt dans cet article.](#orderby-example)

### <a name="layer-specific-functionality"></a>Fonctionnalité spécifique à la couche

Lors de l’utilisation d’une architecture d’oignon ou d’une autre conception d’application en couches, il est courant d’avoir un ensemble d’entités de domaine ou d’objets de transfert de données qui peuvent être utilisés pour communiquer au-delà des limites de l’application. Ces objets ne contiennent généralement aucune fonctionnalité, ni seulement des fonctionnalités minimales qui s’appliquent à toutes les couches de l’application. Les méthodes d’extension peuvent être utilisées pour ajouter des fonctionnalités spécifiques à chaque couche d’application sans charger l’objet vers le bas avec des méthodes non nécessaires ou voulues dans d’autres couches.

```aspx-csharp
public class DomainEntity
{
    public int Id { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
}

static class DomainEntityExtensions
{
    static string FullName(this DomainEntity value)
        => $"{value.FirstName} {value.LastName}";
}
```

### <a name="extending-predefined-types"></a>Extension des types prédéfinis

Plutôt que de créer de nouveaux objets lorsque des fonctionnalités réutilisables doivent être créées, nous pouvons souvent étendre un type existant tel qu’un cadre .NET ou un type CLR. Par exemple, si nous n’utilisons pas de `Engine` méthodes `Query` d’extension, nous pourrions créer une classe ou une classe pour effectuer une requête sur un serveur SQL qui peut être appelé à partir de plusieurs endroits dans notre code. Cependant, nous pouvons <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> plutôt étendre la classe en utilisant des méthodes d’extension pour effectuer cette requête de n’importe où nous avons une connexion à un serveur SQL. D’autres exemples pourraient être <xref:System.String?displayProperty=nameWithType> d’ajouter des fonctionnalités <xref:System.IO.File?displayProperty=nameWithType> communes <xref:System.IO.Stream?displayProperty=nameWithType> à <xref:System.Exception?displayProperty=nameWithType> la classe, d’étendre les capacités de traitement des données et des objets, et des objets pour des fonctionnalités spécifiques de manipulation d’erreurs. Ces types de cas d’utilisation ne sont limités que par votre imagination et votre bon sens.

L’extension des types prédéfinis peut être difficile avec `struct` les types parce qu’ils sont transmis par valeur aux méthodes. Cela signifie que toute modification de la struct est apportée à une copie de la struct. Ces modifications ne sont pas visibles une fois que la méthode d’extension sort. En commençant par C 7.2, `ref` vous pouvez ajouter le modificateur au premier argument d’une méthode d’extension. L’ajout du `ref` modificateur signifie que le premier argument est adopté par référence. Cela vous permet d’écrire des méthodes d’extension qui modifient l’état de la struct étant étendu.

## <a name="general-guidelines"></a>Instructions générales

Bien qu’il soit toujours considéré comme préférable d’ajouter des fonctionnalités en modifiant le code d’un objet ou en dérivant un nouveau type chaque fois qu’il est raisonnable et possible de le faire, les méthodes d’extension sont devenues une option cruciale pour créer des fonctionnalités réutilisables tout au long de la .NET Écosystème. Pour les occasions où la source d’origine n’est pas sous votre contrôle, quand un objet dérivé est inapproprié ou impossible, ou lorsque la fonctionnalité ne doit pas être exposée au-delà de sa portée applicable, les méthodes d’extension sont un excellent choix.

Pour plus d’informations sur les types dérivés, voir [Héritage](./inheritance.md).

Lorsque vous utilisez une méthode d’extension pour étendre un type dont le code source que vous n’êtes pas en contrôle, vous courez le risque qu’un changement dans la mise en œuvre du type provoque votre méthode d’extension à briser.

Si vous implémentez des méthodes d’extension pour un type donné, prenez en compte les points suivants :

- Une méthode d'extension ne sera jamais appelée si elle a la même signature qu'une méthode définie dans le type.
- Les méthodes d'extension sont mises en portée au niveau de l'espace de noms. Par exemple, si vous avez plusieurs classes statiques qui `Extensions`contiennent des méthodes d’extension `using Extensions;` dans un seul namespace nommé, ils seront tous mis en portée par la directive.

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
