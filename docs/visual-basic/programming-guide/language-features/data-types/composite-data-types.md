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
ms.openlocfilehash: 842b74aa7cc99c8196fdfb1eb6c976d9e72a4fa4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077161"
---
# <a name="composite-data-types-visual-basic"></a>Types de données composites (Visual Basic)

En plus des types de données élémentaires fournis par Visual Basic, vous pouvez également assembler des éléments de types différents pour créer des *types de données composites* , tels que des structures, des tableaux et des classes. Vous pouvez générer des types de données composites à partir de types élémentaires et d’autres types composites. Par exemple, vous pouvez définir un tableau d’éléments de structure ou une structure avec des membres de tableau.  
  
## <a name="data-types"></a>Types de données  

 Un type composite est différent du type de données de l’un de ses composants. Par exemple, un tableau d' `Integer` éléments n’est pas du `Integer` type de données.  
  
 Un type de données de tableau est normalement représenté à l’aide du type d’élément, des parenthèses et des virgules, si nécessaire. Par exemple, un tableau unidimensionnel d' `String` éléments est représenté sous `String()` la forme et un tableau à deux dimensions d' `Boolean` éléments est représenté sous la forme `Boolean(,)` .  
  
## <a name="structure-types"></a>Types de structures  

 Il n’existe pas de type de données unique comprenant toutes les structures. Au lieu de cela, chaque définition d’une structure représente un type de données unique, même si deux structures définissent des éléments identiques dans le même ordre. Toutefois, si vous créez deux instances ou plus de la même structure, Visual Basic les considère comme étant du même type de données.  
  
## <a name="tuples"></a>Tuples

Un tuple est une structure légère qui contient au moins deux champs dont les types sont prédéfinis. Les tuples sont pris en charge à partir de Visual Basic 2017. Les tuples sont généralement utilisés pour retourner plusieurs valeurs à partir d’un seul appel de méthode sans avoir à passer d’arguments par référence ou à empaqueter les champs retournés dans une classe ou une structure plus lourde. Pour plus d’informations sur les tuples, consultez la rubrique [tuples](tuples.md) .

## <a name="array-types"></a>Types de tableaux  

 Il n’existe pas de type de données unique comprenant tous les tableaux. Le type de données d’une instance particulière d’un tableau est déterminé par les éléments suivants :  
  
- Le fait qu’il s’agit d’un tableau  
  
- Rang (nombre de dimensions) du tableau  
  
- Type d’élément du tableau  
  
 En particulier, la longueur d’une dimension donnée ne fait pas partie du type de données de l’instance. L'exemple suivant illustre ce comportement.  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 Dans l’exemple précédent, les variables `arrayA` de tableau et `arrayB` sont considérées comme ayant le même type de données, `Byte()` même si elles sont initialisées à des longueurs différentes. `arrayB`Les variables et ne `arrayC` sont pas du même type, car leurs types d’éléments sont différents. `arrayC`Les variables et ne `arrayD` sont pas du même type, car leurs rangs sont différents. Les variables `arrayD` et `arrayE` ont le même type ( `Short(,)` ), car leurs rangs et leurs types d’éléments sont identiques, même si `arrayD` n’est pas encore initialisé.  
  
 Pour plus d’informations sur les tableaux, consultez [tableaux](../arrays/index.md).  
  
## <a name="class-types"></a>Types de classes  

 Il n’existe pas de type de données unique comprenant toutes les classes. Même si une classe peut hériter d’une autre classe, chacun d’eux est un type de données distinct. Plusieurs instances de la même classe sont du même type de données. Si vous assignez une variable d’instance de classe à une autre, non seulement elles ont le même type de données, mais elles pointent vers la même instance de classe en mémoire.  
  
 Pour plus d’informations sur les classes, consultez [objets et classes](../objects-and-classes/index.md).  
  
## <a name="see-also"></a>Voir aussi

- [Data types](index.md)
- [Types de données élémentaires](elementary-data-types.md)
- [Generic Types in Visual Basic](generic-types.md)
- [Types valeur et types référence](value-types-and-reference-types.md)
- [Conversions de type en Visual Basic](type-conversions.md)
- [Structures](structures.md)
- [Dépannage des types de données](troubleshooting-data-types.md)
- [Procédure : Stocker plusieurs valeurs dans une variable](how-to-hold-more-than-one-value-in-a-variable.md)
