---
title: Types de données composites
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 1c099c5082f1c4173a50c70998c99135c94821e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346377"
---
# <a name="composite-data-types-visual-basic"></a>Types de données composites (Visual Basic)
En plus des types de données élémentaires fournis par Visual Basic, vous pouvez également assembler des éléments de types différents pour créer des *types de données composites* , tels que des structures, des tableaux et des classes. Vous pouvez générer des types de données composites à partir de types élémentaires et d’autres types composites. Par exemple, vous pouvez définir un tableau d’éléments de structure ou une structure avec des membres de tableau.  
  
## <a name="data-types"></a>Types de données  
 Un type composite est différent du type de données de l’un de ses composants. Par exemple, un tableau d’éléments `Integer` n’est pas du type de données `Integer`.  
  
 Un type de données de tableau est normalement représenté à l’aide du type d’élément, des parenthèses et des virgules, si nécessaire. Par exemple, un tableau unidimensionnel d’éléments `String` est représenté comme `String()`, et un tableau à deux dimensions d’éléments `Boolean` est représenté comme `Boolean(,)`.  
  
## <a name="structure-types"></a>Types de structures  
 Il n’existe pas de type de données unique comprenant toutes les structures. Au lieu de cela, chaque définition d’une structure représente un type de données unique, même si deux structures définissent des éléments identiques dans le même ordre. Toutefois, si vous créez deux instances ou plus de la même structure, Visual Basic les considère comme étant du même type de données.  
  
## <a name="tuples"></a>Tuples

Un tuple est une structure légère qui contient au moins deux champs dont les types sont prédéfinis. Les tuples sont pris en charge à partir de Visual Basic 2017. Les tuples sont généralement utilisés pour retourner plusieurs valeurs à partir d’un seul appel de méthode sans avoir à passer d’arguments par référence ou à empaqueter les champs retournés dans une classe ou une structure plus lourde. Pour plus d’informations sur les tuples, consultez la rubrique [tuples](tuples.md) .

## <a name="array-types"></a>Types tableau  
 Il n’existe pas de type de données unique comprenant tous les tableaux. Le type de données d’une instance particulière d’un tableau est déterminé par les éléments suivants :  
  
- Le fait qu’il s’agit d’un tableau  
  
- Rang (nombre de dimensions) du tableau  
  
- Type d’élément du tableau  
  
 En particulier, la longueur d’une dimension donnée ne fait pas partie du type de données de l’instance. L’exemple suivant illustre ces actions.  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 Dans l’exemple précédent, les variables de tableau `arrayA` et `arrayB` sont considérées comme ayant le même type de données (`Byte()`), même si elles sont initialisées avec des longueurs différentes. Les variables `arrayB` et `arrayC` ne sont pas du même type, car leurs types d’éléments sont différents. Les variables `arrayC` et `arrayD` ne sont pas du même type, car leurs rangs sont différents. Les variables `arrayD` et `arrayE` avoir le même type, `Short(,)`, car leurs rangs et leurs types d’éléments sont les mêmes, même si `arrayD` n’est pas encore initialisé.  
  
 Pour plus d’informations sur les tableaux, consultez [tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Types de classes  
 Il n’existe pas de type de données unique comprenant toutes les classes. Même si une classe peut hériter d’une autre classe, chacun d’eux est un type de données distinct. Plusieurs instances de la même classe sont du même type de données. Si vous assignez une variable d’instance de classe à une autre, non seulement elles ont le même type de données, mais elles pointent vers la même instance de classe en mémoire.  
  
 Pour plus d’informations sur les classes, consultez [objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Voir aussi

- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Guide pratique : stocker plusieurs valeurs dans une variable](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
