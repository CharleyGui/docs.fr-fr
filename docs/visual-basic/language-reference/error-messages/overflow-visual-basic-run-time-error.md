---
title: Dépassement de capacité (erreur d'exécution Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 5606ae8188c12142800adef46819791b732ff73c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387268"
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
- [Types de données](../data-types/index.md)
- [Types d’erreurs](../../programming-guide/language-features/error-types.md)
