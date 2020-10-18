---
title: L'attribut '<attributename>' ne peut pas être appliqué plusieurs fois
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 27cbe6d0043179c4a5d52baae06bad805f9d1d3a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162659"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a>BC30663 : l’attribut' \<attributename> 'ne peut pas être appliqué plusieurs fois

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
