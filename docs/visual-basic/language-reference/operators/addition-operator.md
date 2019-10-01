---
title: + (Visual Basic), opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 3187551afb7d25470f48dad894188766a811bb0a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700997"
---
# <a name="-operator-visual-basic"></a>+, opérateur (Visual Basic)
Additionne deux nombres ou retourne la valeur positive d’une expression numérique. Peut également être utilisé pour concaténer deux expressions de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb
expression1 + expression2
```
  
ou

```vb  
+expression1  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`expression1`|Obligatoire. Toute expression numérique ou de chaîne.|  
|`expression2`|Obligatoire, sauf `+` si l’opérateur calcule une valeur négative. Toute expression numérique ou de chaîne.|  
  
## <a name="result"></a>Résultat  
 Si `expression1` et que `expression2` sont tous deux numériques, le résultat est leur somme arithmétique.  
  
 Si `expression2` est absent, l’opérateur `+` est l’opérateur d’identité *unaire* pour la valeur inchangée d’une expression. Dans ce sens, l’opération consiste à conserver le signe de `expression1`, donc le résultat est négatif si `expression1` est négatif.  
  
 Si `expression1` et que `expression2` sont des chaînes, le résultat est la concaténation de leurs valeurs.  
  
 Si `expression1` et `expression2` sont des types mixtes, l’action effectuée dépend de leurs types, de leur contenu et du paramètre de l' [instruction Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). Pour plus d’informations, consultez les tableaux dans « remarques ».  
  
## <a name="supported-types"></a>Types pris en charge  
 Tous les types numériques, y compris les types non signés et à virgule flottante, `Decimal` et `String`.  
  
## <a name="remarks"></a>Notes  
 En général, `+` effectue une addition arithmétique lorsque cela est possible, et concatène uniquement lorsque les deux expressions sont des chaînes.  
  
 Si aucune des expressions n’est un `Object`, Visual Basic effectue les actions suivantes.  
  
|Types de données d’expressions|Action par le compilateur|  
|---|---|  
|Les deux expressions sont des types de données numériques (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single` ou 0)|Complémentaires. Le type de données de résultat est un type numérique approprié pour les types `expression1` de `expression2`données de et. Consultez les tables « arithmétiques sur les entiers » dans [types de données des résultats d’opérateur](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Les deux expressions sont de type `String`|Concaténer.|  
|Une expression est un type de données numérique et l’autre est une chaîne|Si `Option Strict` est `On`, génère une erreur du compilateur.<br /><br /> Si `Option Strict` est `Off`, convertit implicitement le `String` en `Double` et ajoute.<br /><br /> Si la `String` ne peut pas être convertie en `Double`, levez une exception <xref:System.InvalidCastException>.|  
|Une expression est un type de données numérique, tandis que l’autre est [Nothing](../../../visual-basic/language-reference/nothing.md)|Ajoutez, avec @no__t valeur 0 comme zéro.|  
|Une expression est une chaîne, tandis que l’autre est `Nothing`|Concaténer, avec @no__t valeur 0 comme «».|  
  
 Si une expression est une expression `Object`, Visual Basic effectue les actions suivantes.  
  
|Types de données d’expressions|Action par le compilateur|  
|---|---|  
|l’expression `Object` contient une valeur numérique et l’autre est un type de données numérique|Si `Option Strict` est `On`, génère une erreur du compilateur.<br /><br /> Si `Option Strict` est `Off`, ajoutez.|  
|l’expression `Object` contient une valeur numérique et l’autre est de type `String`|Si `Option Strict` est `On`, génère une erreur du compilateur.<br /><br /> Si `Option Strict` est `Off`, convertit implicitement le `String` en `Double` et ajoute.<br /><br /> Si la `String` ne peut pas être convertie en `Double`, levez une exception <xref:System.InvalidCastException>.|  
|l’expression `Object` contient une chaîne et l’autre est un type de données numérique|Si `Option Strict` est `On`, génère une erreur du compilateur.<br /><br /> Si `Option Strict` est `Off`, convertit implicitement la chaîne `Object` en `Double` et ajoute.<br /><br /> Si la chaîne `Object` ne peut pas être convertie en `Double`, levez une exception <xref:System.InvalidCastException>.|  
|l’expression `Object` contient une chaîne et l’autre est de type `String`|Si `Option Strict` est `On`, génère une erreur du compilateur.<br /><br /> Si `Option Strict` est `Off`, convertit implicitement `Object` en `String` et concatène.|  
  
 Si les deux expressions sont des expressions `Object`, Visual Basic effectue les actions suivantes (`Option Strict Off` uniquement).  
  
|Types de données d’expressions|Action par le compilateur|  
|---|---|  
|Les deux expressions `Object` contiennent des valeurs numériques|Complémentaires.|  
|Les deux expressions `Object` sont de type `String`|Concaténer.|  
|Une expression `Object` contient une valeur numérique et l’autre contient une chaîne|Convertit implicitement la chaîne `Object` en `Double` et ajoute.<br /><br /> Si la chaîne `Object` ne peut pas être convertie en valeur numérique, levez une exception <xref:System.InvalidCastException>.|  
  
 Si l’une des expressions `Object` a la valeur [Nothing](../../../visual-basic/language-reference/nothing.md) ou <xref:System.DBNull>, l’opérateur `+` le traite en tant que `String` avec la valeur «».  
  
> [!NOTE]
> Lorsque vous utilisez l’opérateur `+`, vous ne pourrez peut-être pas déterminer si l’addition ou la concaténation de chaînes aura lieu. Utilisez l’opérateur `&` pour la concaténation afin d’éliminer toute ambiguïté et de fournir du code auto-documenté.  
  
## <a name="overloading"></a>Surcharge  
 L’opérateur `+` peut être *surchargé*, ce qui signifie qu’une classe ou une structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou de cette structure. Si votre code utilise cet opérateur sur une classe ou une structure de ce type, veillez à bien comprendre son comportement redéfini. Pour plus d'informations, consultez [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’opérateur `+` pour ajouter des nombres. Si les opérandes sont à la fois numériques, Visual Basic calcule le résultat arithmétique. Le résultat arithmétique représente la somme des deux opérandes.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 Vous pouvez également utiliser l’opérateur `+` pour concaténer des chaînes. Si les opérandes sont à la fois des chaînes, Visual Basic les concatène. Le résultat de la concaténation représente une chaîne unique composée du contenu des deux opérandes, l’un après l’autre.  
  
 Si les opérandes sont de types mixtes, le résultat dépend du paramètre de l' [instruction Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). L’exemple suivant illustre le résultat lorsque `Option Strict` est `On`.  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 L’exemple suivant illustre le résultat lorsque `Option Strict` est `Off`.  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Pour éliminer toute ambiguïté, vous devez utiliser l’opérateur `&` au lieu de `+` pour la concaténation.  
  
## <a name="see-also"></a>Voir aussi

- [& (opérateur)](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [opérateur de concaténation](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Opérateurs arithmétiques](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Priorité des opérateurs en Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Opérateurs arithmétiques dans Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
