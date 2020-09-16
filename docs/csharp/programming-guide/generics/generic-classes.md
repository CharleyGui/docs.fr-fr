---
title: Classes génériques - Guide de programmation C#
description: Découvrez les classes génériques utilisées dans les collections telles que les listes liées, les tables de hachage, les piles, les files d’attente et les arborescences.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic classes
- generics [C#], classes
ms.assetid: 27d6f256-cd61-41e3-bc6e-b990a53b0224
ms.openlocfilehash: a885ae042eef939021d3a9b75616505c289bd43c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558085"
---
# <a name="generic-classes-c-programming-guide"></a>Classes génériques (guide de programmation C#)
Les classes génériques encapsulent des opérations qui ne sont pas spécifiques à un type de données particulier. Les classes génériques sont le plus souvent utilisées avec les collections telles que les listes liées, les tables de hachage, les piles, les files d’attente, les arborescences, etc. Les opérations telles que l’ajout et la suppression d’éléments dans la collection sont exécutées fondamentalement de la même manière quel que soit le type des données stockées.  
  
 Pour la plupart des scénarios qui nécessitent des classes de collections, l’approche recommandée consiste à utiliser celles fournies dans la bibliothèque de classes .NET. Pour plus d’informations sur l’utilisation de ces classes, consultez [Collections génériques dans .NET](../../../standard/generics/collections.md).  
  
 En général, vous créez des classes génériques en commençant par une classe concrète existante et en changeant des types en paramètres de type individuellement jusqu’à ce que vous atteigniez l’équilibre optimal au niveau de la généralisation et de la facilité d’utilisation. Lors de la création de vos propres classes génériques, les aspects importants à prendre en considération sont notamment les suivants :  
  
- Quels types généraliser en paramètres de type.  
  
     En règle générale, plus le nombre de types que vous pouvez paramétrer est important, plus votre code est souple et réutilisable. Toutefois, une généralisation excessive peut produire un code qui est difficile à lire ou à comprendre par d’autres développeurs.  
  
- Quelles contraintes, le cas échéant, appliquer aux paramètres de type (consultez [Contraintes sur les paramètres de type](./constraints-on-type-parameters.md)).  
  
     Il est pertinent d’appliquer le maximum de contraintes possible vous permettant néanmoins de gérer les types que vous devez gérer. Par exemple, si vous savez que votre classe générique est destinée uniquement à être utilisée avec les types référence, appliquez la contrainte de classe. Cela empêchera l’utilisation involontaire de votre classe avec les types valeur et vous permettra d’utiliser l’opérateur `as` sur `T` et de rechercher les valeurs nulles.  
  
- S’il convient de prendre en compte le comportement générique dans les sous-classes et les classes de base.  
  
     Les classes génériques pouvant servir de classes de base, les considérations de conception qui s’appliquent ici sont les mêmes que pour les classes non génériques. Consultez les règles relatives à l’héritage à partir des classes de base génériques plus loin dans cette rubrique.  
  
- S’il convient d’implémenter une ou plusieurs interfaces génériques.  
  
     Par exemple, si vous concevez une classe qui sera utilisée pour créer des éléments dans une collection basée sur les génériques, vous pouvez avoir besoin d’implémenter une interface comme <xref:System.IComparable%601>, où `T` est le type de votre classe.  
  
 Pour obtenir un exemple d’une classe générique simple, consultez [Introduction aux génériques](./index.md).  
  
 Les règles pour les paramètres de type et les contraintes ont plusieurs conséquences sur le comportement de classe générique, surtout en ce qui concerne l’héritage et l’accessibilité des membres. Avant de continuer, vous devez comprendre quelques termes. Pour une classe générique `Node<T>,`, le code client peut référencer la classe soit en spécifiant un argument de type, pour créer un type construit fermé (`Node<int>`), soit en laissant le paramètre de type non spécifié, par exemple quand vous spécifiez une classe de base générique, pour créer un type construit ouvert (`Node<T>`). Les classes génériques peuvent hériter de classes de base concrètes, construites fermées ou construites ouvertes :  
  
 [!code-csharp[csProgGuideGenerics#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#16)]  
  
 Les classes non génériques, également appelées concrètes, peuvent hériter des classes de base construites fermées, mais pas des classes construites ouvertes ni des paramètres de type parce que le code client ne peut en aucune façon fournir au moment de l’exécution l’argument de type requis pour instancier la classe de base.  
  
 [!code-csharp[csProgGuideGenerics#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#17)]  
  
 Les classes génériques qui héritent de types construits ouverts doivent fournir des arguments de type pour tout paramètre de type de classe de base qui n’est pas partagé par la classe qui hérite, comme cela est indiqué dans le code suivant :  
  
 [!code-csharp[csProgGuideGenerics#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#18)]  
  
 Les classes génériques qui héritent des types construits ouverts doivent spécifier des contraintes qui sont un sur-ensemble, ou qui impliquent, des contraintes sur le type de base :  
  
 [!code-csharp[csProgGuideGenerics#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#19)]  
  
 Les types génériques peuvent utiliser plusieurs paramètres de type et contraintes, comme suit :  
  
 [!code-csharp[csProgGuideGenerics#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#20)]  
  
 Les types construits ouverts et les types construits fermés peuvent être utilisés comme paramètres de méthode :  
  
 [!code-csharp[csProgGuideGenerics#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#21)]  
  
 Si une classe générique implémente une interface, toutes les instances de cette classe peuvent être castées à cette interface.  
  
 Les classes génériques sont indifférentes. En d’autres termes, si un paramètre d’entrée spécifie un `List<BaseClass>`, vous obtiendrez une erreur de compilation si vous essayez de fournir un `List<DerivedClass>`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic>
- [Guide de programmation C#](../index.md)
- [Génériques](./index.md)
- [Enregistrement de l’état des énumérateurs](/archive/blogs/wesdyer/saving-the-state-of-enumerators)
- [An Inheritance Puzzle, Part One](/archive/blogs/ericlippert/an-inheritance-puzzle-part-one)
