---
title: Single, type de données
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: 60a688c510f6e36dca5809566b37a388429e18c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343919"
---
# <a name="single-data-type-visual-basic"></a>Single, type de données (Visual Basic)

Contient les nombres à virgule flottante simple précision IEEE 32 bits (4 octets) signés dont la valeur est comprise entre-3.4028235 E + 38 et-1.401298 E-45 pour les valeurs négatives et de 1.401298 E-45 à 3.4028235 E + 38 pour les valeurs positives. Les nombres à simple précision stockent une approximation d’un nombre réel.  
  
## <a name="remarks"></a>Notes  

 Utilisez le type de données `Single` pour contenir des valeurs à virgule flottante qui ne nécessitent pas la largeur totale des données de `Double`. Dans certains cas, l’common language runtime peut être en mesure de regrouper vos variables de `Single` étroitement et de réduire la consommation de mémoire.  
  
 La valeur par défaut de `Single` est 0.  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
- **Précision.** Lorsque vous travaillez avec des nombres à virgule flottante, gardez à l’esprit qu’ils n’ont pas toujours une représentation précise en mémoire. Cela peut entraîner des résultats inattendus de certaines opérations, telles que la comparaison de valeurs et l’opérateur `Mod`. Pour plus d’informations, consultez [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
- **Étendue.** Le type de données `Single` s’étend à `Double`. Cela signifie que vous pouvez convertir `Single` en `Double` sans rencontrer d’erreur <xref:System.OverflowException?displayProperty=nameWithType>.  
  
- **Zéros de fin.** Les types de données à virgule flottante n’ont pas de représentation interne des 0 caractères de fin. Par exemple, ils ne font pas la distinction entre 4,2000 et 4,2. Par conséquent, les caractères de fin 0 ne s’affichent pas lorsque vous affichez ou imprimez des valeurs à virgule flottante.  
  
- **Caractères de type.** L'ajout du caractère de type littéral `F` à un littéral force ce dernier en type de données `Single`. L'ajout du caractère de type identificateur `!` à un identificateur force ce dernier en type `Single`.  
  
- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Single?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Single?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal (type de données)](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Double (type de données)](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [Dépannage des types de données](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
