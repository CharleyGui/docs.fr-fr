---
title: Utilisation de structs - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 0e0ba1602468d1bcc38985c78e1af5e4d2a5912c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586084"
---
# <a name="using-structs-c-programming-guide"></a>Utilisation de structs (Guide de programmation C#)
Le type `struct` est approprié pour représenter des objets légers tels que `Point`, `Rectangle`et `Color`. Bien qu’il soit aussi pratique de représenter un point comme [classe](../../../csharp/language-reference/keywords/class.md) avec des [propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), un [struct](../../../csharp/language-reference/keywords/struct.md) peut être plus efficace dans certains scénarios. Par exemple, si vous déclarez un tableau de 1 000 objets `Point` , vous devez allouer de la mémoire supplémentaire pour faire référence à chacun des objets. Dans ce cas, un struct est moins onéreux. Étant donné que le .NET Framework contient un objet nommé <xref:System.Drawing.Point>, le struct utilisé dans cet exemple est nommé « Coords » à la place.  
  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 Définir un constructeur par défaut (sans paramètre) pour un struct constitue une erreur. Vous ne devez pas non plus initialiser un champ d'instance dans le corps d'un struct. Vous pouvez initialiser des membres de struct accessibles en externe uniquement en utilisant un constructeur paramétrable, le constructeur sans paramètre implicite ou un [initialiseur d’objet](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md), ou en accédant individuellement aux membres après la déclaration du struct. Tout membre privé ou inaccessible nécessite exclusivement l’utilisation de constructeurs.
  
 Quand vous créez un objet struct avec l’opérateur [new](../../../csharp/language-reference/keywords/new.md), cet objet est créé et le constructeur approprié est appelé conformément à la [signature du constructeur](../../../csharp/programming-guide/classes-and-structs/constructors.md#constructor-syntax). Contrairement aux classes, les structs peuvent être instanciés sans avoir recours à l’opérateur `new` . Dans un tel cas, il n’y a pas d’appel au constructeur, ce qui rend l’allocation plus efficace. Toutefois, les champs ne sont pas assignés et l’objet ne peut pas être utilisé tant que tous les champs ne sont pas initialisés. Ceci inclut l’incapacité à récupérer ou à définir des valeurs au moyen de propriétés.
 
 Si vous instanciez un objet struct avec le constructeur sans paramètre (la façon de l’instancier par défaut), tous les membres sont affectés en fonction de leur [valeur par défaut](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md).
  
 Quand vous écrivez un constructeur avec des paramètres pour un struct, vous devez explicitement initialiser tous les membres ; sinon, un ou plusieurs membres restent non affectés et le struct ne peut pas être utilisé, produisant l’erreur du compilateur CS0171.  
  
 Il n'existe pas d'héritage pour un struct comme il en existe pour une classe. Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe. Toutefois, les structs héritent de la classe de base <xref:System.Object>. Un struct peut implémenter des interfaces exactement de la même manière que les classes.  
  
 Vous ne pouvez pas déclarer une classe à l’aide du mot clé `struct`. En C#, les classes et les structs ont une sémantique différente. Un struct est un type valeur, alors qu'une classe est un type référence. Pour plus d’informations, consultez [Types valeur](../../../csharp/language-reference/keywords/value-types.md).  
  
 Sauf si vous avez besoin d’une sémantique de type référence, une petite classe peut être gérée plus efficacement par le système si vous la déclarez plutôt sous forme de struct.  
  
## <a name="example-1"></a>Exemple 1  
  
### <a name="description"></a>Description  
 Cet exemple illustre l’initialisation du type `struct` à l’aide des constructeurs par défaut et des constructeurs paramétrables.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]  
  
## <a name="example-2"></a>Exemple 2  
  
### <a name="description"></a>Description  
 Cet exemple montre une caractéristique propre aux structs. Il crée un objet Coords sans utiliser l’opérateur `new`. Si vous remplacez le mot `struct` par le mot `class`, le programme ne peut pas se compiler.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]  
  
 [!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
- [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md)
