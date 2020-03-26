---
title: L'inférence de type nullable n'est pas prise en charge dans ce contexte
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249498"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>L'inférence de type nullable n'est pas prise en charge dans ce contexte
Les types et les structures de valeur peuvent être déclarés nuls.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Toutefois, vous ne pouvez pas utiliser la déclaration annulée en combinaison avec l’inférence de type. Les exemples suivants causent cette erreur.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID erreur:** BC36629  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Utilisez `As` une clause pour déclarer la variable comme un type de valeur nulle.  
  
## <a name="see-also"></a>Voir aussi

- [Types de valeur nuls](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
