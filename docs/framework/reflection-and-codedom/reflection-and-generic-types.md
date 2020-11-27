---
title: Réflexion et types génériques
description: Prise en main de la réflexion et des types génériques dans .NET. Contrairement à un type ordinaire, un type générique est associé à un ensemble de paramètres de type ou d’arguments de type.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic types
- reflection, generic types
- type arguments
- generics [.NET Framework], reflection
- viewing type information
- type information, viewing
- types, generic
- type parameters
ms.assetid: f7180fc5-dd41-42d4-8a8e-1b34288e06de
ms.openlocfilehash: 2add589d171163d5497e80ed7b7990c3596add20
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259913"
---
# <a name="reflection-and-generic-types"></a>Réflexion et types génériques

Du point de vue de la réflexion, la différence entre un type générique et un type ordinaire est qu'un type générique est associé à un ensemble de paramètres de type (s'il s'agit d'une définition de type générique) ou d'arguments de type (s'il s'agit d'un type construit). Une méthode générique diffère d'une méthode ordinaire de la même façon.  
  
 Deux éléments essentiels permettent de comprendre comment la réflexion gère les types et méthodes génériques :  
  
- Les paramètres de type des définitions de type générique et des définitions de méthode générique sont représentés par des instances de la classe <xref:System.Type> .  
  
    > [!NOTE]
    > De nombreuses propriétés et méthodes de <xref:System.Type> ont un comportement différent quand un objet <xref:System.Type> représente un paramètre de type générique. Ces différences sont documentées dans les rubriques de la propriété et de la méthode. Par exemple, consultez <xref:System.Type.IsAutoClass%2A> et <xref:System.Type.DeclaringType%2A>. Par ailleurs, certains membres sont valides uniquement quand un objet <xref:System.Type> représente un paramètre de type générique. Par exemple, consultez <xref:System.Type.GetGenericTypeDefinition%2A>.  
  
- Si une instance de <xref:System.Type> représente un type générique, elle inclut un tableau de types qui représentent les paramètres de type (pour les définitions de type générique) ou les arguments de type (pour les types construits). Il en est de même d'une instance de la classe <xref:System.Reflection.MethodInfo> qui représente une méthode générique.  
  
 La réflexion fournit des méthodes de <xref:System.Type> et <xref:System.Reflection.MethodInfo> qui permettent d'accéder au tableau des paramètres de type et de déterminer si une instance de <xref:System.Type> représente un paramètre de type ou un type réel.  
  
 Pour obtenir un exemple de code illustrant les méthodes présentées ici, consultez [Guide pratique pour examiner et instancier des types génériques avec la réflexion](how-to-examine-and-instantiate-generic-types-with-reflection.md).  
  
 La discussion suivante suppose que vous connaissez la terminologie des génériques, par exemple, la différence entre les paramètres et les arguments de type et entre les types construits ouverts ou fermés. Pour plus d’informations, consultez [Génériques](../../standard/generics/index.md).  

## <a name="is-this-a-generic-type-or-method"></a>S'agit-il d'un type ou d'une méthode générique ?  

 Quand vous utilisez la réflexion pour examiner un type inconnu, représenté par une instance de <xref:System.Type>, utilisez la propriété <xref:System.Type.IsGenericType%2A> pour déterminer si le type inconnu est générique. Elle retourne `true` si le type est générique. De la même façon, quand vous examiner une méthode inconnue, représentée par une instance de la classe <xref:System.Reflection.MethodInfo> , utilisez la propriété <xref:System.Reflection.MethodBase.IsGenericMethod%2A> pour déterminer si la méthode est générique.  
  
### <a name="is-this-a-generic-type-or-method-definition"></a>S'agit-il d'une définition de type ou de méthode générique ?  

 Utilisez la propriété <xref:System.Type.IsGenericTypeDefinition%2A> pour déterminer si un objet <xref:System.Type> représente une définition de type générique et utilisez la méthode <xref:System.Reflection.MethodBase.IsGenericMethodDefinition%2A> pour déterminer si un <xref:System.Reflection.MethodInfo> représente une définition de méthode générique.  
  
 Les définitions de type et de méthode génériques sont les modèles à partir desquels les types instanciables sont créés. Les types génériques dans la bibliothèque de classes .NET Framework, tels que <xref:System.Collections.Generic.Dictionary%602>, sont des définitions de type générique.  
  
### <a name="is-the-type-or-method-open-or-closed"></a>Le type ou la méthode est-il ouvert ou fermé ?  

 Un type ou une méthode générique est fermé si des types instanciables ont été substitués à tous ses paramètres de type, y compris tous les paramètres de type de tous les types englobants. Vous pouvez uniquement créer une instance d'un type générique s'il est fermé. La propriété <xref:System.Type.ContainsGenericParameters%2A?displayProperty=nameWithType> renvoie `true` si un type est ouvert. Pour les méthodes, la méthode <xref:System.Reflection.MethodBase.ContainsGenericParameters%2A?displayProperty=nameWithType> a la même fonction.

## <a name="generating-closed-generic-types"></a>Génération de types génériques fermés  

 Une fois que vous avez une définition de type ou méthode générique, utilisez la méthode <xref:System.Type.MakeGenericType%2A> pour créer un type générique fermé ou la méthode <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> pour créer un <xref:System.Reflection.MethodInfo> pour une méthode générique fermée.  
  
### <a name="getting-the-generic-type-or-method-definition"></a>Obtention d'une définition de type ou de méthode générique  

 Si vous avez un type ou une méthode générique ouvert qui n'est pas une définition de type ou méthode générique, vous ne pouvez pas créer d'instances de ce type et vous ne pouvez pas fournir les paramètres de type manquants. Vous devez avoir une définition de type ou de méthode générique. Utilisez la méthode <xref:System.Type.GetGenericTypeDefinition%2A> pour obtenir la définition de type générique ou la méthode <xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A> pour obtenir la définition de méthode générique.  
  
 Par exemple, si vous avez un objet <xref:System.Type> représentant `Dictionary<int, string>` (`Dictionary(Of Integer, String)` en Visual Basic) et que vous voulez créer le type `Dictionary<string, MyClass>`, vous pouvez utiliser la méthode <xref:System.Type.GetGenericTypeDefinition%2A> pour obtenir un <xref:System.Type> représentant `Dictionary<TKey, TValue>` , puis utiliser la méthode <xref:System.Type.MakeGenericType%2A> pour produire un <xref:System.Type> représentant `Dictionary<int, MyClass>`.  
  
 Pour obtenir un exemple de type générique ouvert qui n'est pas un type générique, consultez « Paramètre de type ou argument de type » plus loin dans cette rubrique.

## <a name="examining-type-arguments-and-type-parameters"></a>Examen des arguments de type et des paramètres de type  

 Utilisez la méthode <xref:System.Type.GetGenericArguments%2A?displayProperty=nameWithType> pour obtenir un tableau d'objets <xref:System.Type> qui représentent les paramètres ou les arguments de type d'un type générique, et utilisez la méthode <xref:System.Reflection.MethodInfo.GetGenericArguments%2A?displayProperty=nameWithType> pour faire de même pour une méthode générique.  
  
 Dès que vous savez qu'un objet <xref:System.Type> représente un paramètre de type, la réflexion peut répondre à de nombreuses autres questions. Vous pouvez déterminer la source du paramètre de type, sa position et ses contraintes.  
  
### <a name="type-parameter-or-type-argument"></a>Paramètre de type ou argument de type  

 Pour déterminer si un élément particulier du tableau est un paramètre ou un argument de type, utilisez la propriété <xref:System.Type.IsGenericParameter%2A> . La propriété <xref:System.Type.IsGenericParameter%2A> a la valeur `true` si l'élément est un paramètre de type.  
  
 Un type générique peut être ouvert sans être une définition de type générique, dans ce cas, il comprend un mélange d'arguments de type et de paramètres de type. Par exemple, dans le code suivant, la classe `D` dérive d'un type créé en substituant le premier paramètre de type `D` au deuxième paramètre de type `B`.  
  
```csharp  
class B<T, U> {}  
class D<V, W> : B<int, V> {}  
```  
  
```vb  
Class B(Of T, U)  
End Class  
Class D(Of V, W)  
    Inherits B(Of Integer, V)  
End Class  
```  
  
```cpp  
generic<typename T, typename U> ref class B {};  
generic<typename V, typename W> ref class D : B<int, V> {};  
```  
  
 Si vous obtenez un objet <xref:System.Type> représentant `D<V, W>` et utilisez la propriété <xref:System.Type.BaseType%2A> pour obtenir son type de base, le `type B<int, V>` résultant est ouvert, mais n'est pas une définition de type générique.  
  
### <a name="source-of-a-generic-parameter"></a>Source d'un paramètre générique  

 Un paramètre de type générique peut provenir du type que vous examinez, d'un type englobant ou d'une méthode générique. Vous pouvez déterminer la source du paramètre de type générique comme suit :  
  
- Tout d'abord, utilisez la propriété <xref:System.Type.DeclaringMethod%2A> pour déterminer si le paramètre de type vient d'une méthode générique. Si la valeur de propriété n'est pas une référence null (`Nothing` en Visual Basic), la source est une méthode générique.  
  
- Si la source n'est pas une méthode générique, utilisez la propriété <xref:System.Type.DeclaringType%2A> pour déterminer le type générique auquel appartient le paramètre de type générique.  
  
 Si le paramètre de type appartient à une méthode générique, la propriété <xref:System.Type.DeclaringType%2A> retourne le type qui a déclaré la méthode générique, ce qui n'est pas pertinent.  
  
### <a name="position-of-a-generic-parameter"></a>Position d'un paramètre générique  

 Dans de rares cas, il est nécessaire de déterminer la position d'un paramètre de type dans la liste de paramètres de type de la classe de déclaration. Par exemple, supposons que vous ayez un objet <xref:System.Type> représentant le type `B<int, V>` de l'exemple précédent. La méthode <xref:System.Type.GetGenericArguments%2A> vous donne la liste des arguments de type et, quand vous examinez `V` , vous pouvez utiliser les propriétés <xref:System.Type.DeclaringMethod%2A> et <xref:System.Type.DeclaringType%2A> pour découvrir d'où il vient. Vous pouvez ensuite utiliser la propriété <xref:System.Type.GenericParameterPosition%2A> afin de déterminer sa position dans la liste de paramètres de type dans laquelle il a été défini. Dans cet exemple, `V` se trouve à la position 0 (zéro) dans la liste de paramètres de type dans laquelle il a été défini.  
  
### <a name="base-type-and-interface-constraints"></a>Type de base et contraintes d'interface  

 Utilisez la méthode <xref:System.Type.GetGenericParameterConstraints%2A> pour obtenir la contrainte de type de base et les contraintes d'interface d'un paramètre de type. L'ordre des éléments du tableau n'est pas significatif. Un élément représente une contrainte d'interface s'il s'agit d'un type d'interface.  
  
### <a name="generic-parameter-attributes"></a>Attributs du paramètre générique  

 La propriété <xref:System.Type.GenericParameterAttributes%2A> obtient une valeur <xref:System.Reflection.GenericParameterAttributes> qui indique l'écart (covariance ou contravariance) et les contraintes spéciales d'un paramètre de type.  
  
#### <a name="covariance-and-contravariance"></a>Covariance et contravariance  

 Pour déterminer si un paramètre de type est covariant ou contravariant, appliquez le masque <xref:System.Reflection.GenericParameterAttributes.VarianceMask?displayProperty=nameWithType> à la valeur <xref:System.Reflection.GenericParameterAttributes> retournée par la propriété <xref:System.Type.GenericParameterAttributes%2A> . Si le résultat est <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, le paramètre de type est invariant. Consultez [Covariance et contravariance](../../standard/generics/covariance-and-contravariance.md).  
  
#### <a name="special-constraints"></a>Contraintes spéciales  

 Pour déterminer les contraintes spéciales d'un paramètre de type, appliquez le masque <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> à la valeur <xref:System.Reflection.GenericParameterAttributes> retournée par la propriété <xref:System.Type.GenericParameterAttributes%2A> . Si le résultat est <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>, il n'y a aucune contrainte spéciale. Un paramètre de type peut être contraint à être un type de référence, un type de valeur qui n'autorise pas les valeurs null et à avoir un constructeur sans paramètre.

## <a name="invariants"></a>Invariants  

 Pour obtenir un tableau des conditions invariantes pour les termes courants dans la réflexion pour les types génériques, consultez <xref:System.Type.IsGenericType%2A?displayProperty=nameWithType>. Pour obtenir des termes supplémentaires relatifs aux méthodes génériques, consultez <xref:System.Reflection.MethodBase.IsGenericMethod%2A?displayProperty=nameWithType>.  

## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Guide pratique pour examiner et instancier des types génériques avec la réflexion](how-to-examine-and-instantiate-generic-types-with-reflection.md)|Montre comment utiliser les propriétés et méthodes de <xref:System.Type> et <xref:System.Reflection.MethodInfo> pour examiner des types génériques.|  
|[Génériques](../../standard/generics/index.md)|Décrit la fonctionnalité des génériques et sa prise en charge dans le .NET Framework.|  
|[Procédure : définir un type générique avec l’émission de réflexion](how-to-define-a-generic-type-with-reflection-emit.md)|Montre comment utiliser l'émission de réflexion pour générer des types génériques dans des assemblys dynamiques.|  
|[Affichage des informations de type](viewing-type-information.md)|Décrit la classe <xref:System.Type> et fournit des exemples de code qui montrent comment utiliser <xref:System.Type> avec diverses classes de réflexion pour obtenir des informations sur les constructeurs, les méthodes, les champs, les propriétés et les événements.|
