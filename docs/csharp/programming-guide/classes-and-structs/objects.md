---
title: Objets - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: a2f5300f9647823cf2c9ac2a4a5c7c888c7dd245
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626579"
---
# <a name="objects-c-programming-guide"></a>Objets (Guide de programmation C#)
Une définition de classe ou de struct s’apparente à un plan qui spécifie ce que le type peut faire. Un objet est fondamentalement un bloc de mémoire qui a été alloué et configuré selon le plan. Un programme peut créer de nombreux objets de la même classe. Les objets sont également appelés instances. Ils peuvent être stockés dans une variable nommée, dans un tableau ou dans une collection. Le code client est le code qui utilise ces variables pour appeler les méthodes et accéder aux propriétés publiques de l’objet. Dans un langage orienté objet tel que C#, un programme classique se compose de plusieurs objets qui interagissent de façon dynamique.  
  
> [!NOTE]
> Les types statiques se comportent différemment de ce qui est décrit ici. Pour plus d’informations, consultez [Classes statiques et membres de classe statique](./static-classes-and-static-class-members.md).
  
## <a name="struct-instances-vs-class-instances"></a>Instances struct et instances de classe  
 Étant donné que les classes sont des types référence, une variable d’un objet de classe conserve une référence à l’adresse de l’objet sur le tas managé. Si un deuxième objet du même type est assigné au premier objet, les deux variables font référence à l’objet à cette adresse. Ce point est abordé en détail plus loin dans cette rubrique.  
  
 Les instances de classes sont créées à l’aide de l’[opérateur new](../../language-reference/operators/new-operator.md). Dans l’exemple suivant, `Person` est le type, et `person1` et `person 2` sont des instances, ou objets, de ce type.  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 Étant donné que les structs sont des types valeur, une variable d’un objet de struct conserve une copie de l’objet entier. Les instances de structs peuvent également être créées à l’aide de l’opérateur `new`, mais cela n’est pas obligatoire, comme illustré dans l’exemple suivant :  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 La mémoire pour `p1` et `p2` est allouée sur la pile de threads. Cette mémoire est récupérée avec le type ou la méthode où elle est déclarée. C’est l’une des raisons pour lesquelles les structs sont copiés au moment de l’assignation. En revanche, la mémoire allouée pour une instance de classe est récupérée automatiquement (garbage collection) par le common language runtime quand toutes les références à l’objet sont hors de la portée. Il n’est pas possible de détruire de façon déterministe un objet de classe comme vous pouvez le faire dans C++. Pour plus d’informations sur l’opération de garbage collection dans le .NET Framework, consultez [Garbage collection](../../../standard/garbage-collection/index.md).  
  
> [!NOTE]
> L’allocation et la libération de mémoire sur le tas managé sont des opérations très optimisées dans le common language runtime. Dans la plupart des cas, il n’y a pas de différence significative sur le plan des performances entre l’allocation d’une instance de classe sur le tas et l’allocation d’une instance de struct sur la pile.
  
## <a name="object-identity-vs-value-equality"></a>Identité de l’objet et égalité de la valeur  
 Quand vous effectuez une comparaison d’égalité entre deux objets, vous devez d’abord décider si vous souhaitez savoir si les deux variables représentent le même objet en mémoire, ou si les valeurs d’un ou de plusieurs de leurs champs sont équivalentes. Si vous projetez de comparer les valeurs, vous devez établir si les objets sont des instances de types valeur (structs) ou de types référence (classes, délégués, tableaux).  
  
- Pour déterminer si deux instances de classe référencent le même emplacement en mémoire (ce qui signifie qu’elles ont la même *identité*), utilisez la méthode statique <xref:System.Object.Equals%2A>. (<xref:System.Object?displayProperty=nameWithType> est la classe de base implicite pour tous les types valeur et types référence, y compris les classes et structs définis par l’utilisateur.)  
  
- Pour déterminer si les champs d’instance dans deux instances de struct ont les mêmes valeurs, utilisez la méthode <xref:System.ValueType.Equals%2A?displayProperty=nameWithType>. Comme tous les structs héritent implicitement de <xref:System.ValueType?displayProperty=nameWithType>, vous appelez directement la méthode sur votre objet, comme indiqué dans l’exemple suivant :  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 L’implémentation <xref:System.ValueType?displayProperty=nameWithType> de `Equals` utilise la réflexion, car elle doit être en mesure de déterminer la nature des champs dans chaque struct. Quand vous créez vos propres structs, substituez la méthode `Equals` pour fournir un algorithme d’égalité efficace qui est propre à votre type.  
  
- Pour déterminer si les valeurs des champs dans deux instances de classe sont égales, vous pouvez utiliser la méthode <xref:System.Object.Equals%2A> ou l’[opérateur ==](../../language-reference/operators/equality-operators.md#equality-operator-). Toutefois, utilisez-les uniquement si la classe les a substitués ou surchargés pour fournir une définition personnalisée de ce que signifie « égalité » pour les objets de ce type. La classe peut également implémenter l’interface <xref:System.IEquatable%601> ou <xref:System.Collections.Generic.IEqualityComparer%601>. Les deux interfaces fournissent des méthodes qui peuvent être utilisées pour tester l’égalité des valeurs. Quand vous concevez vos propres classes qui substituent `Equals`, veillez à suivre les instructions indiquées dans [comment définir l’égalité des valeurs pour un type](../statements-expressions-operators/how-to-define-value-equality-for-a-type.md) et <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.
  
## <a name="related-sections"></a>Sections connexes  
 Pour plus d'informations :  
  
- [Classes](./classes.md)  
  
- [Structures](./structs.md)  
  
- [Constructeurs](./constructors.md)  
  
- [Finaliseurs](./destructors.md)  
  
- [Événements](../events/index.md)  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [object](../../language-reference/builtin-types/reference-types.md)
- [Héritage](./inheritance.md)
- [class](../../language-reference/keywords/class.md)
- [struct](../../language-reference/builtin-types/struct.md)
- [Opérateur new](../../language-reference/operators/new-operator.md)
- [Système de type commun](../../../standard/base-types/common-type-system.md)
