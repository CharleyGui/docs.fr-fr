---
title: L'attribut '<attributename>' ne peut pas être appliqué plusieurs fois
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 14145f165adf5ccd20298a70ca5596488b488b0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409957"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>L'attribut '\<attributename>' ne peut pas être appliqué plusieurs fois

L’attribut ne peut être appliqué qu’une seule fois. L' `AttributeUsage` attribut détermine si un attribut peut être appliqué plusieurs fois.  
  
 **ID d’erreur :** BC30663  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Assurez-vous que l’attribut n’est appliqué qu’une seule fois.  
  
2. Si vous utilisez des attributs personnalisés que vous avez développés, pensez `AttributeUsage` à modifier leur attribut pour permettre l’utilisation de plusieurs attributs, comme dans l’exemple suivant.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AttributeUsageAttribute>
- [Création d'attributs personnalisés](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../programming-guide/concepts/attributes/attributeusage.md)
