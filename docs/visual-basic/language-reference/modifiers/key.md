---
title: Clé
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 92c8809779d6cab524f67ee47f355b72ab152403
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351517"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
Le mot clé `Key` vous permet de spécifier le comportement des propriétés de types anonymes. Seules les propriétés que vous désignez en tant que propriétés de clé participent aux tests d’égalité entre les instances de type anonyme ou le calcul des valeurs de code de hachage. Les valeurs des propriétés de clé ne peuvent pas être modifiées.  
  
 Vous désignez une propriété d’un type anonyme en tant que propriété de clé en plaçant le mot clé `Key` devant sa déclaration dans la liste d’initialisation. Dans l’exemple suivant, `Airline` et `FlightNo` sont des propriétés de clé, mais `Gate` ne l’est pas.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 Lorsqu’un nouveau type anonyme est créé, il hérite directement de <xref:System.Object>. Le compilateur remplace trois membres hérités : <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>et <xref:System.Object.ToString%2A>. Le code de substitution produit pour <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> est basé sur les propriétés de clé. S’il n’existe aucune propriété de clé dans le type, <xref:System.Object.GetHashCode%2A> et <xref:System.Object.Equals%2A> ne sont pas substitués.  
  
## <a name="equality"></a>Égalité  
 Deux instances de type anonyme sont égales si elles sont des instances du même type et si les valeurs de leurs propriétés de clé sont égales. Dans les exemples suivants, `flight2` est égal à `flight1` de l’exemple précédent parce qu’il s’agit d’instances du même type anonyme et qu’elles ont des valeurs correspondantes pour leurs propriétés de clé. Toutefois, `flight3` n’est pas égal à `flight1`, car elle a une valeur différente pour une propriété de clé, `FlightNo`. L' `flight4` d’instance n’est pas du même type que `flight1`, car ils désignent des propriétés différentes en tant que propriétés de clé.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 Si deux instances sont déclarées avec uniquement des propriétés non-clés, identiques dans le nom, le type, l’ordre et la valeur, les deux instances ne sont pas égales. Une instance sans propriétés de clé est uniquement égale à elle-même.  
  
 Pour plus d’informations sur les conditions dans lesquelles deux instances de type anonyme sont des instances du même type anonyme, consultez [types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Calcul du code de hachage  
 Comme <xref:System.Object.Equals%2A>, la fonction de hachage définie dans <xref:System.Object.GetHashCode%2A> pour un type anonyme est basée sur les propriétés de clé du type. Les exemples suivants illustrent l’interaction entre les propriétés de clé et les valeurs de code de hachage.  
  
 Les instances d’un type anonyme qui ont les mêmes valeurs pour toutes les propriétés de clé ont la même valeur de code de hachage, même si les propriétés non-clés n’ont pas de valeurs correspondantes. L’instruction suivante retourne `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 Les instances d’un type anonyme qui ont des valeurs différentes pour une ou plusieurs propriétés de clé ont des valeurs de code de hachage différentes. L’instruction suivante retourne `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 Les instances de types anonymes qui désignent des propriétés différentes en tant que propriétés de clé ne sont pas des instances du même type. Elles ont des valeurs de code de hachage différentes, même lorsque les noms et les valeurs de toutes les propriétés sont identiques. L’instruction suivante retourne `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>Valeurs en lecture seule  
 Les valeurs des propriétés de clé ne peuvent pas être modifiées. Par exemple, dans `flight1` dans les exemples précédents, les champs `Airline` et `FlightNo` sont en lecture seule, mais `Gate` peuvent être modifiés.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>Voir aussi

- [Définition du type anonyme](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Guide pratique : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
