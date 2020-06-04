---
title: DirectCast, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 96cb2082d59373deb34d6894270205b7c1045850
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371516"
---
# <a name="directcast-operator-visual-basic"></a>Opérateur DirectCast (Visual Basic)
Introduit une opération de conversion de type en fonction de l’héritage ou de l’implémentation.  
  
## <a name="remarks"></a>Notes  
 `DirectCast`n’utilise pas les routines d’assistance au moment de l’exécution Visual Basic pour la conversion, afin d’offrir des performances supérieures à celles de la `CType` conversion vers et à partir du type de données `Object` .  
  
 Vous utilisez le `DirectCast` mot clé de la même façon que vous utilisez la [fonction CType](../functions/ctype-function.md) et le mot clé [opérateur TryCast](trycast-operator.md) . Vous fournissez une expression comme premier argument et un type à convertir en tant que deuxième argument. `DirectCast`requiert une relation d’héritage ou d’implémentation entre les types de données des deux arguments. Cela signifie qu’un type doit hériter de ou implémenter l’autre.  
  
## <a name="errors-and-failures"></a>Erreurs et échecs  
 `DirectCast`génère une erreur du compilateur s’il détecte qu’il n’existe aucune relation d’héritage ou d’implémentation. Toutefois, l’absence d’erreur du compilateur ne garantit pas une conversion réussie. Si la conversion souhaitée est restrictive, elle peut échouer au moment de l’exécution. Dans ce cas, le runtime génère une <xref:System.InvalidCastException> erreur.  
  
## <a name="conversion-keywords"></a>Mots clés de conversion  
 Une comparaison des mots clés de conversion de type est la suivante.  
  
|Mot clé|Types de données|Relation d’argument|Échec au moment de l’exécution|  
|---|---|---|---|  
|[CType Function](../functions/ctype-function.md)|Tous les types de données|La conversion étendue ou restrictive doit être définie entre les deux types de données|Lève<xref:System.InvalidCastException>|  
|`DirectCast`|Tous les types de données|Un type doit hériter de ou implémenter l’autre type|Lève<xref:System.InvalidCastException>|  
|[TryCast, opérateur](trycast-operator.md)|Types référence uniquement|Un type doit hériter de ou implémenter l’autre type|Retourne [Nothing](../nothing.md)|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre deux utilisations de `DirectCast` , une qui échoue au moment de l’exécution et une qui réussit.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 Dans l’exemple précédent, le type au moment de l’exécution `q` est `Double` . `CType`réussit, car `Double` peut être converti en `Integer` . Toutefois, le premier `DirectCast` échoue au moment de l’exécution, car le type d’exécution de `Double` n’a pas de relation d’héritage avec `Integer` , même s’il existe une conversion. La deuxième `DirectCast` opération est effectuée, car elle convertit le type <xref:System.Windows.Forms.Form> en type <xref:System.Windows.Forms.Control> , duquel <xref:System.Windows.Forms.Form> hérite.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversions implicites et explicites](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
