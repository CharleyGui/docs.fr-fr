---
title: DirectCast, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 8ea29b80cf27bbb2c21a8cebbfaa0a294e05f11d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331305"
---
# <a name="directcast-operator-visual-basic"></a>Opérateur DirectCast (Visual Basic)
Introduit une opération de conversion de type en fonction de l’héritage ou de l’implémentation.  
  
## <a name="remarks"></a>Notes  
 `DirectCast` n’utilise pas les routines d’assistance d’exécution Visual Basic pour la conversion, il peut donc fournir des performances légèrement meilleures que `CType` lors de la conversion vers et depuis le type de données `Object`.  
  
 Vous utilisez le mot clé `DirectCast` de la même façon que vous utilisez la [fonction CType](../../../visual-basic/language-reference/functions/ctype-function.md) et le mot clé [opérateur TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) . Vous fournissez une expression comme premier argument et un type à convertir en tant que deuxième argument. `DirectCast` nécessite une relation d’héritage ou d’implémentation entre les types de données des deux arguments. Cela signifie qu’un type doit hériter de ou implémenter l’autre.  
  
## <a name="errors-and-failures"></a>Erreurs et échecs  
 `DirectCast` génère une erreur du compilateur s’il détecte qu’il n’existe aucune relation d’héritage ou d’implémentation. Toutefois, l’absence d’erreur du compilateur ne garantit pas une conversion réussie. Si la conversion souhaitée est restrictive, elle peut échouer au moment de l’exécution. Dans ce cas, le runtime lève une erreur <xref:System.InvalidCastException>.  
  
## <a name="conversion-keywords"></a>Mots clés de conversion  
 Une comparaison des mots clés de conversion de type est la suivante.  
  
|Mot clé|Types de données|Relation d’argument|Échec au moment de l’exécution|  
|---|---|---|---|  
|[CType (fonction)](../../../visual-basic/language-reference/functions/ctype-function.md)|Tous les types de données|La conversion étendue ou restrictive doit être définie entre les deux types de données|Lève <xref:System.InvalidCastException>|  
|`DirectCast`|Tous les types de données|Un type doit hériter de ou implémenter l’autre type|Lève <xref:System.InvalidCastException>|  
|[TryCast (opérateur)](../../../visual-basic/language-reference/operators/trycast-operator.md)|Types référence uniquement|Un type doit hériter de ou implémenter l’autre type|Retourne [Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre deux utilisations de `DirectCast`, une qui échoue au moment de l’exécution et une qui réussit.  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 Dans l’exemple précédent, le type au moment de l’exécution de `q` est `Double`. `CType` réussit, car `Double` peut être converti en `Integer`. Toutefois, la première `DirectCast` échoue au moment de l’exécution, car le type d’exécution de `Double` n’a pas de relation d’héritage avec `Integer`, même s’il existe une conversion. La deuxième `DirectCast` réussie, car elle convertit le type <xref:System.Windows.Forms.Form> en type <xref:System.Windows.Forms.Control>, à partir duquel <xref:System.Windows.Forms.Form> hérite.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
