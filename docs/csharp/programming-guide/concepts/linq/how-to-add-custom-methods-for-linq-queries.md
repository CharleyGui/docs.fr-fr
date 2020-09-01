---
title: Comment ajouter des méthodes personnalisées pour les requêtes LINQ (C#)
description: Découvrez comment étendre la syntaxe des requêtes LINQ en ajoutant des méthodes d’extension à l' <T> interface IEnumerable en C#.
ms.date: 08/26/2020
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 768882fce40a2fc6e018f24c8928341e7c65bc4b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122423"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Comment ajouter des méthodes personnalisées pour les requêtes LINQ (C#)

Vous étendez l’ensemble de méthodes que vous utilisez pour les requêtes LINQ en ajoutant des méthodes d’extension à l' <xref:System.Collections.Generic.IEnumerable%601> interface. Par exemple, en plus des opérations standard de moyenne ou maximale, vous créez une méthode d’agrégation personnalisée pour calculer une valeur unique à partir d’une séquence de valeurs. Vous créez également une méthode qui fonctionne comme un filtre personnalisé ou une transformation de données spécifique pour une séquence de valeurs et retourne une nouvelle séquence. <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A> et <xref:System.Linq.Enumerable.Reverse%2A> en sont quelques exemples.

Quand vous étendez l’interface <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez appliquer vos méthodes personnalisées à n’importe quelle collection énumérable. Pour plus d’informations, consultez [Méthodes d’extension](../../classes-and-structs/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Ajout d’une méthode d’agrégation

Une méthode d’agrégation calcule une valeur à partir d’un ensemble de valeurs. LINQ fournit plusieurs méthodes d’agrégation, notamment <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A> et <xref:System.Linq.Enumerable.Max%2A>. Vous pouvez créer votre propre méthode d’agrégation en ajoutant une méthode d’extension à l’interface <xref:System.Collections.Generic.IEnumerable%601>.

L’exemple de code suivant montre comment créer une méthode d’extension appelée `Median` pour calculer une valeur médiane pour une séquence de nombres de type `double`.

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="LinqExtensionClass":::

Vous appelez cette méthode d’extension pour toute collection énumérable de la même façon que vous appelez d’autres méthodes d’agrégation depuis l’interface <xref:System.Collections.Generic.IEnumerable%601>.

L’exemple de code suivant montre comment utiliser la méthode `Median` pour un tableau de type `double`.

:::code language="csharp" source="./snippets/Program.cs" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Surcharge d’une méthode d’agrégation pour accepter différents types

Vous pouvez surcharger votre méthode d’agrégation pour qu’elle accepte des séquences de différents types. L’approche standard consiste à créer une surcharge pour chaque type. Une autre approche consiste à créer une surcharge qui accepte un type générique et le convertit en un autre type à l’aide d’un délégué. Vous pouvez également combiner ces deux approches.

#### <a name="to-create-an-overload-for-each-type"></a>Pour créer une surcharge pour chaque type

Vous pouvez créer une surcharge pour chacun des types que vous voulez prendre en charge. L’exemple de code suivant montre une surcharge de la méthode `Median` pour le type `int`.

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="IntOverload":::

Vous pouvez maintenant appeler les surcharges `Median` pour les types `integer` et `double`, comme indiqué dans le code suivant :

:::code language="csharp" source="./snippets/Program.cs" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a>Pour créer une surcharge générique

Vous pouvez également créer une surcharge qui accepte une séquence d’objets génériques. Cette surcharge prend un délégué comme paramètre et l’utilise pour convertir une séquence d’objets de type générique en un autre type d’objets.

Le code suivant montre une surcharge de la méthode `Median` qui prend le délégué <xref:System.Func%602> comme paramètre. Ce délégué prend un objet de type générique T et retourne un objet de type `double`.

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="GenericOverload":::

Vous pouvez maintenant appeler la méthode `Median` pour une séquence d’objets de tout type. Si le type n’a pas sa propre surcharge de méthode, vous devez passer un paramètre de délégué. En C#, vous pouvez utiliser une expression lambda à cet effet. En outre, en Visual Basic uniquement, si vous utilisez la clause `Aggregate` ou `Group By` au lieu de l’appel de méthode, vous pouvez passer n’importe quelle valeur ou expression qui se trouve dans la portée de cette clause.

L’exemple de code suivant montre comment appeler la méthode `Median` pour un tableau d’entiers et un tableau de chaînes. Pour les chaînes, c’est la valeur médiane des longueurs de chaînes du tableau qui est calculée. L’exemple montre comment passer le paramètre de délégué <xref:System.Func%602> à la méthode `Median` pour chaque cas.

:::code language="csharp" source="./snippets/Program.cs" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-sequence"></a>Ajout d’une méthode qui retourne une séquence

Vous pouvez étendre l’interface <xref:System.Collections.Generic.IEnumerable%601> avec une méthode de requête personnalisée qui retourne une séquence de valeurs. Dans ce cas, la méthode doit retourner une collection de type <xref:System.Collections.Generic.IEnumerable%601>. Ces méthodes peuvent être utilisées pour appliquer des filtres ou des transformations de données à une séquence de valeurs.

L’exemple suivant montre comment créer une méthode d’extension nommée `AlternateElements` qui retourne un élément sur deux d’une collection, en commençant par le premier élément.

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="SequenceElement":::

Vous pouvez appeler cette méthode d’extension pour n’importe quelle collection énumérable, de la même façon que vous appelez d’autres méthodes depuis l’interface <xref:System.Collections.Generic.IEnumerable%601>, comme le montre le code suivant :

:::code language="csharp" source="./snippets/Program.cs" ID="SequenceUsage":::

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic.IEnumerable%601>
- [Méthodes d’extension](../../classes-and-structs/extension-methods.md)
