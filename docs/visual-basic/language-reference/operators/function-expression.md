---
title: Expression de fonction
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: a9b621ff03f833fcf0f07f876fd864ee963bef75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371179"
---
# <a name="function-expression-visual-basic"></a>Expression de fonction (Visual Basic)
Déclare les paramètres et le code qui définissent une expression lambda de fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`parameterlist`|Facultatif. Liste des noms de variables locales qui représentent les paramètres de cette procédure. Les parenthèses doivent être présentes même lorsque la liste est vide. Consultez la [liste des paramètres](../statements/parameter-list.md).|  
|`expression`|Obligatoire. Expression unique. Le type de l’expression est le type de retour de la fonction.|  
|`statements`|Obligatoire. Liste d’instructions qui retourne une valeur à l’aide de l' `Return` instruction. (Consultez [instruction return](../statements/return-statement.md).) Le type de la valeur retournée est le type de retour de la fonction.|  
  
## <a name="remarks"></a>Notes  
 Une *expression lambda* est une fonction sans nom qui calcule et retourne une valeur. Vous pouvez utiliser une expression lambda partout où vous pouvez utiliser un type délégué, sauf en tant qu’argument de `RemoveHandler` . Pour plus d’informations sur les délégués et l’utilisation d’expressions lambda avec des délégués, consultez [instruction de délégué](../statements/delegate-statement.md) et [conversion simplifiée](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)des délégués.  
  
## <a name="lambda-expression-syntax"></a>Syntaxe d’expression lambda  
 La syntaxe d’une expression lambda ressemble à celle d’une fonction standard. Les différences sont les suivantes :  
  
- Une expression lambda n’a pas de nom.  
  
- Les expressions lambda ne peuvent pas avoir de modificateurs, tels que `Overloads` ou `Overrides` .  
  
- Les expressions lambda n’utilisent pas de `As` clause pour désigner le type de retour de la fonction. Au lieu de cela, le type est déduit de la valeur à laquelle le corps d’une expression lambda sur une seule ligne prend la valeur, ou la valeur de retour d’une expression lambda multiligne. Par exemple, si le corps d’une expression lambda sur une seule ligne est `Where cust.City = "London"` , son type de retour est `Boolean` .  
  
- Le corps d’une expression lambda sur une seule ligne doit être une expression, et non une instruction. Le corps peut se composer d’un appel à une procédure de fonction, mais pas d’un appel à une procédure Sub.  
  
- Tous les paramètres doivent avoir des types de données spécifiés ou tous doivent être déduits.  
  
- Les paramètres facultatifs et ParamArray ne sont pas autorisés.  
  
- Les paramètres génériques ne sont pas autorisés.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants illustrent deux façons de créer des expressions lambda simples. La première utilise un `Dim` pour fournir un nom pour la fonction. Pour appeler la fonction, vous devez envoyer une valeur pour le paramètre.  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez également déclarer et exécuter la fonction en même temps.  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>Exemple  
 Voici un exemple d’expression lambda qui incrémente son argument et retourne la valeur. L’exemple montre la syntaxe d’expression lambda à ligne unique et multiligne pour une fonction. Pour obtenir plus d’exemples, consultez [expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>Exemple  
 Les expressions lambda sont sous-jacentes de nombreux opérateurs de requête dans LINQ (Language-Integrated Query) et peuvent être utilisées explicitement dans les requêtes basées sur une méthode. L’exemple suivant montre une requête LINQ classique, suivie de la traduction de la requête en format de méthode.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Pour plus d’informations sur les méthodes de requête, consultez [requêtes](../queries/index.md). Pour plus d’informations sur les opérateurs de requête standard, consultez [vue d’ensemble des opérateurs de requête standard](../../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Function (instruction)](../statements/function-statement.md)
- [Expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Opérateurs et expressions](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Instructions](../../programming-guide/language-features/statements.md)
- [Comparaisons de valeurs](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Expressions booléennes](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [If, opérateur](if-operator.md)
- [Conversion simplifiée des délégués](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
