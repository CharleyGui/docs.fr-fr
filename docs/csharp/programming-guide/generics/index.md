---
title: Génériques - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: e32eb7c60e01ca72824ffb3a1e1269cf34650f5a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423401"
---
# <a name="generics-c-programming-guide"></a>Génériques (guide de programmation C#)
Les génériques ont été ajoutés à la version 2.0 du langage C# et du Common Language Runtime (CLR). Les génériques introduisent le concept des paramètres de type dans .NET Framework, qui permettent de concevoir des classes et des méthodes qui diffèrent la spécification d’un ou de plusieurs types jusqu’à ce que la classe ou la méthode soit déclarée et instanciée par le code client. Par exemple, à l’aide d’un paramètre de type générique T, vous pouvez écrire une seule classe qui peut être utilisée par un autre code client sans impliquer le coût ou le risque des casts ou des opérations de boxing à l’exécution, comme illustré ici :  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

Les méthodes et les classes génériques combinent la réutilisabilité, la cohérence des types et l’efficacité, ce que ne peuvent pas faire leurs équivalents non génériques. Les génériques sont plus fréquemment utilisés dans des collections et des méthodes qui agissent sur eux. La version 2.0 de la bibliothèque de classes .NET Framework fournit un nouvel espace de noms, <xref:System.Collections.Generic>, qui contient plusieurs nouvelles classes de collection génériques. Pour toutes les applications qui ciblent le .NET Framework version 2.0 et ultérieures, il est recommandé d’utiliser les nouvelles classes de collection génériques plutôt que leurs équivalents non génériques, tels que <xref:System.Collections.ArrayList>. Pour plus d’informations, consultez [Génériques en .NET](../../../standard/generics/index.md).  
  
 Bien sûr, vous pouvez également créer des types et des méthodes génériques personnalisés pour fournir des solutions et des modèles de conception généralisés qui soient efficaces et de type sécurisé. L’exemple de code suivant montre une classe de liste liée générique simple, à des fins de démonstration. Dans la plupart des cas, vous aurez tout intérêt à utiliser la classe <xref:System.Collections.Generic.List%601> fournie par la bibliothèque de classes .NET Framework plutôt que de créer la vôtre. Le paramètre de type `T` est utilisé dans plusieurs emplacements où un type concret est normalement utilisé pour indiquer le type de l’élément stocké dans la liste. Il est utilisé de la façon suivante :  
  
- Comme le type d’un paramètre de méthode dans la méthode`AddHead`.  
  
- Comme le type de retour de la propriété `Data` de la classe imbriquée `Node`.  
  
- Comme le type de membre privé `data` de la classe imbriquée.  
  
 Notez que T est disponible pour la classe imbriquée `Node`. Quand `GenericList<T>` est instancié avec un type concret, par exemple comme un `GenericList<int>`, chaque occurrence de `T` est remplacée par `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 L’exemple de code suivant montre comment le code client utilise la classe générique `GenericList<T>` pour créer une liste d’entiers. En changeant l’argument de type, vous pouvez facilement modifier le code suivant pour créer des listes de chaînes ou tout autre type personnalisé :  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a>Vue d’ensemble des génériques  
  
- Utilisez des types génériques pour optimiser la réutilisation de code, la sécurité des types et les performances.  
  
- L’utilisation la plus courante des génériques est de créer des classes de collection.  
  
- La bibliothèque de classes du .NET Framework contient plusieurs nouvelles classes de collection génériques dans l’espace de noms <xref:System.Collections.Generic>. Celles-ci doivent être utilisées chaque fois que c’est possible, à la place de classes comme <xref:System.Collections.ArrayList> dans l’espace de noms <xref:System.Collections>.  
  
- Vous pouvez créer vos propres interfaces, classes, méthodes, événements et délégués génériques.  
  
- Les classes génériques peuvent être contraintes pour permettre l’accès à des méthodes sur des types de données particuliers.  
  
- Des informations sur les types qui sont utilisés dans un type de données générique peuvent être obtenues à l’exécution à l’aide de la réflexion.  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations :  
  
- [Paramètres de type générique](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
- [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
- [Classes génériques](../../../csharp/programming-guide/generics/generic-classes.md)  
  
- [Interfaces génériques](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
- [Méthodes génériques](../../../csharp/programming-guide/generics/generic-methods.md)  
  
- [Délégués génériques](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
- [Différences entre les modèles C++ et les génériques C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
- [Génériques et réflexion](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
- [Génériques dans le runtime](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 Pour plus d'informations, voir la [spécification du langage C#](~/_csharplang/spec/types.md#constructed-types).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic>
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Types](../../../csharp/programming-guide/types/index.md)
- [\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [Génériques en .NET](../../../standard/generics/index.md)
