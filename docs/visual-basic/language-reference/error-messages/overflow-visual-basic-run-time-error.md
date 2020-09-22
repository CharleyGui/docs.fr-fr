---
title: Dépassement de capacité (erreur d'exécution Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: e287d6c24eca75d8bf20181a201056f467d6fc4e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871223"
---
# <a name="overflow-visual-basic-run-time-error"></a>Dépassement de capacité (erreur d'exécution Visual Basic)

Un dépassement de capacité se produit lorsque vous tentez une assignation qui dépasse les limites de la cible de l’assignation.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que les résultats des assignations, des calculs et des conversions de types de données ne sont pas trop grands pour être représentés dans la plage de variables autorisées pour ce type de valeur, et attribuez la valeur à une variable d’un type qui peut contenir une plus grande plage de valeurs, si nécessaire.  
  
2. Assurez-vous que les assignations aux propriétés correspondent à la plage de la propriété dans laquelle elles sont effectuées.  
  
3. Assurez-vous que les nombres utilisés dans les calculs qui sont convertis en entiers n’ont pas de résultats plus grands que des entiers.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [Data types](../data-types/index.md)
- [Types d’erreurs](../../programming-guide/language-features/error-types.md)
