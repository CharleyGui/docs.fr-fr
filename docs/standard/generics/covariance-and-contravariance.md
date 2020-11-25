---
title: Covariance et contravariance dans les génériques
description: En savoir plus sur la covariance, qui vous permet d’utiliser un type plus dérivé, et la contravariance, qui vous permet d’utiliser un type moins dérivé, dans des génériques .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics, covariance and contravariance
- generics, variance
- covariance and contravariance in generics
- generic type parameters
ms.assetid: 2678dc63-c7f9-4590-9ddc-0a4df684d42e
ms.openlocfilehash: 9d5d5b27fb77500aa5f6deff3fcb1c739ba8b094
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722659"
---
# <a name="covariance-and-contravariance-in-generics"></a>Covariance et contravariance dans les génériques

La *covariance* et la *contravariance* sont des termes qui font référence à la possibilité d’utiliser un type plus dérivé (plus spécifique) ou un type moins dérivé (moins spécifique) que celui spécifié à l’origine. Les paramètres de type générique prennent en charge la covariance et la contravariance afin de fournir une meilleure flexibilité dans l'assignation et l'utilisation des types génériques.

Lorsque vous faites référence à un système de type, la covariance, la contravariance et l’invariance ont les définitions suivantes. Les exemples supposent qu'une classe de base est nommée `Base` et qu'une classe dérivée est nommée `Derived`.  
  
- `Covariance`  
  
     Vous permet d'utiliser un type plus dérivé que celui spécifié à l'origine.  
  
     Vous pouvez assigner une instance de `IEnumerable<Derived>` à une variable de type `IEnumerable<Base>` .  
  
- `Contravariance`  
  
     Vous permet d'utiliser un type plus générique (moins dérivé) que celui spécifié à l'origine.  
  
     Vous pouvez assigner une instance de `Action<Base>` à une variable de type `Action<Derived>` .  
  
- `Invariance`  
  
     Signifie que vous pouvez utiliser uniquement le type spécifié à l’origine. Un paramètre de type générique indifférent n’est ni covariant ni contravariant.  
  
     Vous ne pouvez pas assigner une instance de `List<Base>` à une variable de type `List<Derived>` , ou vice versa.  
  
 Les paramètres de type covariant vous permettent d'effectuer des assignations très similaires au [Polymorphisme](../../csharp/programming-guide/classes-and-structs/polymorphism.md) ordinaire, comme indiqué dans le code suivant.  
  
 [!code-csharp[CoContraSimpleIEnum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleienum/cs/example.cs#1)]
 [!code-vb[CoContraSimpleIEnum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleienum/vb/example.vb#1)]  
  
 La classe <xref:System.Collections.Generic.List%601> implémente l'interface générique <xref:System.Collections.Generic.IEnumerable%601> , donc `List<Derived>` (`List(Of Derived)` en Visual Basic) implémente `IEnumerable<Derived>`. Le paramètre de type covariant fait le reste.  
  
 La contravariance, en revanche, paraît peu intuitive. L'exemple suivant crée un délégué de type `Action<Base>` (`Action(Of Base)` en Visual Basic), puis assigne ce délégué à une variable de type `Action<Derived>`.  
  
 [!code-csharp[CoContraSimpleAction#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontrasimpleaction/cs/example.cs#1)]
 [!code-vb[CoContraSimpleAction#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontrasimpleaction/vb/example.vb#1)]  
  
 Cela peut paraître rétrograde, mais c'est le code de type sécurisé qui est compilé et exécuté. L’expression lambda correspond au délégué auquel elle est assignée. elle définit donc une méthode qui accepte un paramètre de type `Base` et n’a aucune valeur de retour. Le délégué résultant peut être assigné à une variable de type `Action<Derived>` parce que le paramètre de type `T` du délégué <xref:System.Action%601> est contravariant. Le code est de type sécurisé parce que `T` spécifie un type de paramètre. Lorsque le délégué de type `Action<Base>` est appelé comme s'il était de type `Action<Derived>`, son argument doit être de type `Derived`. Cet argument peut toujours être passé sans risque à la méthode sous-jacente, parce que le paramètre de la méthode est de type `Base`.  
  
 En général, un paramètre de type covariant peut être utilisé comme type de retour d'un délégué et les paramètres de type contravariant peuvent être utilisés comme types de paramètres. Pour une interface, les paramètres de type covariant peuvent être utilisés comme types de retour des méthodes de l'interface et les paramètres de type contravariant peuvent être utilisés comme types de paramètres des méthodes de l'interface.  
  
 La covariance et la contravariance sont désignées collectivement sous le nom de *variation*. Un paramètre de type générique qui n'est marqué ni comme étant covariant, ni comme étant contravariant, est appelé *indifférent*. Récapitulatif des informations relatives à la variance dans le common language runtime :  
  
- Les paramètres de type Variant sont limités aux types d’interfaces génériques et aux types délégués génériques.  
  
- Un type d'interface générique ou un type délégué générique peut avoir des paramètres de type covariant et contravariant.  
  
- La variance s'applique uniquement aux types référence ; si vous spécifiez un type valeur pour un paramètre de type variant, ce paramètre de type est indifférent pour le type construit résultant.  
  
- La variance ne s'applique pas à la combinaison de délégués. Autrement dit, avec deux délégués de types `Action<Derived>` et `Action<Base>` (`Action(Of Derived)` et `Action(Of Base)` en Visual Basic), il n'est pas possible de combiner le deuxième délégué avec le premier, même si le résultat sera de type sécurisé. La variance permet au deuxième délégué d'être assigné à une variable de type `Action<Derived>`, mais les délégués peuvent uniquement être combinés si leurs types correspondent exactement.

- À compter de C# 9, les types de retour covariants sont pris en charge. Une méthode de substitution peut déclarer un type de retour plus dérivé comme méthode qu’elle substitue, et une propriété de substitution, en lecture seule peut déclarer un type plus dérivé.

<a name="InterfaceCovariantTypeParameters"></a>

## <a name="generic-interfaces-with-covariant-type-parameters"></a>Interfaces génériques avec paramètres de type covariant

Plusieurs interfaces génériques ont des paramètres de type covariant, par exemple,,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Linq.IQueryable%601> et <xref:System.Linq.IGrouping%602> . Tous les paramètres de type de ces interfaces sont covariants, les paramètres de type sont donc uniquement utilisés pour les types de retour des membres.  
  
 L'exemple suivant illustre les paramètres de type covariant. L'exemple définit deux types : `Base` a une méthode statique nommée `PrintBases` qui prend un `IEnumerable<Base>` (`IEnumerable(Of Base)` en Visual Basic) et imprime les éléments. `Derived` hérite de `Base`. L'exemple crée un `List<Derived>` vide (`List(Of Derived)` en Visual Basic) et montre que ce type peut être passé à `PrintBases` et assigné à une variable de type `IEnumerable<Base>` sans cast. <xref:System.Collections.Generic.List%601> implémente <xref:System.Collections.Generic.IEnumerable%601>, qui a un paramètre de type covariant unique. Le paramètre de type covariant est la raison pour laquelle une instance de `IEnumerable<Derived>` peut être utilisée au lieu de `IEnumerable<Base>`.  
  
 [!code-csharp[CoContravarianceInClrGenericI#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici/vb/example.vb#1)]  
  
## <a name="generic-interfaces-with-contravariant-type-parameters"></a>Interfaces génériques avec paramètres de type contravariant

Plusieurs interfaces génériques ont des paramètres de type contravariant ; par exemple : <xref:System.Collections.Generic.IComparer%601> , <xref:System.IComparable%601> et <xref:System.Collections.Generic.IEqualityComparer%601> . Ces interfaces ont des paramètres de type contravariant uniquement, par conséquent, les paramètres de type sont utilisés uniquement comme types de paramètre dans les membres des interfaces.  
  
 L'exemple suivant illustre les paramètres de type contravariant. L'exemple définit une classe abstraite (`MustInherit` dans Visual Basic) `Shape` avec une propriété `Area` . L'exemple définit également une classe `ShapeAreaComparer` qui implémente `IComparer<Shape>` (`IComparer(Of Shape)` dans Visual Basic). L'implémentation de la méthode <xref:System.Collections.Generic.IComparer%601.Compare%2A?displayProperty=nameWithType> est basée sur la valeur de la propriété `Area` , de sorte que `ShapeAreaComparer` peut être utilisé pour trier des objets `Shape` par zone.  
  
 La classe `Circle` hérite de `Shape` et remplace `Area`. L'exemple crée un <xref:System.Collections.Generic.SortedSet%601> d'objets `Circle` , à l'aide d'un constructeur qui accepte un `IComparer<Circle>` (`IComparer(Of Circle)` dans Visual Basic). Toutefois, au lieu de passer un `IComparer<Circle>`, l'exemple passe un objet `ShapeAreaComparer` qui implémente `IComparer<Shape>`. L'exemple peut passer un comparateur d'un type moins dérivé (`Shape`) lorsque le code appelle un comparateur d'un type plus dérivé (`Circle`), parce que le paramètre de type de l'interface générique <xref:System.Collections.Generic.IComparer%601> est contravariant.  
  
 Lorsqu'un nouvel objet `Circle` est ajouté au `SortedSet<Circle>`, la méthode `IComparer<Shape>.Compare` (méthode `IComparer(Of Shape).Compare` dans Visual Basic) de l'objet `ShapeAreaComparer` est appelée chaque fois que le nouvel élément est comparé à un élément existant. Le type de paramètre de la méthode (`Shape`) étant moins dérivé que le type passé (`Circle`), l'appel garantit la cohérence des types. La contravariance permet à `ShapeAreaComparer` de trier une collection d'un type unique, ainsi qu'une collection mixte de types, qui dérivent de `Shape`.  
  
 [!code-csharp[CoContravarianceInClrGenericI2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravarianceinclrgenerici2/cs/example.cs#1)]
 [!code-vb[CoContravarianceInClrGenericI2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravarianceinclrgenerici2/vb/example.vb#1)]  

## <a name="generic-delegates-with-variant-type-parameters"></a>Délégués génériques avec paramètres de type Variant

Les `Func` délégués génériques, tels que <xref:System.Func%602> , ont des types de retour covariants et des types de paramètres contravariants. Les délégués génériques `Action` , tels que <xref:System.Action%602>, ont des types de paramètres contravariants. Cela signifie que les délégués peuvent être assignés à des variables avec des types de paramètres plus dérivés et (dans le cas des délégués génériques `Func` ) des types de retour moins dérivés.  
  
> [!NOTE]
> Le dernier paramètre de type générique des délégués génériques `Func` spécifie le type de la valeur de retour dans la signature du délégué. Il est covariant (mot clé`out` ), alors que les autres paramètres de type générique sont contravariants (mot clé`in` ).  
  
 Le code suivant illustre cela. La première partie du code définit une classe nommée `Base`, une classe nommée `Derived` qui hérite de `Base`, et une autre classe avec une méthode `static` (`Shared` en Visual Basic) nommée `MyMethod`. La méthode prend une instance de `Base` et retourne une instance de `Derived`. (Si l’argument est une instance de `Derived` , le `MyMethod` retourne ; si l’argument est une instance de `Base` , `MyMethod` retourne une nouvelle instance de `Derived` .) Dans `Main()` , l’exemple crée une instance de `Func<Base, Derived>` ( `Func(Of Base, Derived)` dans Visual Basic) qui représente `MyMethod` et le stocke dans la variable `f1` .  
  
 [!code-csharp[CoContravarianceDelegates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#2)]
 [!code-vb[CoContravarianceDelegates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#2)]  
  
 La deuxième partie du code indique que le délégué peut être assigné à une variable de type `Func<Base, Base>` (`Func(Of Base, Base)` en Visual Basic), car le type de retour est covariant.  
  
 [!code-csharp[CoContravarianceDelegates#3](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#3)]
 [!code-vb[CoContravarianceDelegates#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#3)]  
  
 La troisième partie du code indique que le délégué peut être assigné à une variable de type `Func<Derived, Derived>` (`Func(Of Derived, Derived)` en Visual Basic), car le type de paramètre est contravariant.  
  
 [!code-csharp[CoContravarianceDelegates#4](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#4)]
 [!code-vb[CoContravarianceDelegates#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#4)]  
  
 La dernière partie du code indique que le délégué peut être assigné à une variable de type `Func<Derived, Base>` (`Func(Of Derived, Base)` en Visual Basic), ce qui combine les effets du type de paramètre contravariant et du type de valeur de retour covariant.  
  
 [!code-csharp[CoContravarianceDelegates#5](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegates/cs/example.cs#5)]
 [!code-vb[CoContravarianceDelegates#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegates/vb/example.vb#5)]  
  
### <a name="variance-in-non-generic-delegates"></a>Variance dans les délégués non génériques

 Dans le code précédent, la signature de `MyMethod` correspond exactement à la signature du délégué générique construit : `Func<Base, Derived>` (`Func(Of Base, Derived)` en Visual Basic). L'exemple montre que ce délégué générique peut être stocké dans des variables ou des paramètres de méthode qui ont des types de paramètres plus dérivés et des types de retour moins dérivés, tant que tous les types délégués sont construits à partir du type délégué générique <xref:System.Func%602>.  
  
 Ceci est un point important. Les effets de la covariance et de la contravariance dans les paramètres de type des délégués génériques sont semblables aux effets de la covariance et de la contravariance dans la liaison de délégués ordinaire (consultez [Variance dans les délégués (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [Variance dans les délégués (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)). Toutefois, la variance dans la liaison de délégués fonctionne avec tous les types délégués, et pas seulement les types délégués génériques qui ont des paramètres de type variant. En outre, la variance dans la liaison de délégués permet de lier une méthode à tout délégué disposant de types de paramètres plus restrictifs et d'un type de retour moins restrictif, alors que l'assignation de délégués génériques fonctionne uniquement si les deux types délégués sont construits à partir de la même définition de type générique.  
  
 L'exemple suivant indique les effets combinés de la variance dans la liaison de délégués et de la variance dans les paramètres de type générique. L'exemple définit une hiérarchie de type qui inclut trois types, du moins dérivé (`Type1`) au plus dérivé (`Type3`). La variance dans la liaison de délégués ordinaire est utilisée pour lier une méthode avec le type de paramètre `Type1` et le type de retour `Type3` à un délégué générique avec le type de paramètre `Type2` et le type de retour `Type2`. Le délégué générique résultant est ensuite assigné à une autre variable dont le type délégué générique a un paramètre de type `Type3` et le type de retour `Type1`, à l'aide de la covariance et de la contravariance de paramètres de type générique. La deuxième assignation requiert que le type de variable et le type délégué soient construits à partir de la même définition de type générique, dans ce cas, <xref:System.Func%602>.  
  
 [!code-csharp[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/csharp/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/cs/example.cs#1)]
 [!code-vb[CoContravarianceDelegatesGenRelaxed#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/cocontravariancedelegatesgenrelaxed/vb/example.vb#1)]  

## <a name="define-variant-generic-interfaces-and-delegates"></a>Définir des interfaces et des délégués génériques de type Variant

Visual Basic et C# ont des mots clés qui vous permettent de marquer les paramètres de type générique des interfaces et des délégués comme covariants ou contravariant.
  
 Un paramètre de type covariant est marqué avec le `out` mot clé ( `Out` mot clé dans Visual Basic). Vous pouvez utiliser un paramètre de type covariant comme valeur de retour d'une méthode qui appartient à une interface ou comme type de retour d'un délégué. Vous ne pouvez pas utiliser un paramètre de type covariant comme contrainte de type générique pour les méthodes d'interface.  
  
> [!NOTE]
> Si une méthode d'une interface a un paramètre qui est un type délégué générique, un paramètre de type covariant du type d'interface peut être utilisé pour spécifier un paramètre de type contravariant du type délégué.  
  
 Un paramètre de type contravariant est marqué avec le `in` mot clé ( `In` mot clé dans Visual Basic). Vous pouvez utiliser un paramètre de type contravariant comme type d'un paramètre d'une méthode qui appartient à une interface ou comme type d'un paramètre d'un délégué. Vous pouvez utiliser un paramètre de type contravariant comme contrainte de type générique pour une méthode d'interface.  
  
 Seuls les types d'interfaces et les types délégués peuvent avoir des paramètres de type variant. Un type d'interface ou un type délégué peut avoir à la fois des paramètres de type covariant et contravariant.  
  
 Visual Basic et Visual C# ne vous permettent pas de violer les règles d'utilisation des paramètres de type covariant et contravariant ou d'ajouter des annotations de covariance et de contravariance aux paramètres qui diffèrent des types d'interfaces et des types délégués.
  
 Pour obtenir des informations et un exemple de code, consultez [Variance dans les interfaces génériques (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) et [Variance dans les interfaces génériques (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  

## <a name="list-of-types"></a>Liste de types

L’interface et les types délégués suivants ont des paramètres de type covariant et/ou contravariant.  
  
|Type|Paramètres de type covariant|Paramètres de type contravariant|  
|----------|-------------------------------|-----------------------------------|  
|Il lance <xref:System.Action%601> sur <xref:System.Action%6016>.||Oui|  
|<xref:System.Comparison%601>||Oui|  
|<xref:System.Converter%602>|Oui|Oui|  
|<xref:System.Func%601>|Oui||  
|Il lance <xref:System.Func%602> sur <xref:System.Func%6017>.|Oui|Oui|  
|<xref:System.IComparable%601>||Oui|  
|<xref:System.Predicate%601>||Oui|  
|<xref:System.Collections.Generic.IComparer%601>||Oui|  
|<xref:System.Collections.Generic.IEnumerable%601>|Oui||  
|<xref:System.Collections.Generic.IEnumerator%601>|Oui||  
|<xref:System.Collections.Generic.IEqualityComparer%601>||Oui|  
|<xref:System.Linq.IGrouping%602>|Oui||  
|<xref:System.Linq.IOrderedEnumerable%601>|Oui||  
|<xref:System.Linq.IOrderedQueryable%601>|Oui||  
|<xref:System.Linq.IQueryable%601>|Oui||  
  
## <a name="see-also"></a>Voir aussi

- [Covariance et contravariance (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/index.md)
- [Covariance et contravariance (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Variance dans les délégués (C#)](../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Variance dans les délégués (Visual Basic)](../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
