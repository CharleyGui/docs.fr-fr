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
ms.openlocfilehash: 5b060f5fa0042dfb8ffa6876f5e172d3bcda67a3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396218"
---
# <a name="key-visual-basic"></a>Key (Visual Basic)
Le `Key` mot clé vous permet de spécifier le comportement des propriétés de types anonymes. Seules les propriétés que vous désignez en tant que propriétés de clé participent aux tests d’égalité entre les instances de type anonyme ou le calcul des valeurs de code de hachage. Les valeurs des propriétés de clé ne peuvent pas être modifiées.  
  
 Vous désignez une propriété d’un type anonyme en tant que propriété de clé en plaçant le mot clé `Key` devant sa déclaration dans la liste d’initialisation. Dans l’exemple suivant, `Airline` et `FlightNo` sont des propriétés de clé, mais `Gate` pas.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 Lorsqu’un nouveau type anonyme est créé, il hérite directement de <xref:System.Object> . Le compilateur remplace trois membres hérités : <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> et <xref:System.Object.ToString%2A> . Le code de substitution produit pour <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> est basé sur les propriétés de clé. S’il n’y a aucune propriété de clé dans le type <xref:System.Object.GetHashCode%2A> et n' <xref:System.Object.Equals%2A> est pas substitué.  
  
## <a name="equality"></a>Égalité  
 Deux instances de type anonyme sont égales si elles sont des instances du même type et si les valeurs de leurs propriétés de clé sont égales. Dans les exemples suivants, `flight2` est égal à `flight1` de l’exemple précédent, car il s’agit d’instances du même type anonyme et les valeurs de leurs propriétés de clé correspondent à celles-ci. Toutefois, `flight3` n’est pas égal à `flight1` parce qu’il a une valeur différente pour une propriété de clé, `FlightNo` . `flight4`L’instance n’est pas du même type que `flight1` parce qu’elle désigne des propriétés différentes en tant que propriétés de clé.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 Si deux instances sont déclarées avec uniquement des propriétés non-clés, identiques dans le nom, le type, l’ordre et la valeur, les deux instances ne sont pas égales. Une instance sans propriétés de clé est uniquement égale à elle-même.  
  
 Pour plus d’informations sur les conditions dans lesquelles deux instances de type anonyme sont des instances du même type anonyme, consultez [types anonymes](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Calcul du code de hachage  
 À l’instar de <xref:System.Object.Equals%2A> , la fonction de hachage définie dans <xref:System.Object.GetHashCode%2A> pour un type anonyme est basée sur les propriétés de clé du type. Les exemples suivants illustrent l’interaction entre les propriétés de clé et les valeurs de code de hachage.  
  
 Les instances d’un type anonyme qui ont les mêmes valeurs pour toutes les propriétés de clé ont la même valeur de code de hachage, même si les propriétés non-clés n’ont pas de valeurs correspondantes. L'instruction suivante retourne `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 Les instances d’un type anonyme qui ont des valeurs différentes pour une ou plusieurs propriétés de clé ont des valeurs de code de hachage différentes. L'instruction suivante retourne `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 Les instances de types anonymes qui désignent des propriétés différentes en tant que propriétés de clé ne sont pas des instances du même type. Elles ont des valeurs de code de hachage différentes, même lorsque les noms et les valeurs de toutes les propriétés sont identiques. L'instruction suivante retourne `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>Valeurs en lecture seule  
 Les valeurs des propriétés de clé ne peuvent pas être modifiées. Par exemple, dans `flight1` dans les exemples précédents, les `Airline` `FlightNo` champs et sont en lecture seule, mais ils `Gate` peuvent être modifiés.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>Voir aussi

- [Définition du type anonyme](../../programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Types anonymes](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
