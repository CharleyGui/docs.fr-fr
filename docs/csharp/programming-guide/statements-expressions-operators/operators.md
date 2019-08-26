---
title: Opérateurs - Guide de programmation C#
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 4870c744383205c2b7e3832c01fb838a545f085f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588609"
---
# <a name="operators-c-programming-guide"></a>Opérateurs (guide de programmation C#)

En C#, un *opérateur* est un élément de programme qui s'applique à un ou plusieurs *opérandes* dans une expression ou une instruction. Les opérateurs qui prennent un opérande, comme l'opérateur d'incrément (`++`) ou `new`, portent le nom d'opérateurs *unaires* . Les opérateurs qui prennent deux opérandes, comme les opérateurs arithmétiques (`+`,`-`,`*`,`/`) portent le nom d'opérateur *binaires* . Un opérateur, l'opérateur conditionnel (`?:`), prend trois opérandes et est le seul opérateur ternaire en C#.  
  
 L'instruction C# suivante contient un seul opérateur unaire et un seul opérande. L'opérateur d'incrément, `++`, modifie la valeur de l'opérande `y`.  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 L'instruction C# suivante contient deux opérateurs binaires, chacun avec deux opérandes. L'opérateur d'assignation, `=`, a la variable de type entier `y` et l'expression `2 + 3` comme opérandes. L'expression `2 + 3` elle-même se compose de l'opérateur Addition et de deux opérandes, `2` et `3`.  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
Un opérande peut être une expression valide qui est composée d'une longueur quelconque de code, et qui peut comporter plusieurs sous-expressions. Dans une expression qui contient plusieurs opérateurs, l'ordre dans lequel les opérateurs sont appliqués est déterminé par la *priorité des opérateurs*, *l'associativité*et les parenthèses.  

## <a name="operator-precedence"></a>Précédence des opérateurs
  
Chaque opérateur a une priorité définie. Dans une expression qui contient plusieurs opérateurs ayant différents niveaux de priorité, la priorité des opérateurs détermine l'ordre dans lequel les opérateurs sont évalués. Par exemple, l’instruction suivante assigne la valeur 3 à `n1` :

```csharp
n1 = 11 - 2 * 4;
```

La multiplication est effectuée en premier lieu parce que la multiplication est prioritaire sur la soustraction.

Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](../../language-reference/operators/index.md).
  
## <a name="associativity"></a>l'associativité

 Lorsque deux opérateurs ou plus, de même niveau de priorité figurent dans une expression, ils sont évalués sur la base de l'associativité. Les opérateurs associatifs sur leur gauche sont évalués dans l'ordre, de gauche à droite. Par exemple, `x * y / z` est évalué comme étant `(x * y) / z`. Les opérateurs associatifs sur leur droite sont évalués dans l'ordre, de droite à gauche. Par exemple, l'opérateur d'assignation est associatif sur sa droite. Dans le cas contraire, le code suivant génère une erreur.  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 Autre exemple, l’opérateur ternaire ([?:](../../language-reference/operators/conditional-operator.md)) est associatif sur sa droite. La plupart des opérateurs binaires sont associatifs sur leur gauche.  
  
 Si les opérateurs présents dans une expression sont associatifs sur leur gauche ou associatifs sur leur droite, les opérandes de chaque expression sont évalués en premier, de gauche à droite. Les exemples suivants illustrent l'ordre d'évaluation des opérateurs et des opérandes.  
  
|Instruction|Ordre d'évaluation|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>Ajout de parenthèses

 Vous pouvez modifier l'ordre imposé par la priorité d'opérateur et l'associativité en utilisant des parenthèses. Par exemple, `2 + 3 * 2` correspond généralement à 8, car les opérateurs de multiplication ont la priorité sur les opérateurs additifs. Toutefois, si vous entrez une expression comme `(2 + 3) * 2`, l'addition est évaluée avant la multiplication, et le résultat est 10. Les exemples suivants illustrent l'ordre d'évaluation dans les expressions entre parenthèses. Comme dans les exemples précédents, l'évaluation des opérandes a lieu avant l'application de l'opérateur.  
  
|Instruction|Ordre d'évaluation|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>Surcharge d’opérateur

Vous pouvez définir le comportement de certains opérateurs pour les classes et les structs personnalisés. Ce processus est connu sous le nom de *surcharge d'opérateur*. Pour plus d’informations, consultez [Surcharge d’opérateur](../../language-reference/operators/operator-overloading.md).
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Instructions, expressions et opérateurs](index.md)
- [Opérateurs C#](../../language-reference/operators/index.md)
