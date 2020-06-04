---
title: L'inférence de type nullable n'est pas prise en charge dans ce contexte
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409385"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>L'inférence de type nullable n'est pas prise en charge dans ce contexte
Les types valeur et les structures peuvent être déclarés Nullable.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Toutefois, vous ne pouvez pas utiliser la déclaration Nullable en association avec l’inférence de type. Les exemples suivants provoquent cette erreur.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID d’erreur :** BC36629  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Utilisez une `As` clause pour déclarer la variable en tant que type valeur Nullable.  
  
## <a name="see-also"></a>Voir aussi

- [Types valeur Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md)
