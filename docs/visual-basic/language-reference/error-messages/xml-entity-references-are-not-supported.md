---
title: Les références d'entité XML ne sont pas prises en charge
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 37e72dbd6de61a50b4192a0151db40cb4be49d1c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163270"
---
# <a name="bc31180-xml-entity-references-are-not-supported"></a>BC31180 : les références d’entité XML ne sont pas prises en charge

Une référence d’entité (par exemple, `©` ) qui n’est pas définie dans la spécification xml 1,0 est incluse comme valeur pour un LITTÉRAL XML. Seules `&` `"` `<` `>` `'` les références d’entité XML,,, et sont prises en charge dans les littéraux XML.

 **ID d’erreur :** BC31180

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Supprimez la référence d’entité non prise en charge.

## <a name="see-also"></a>Voir aussi

- [Littéraux XML et spécification XML 1.0](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [Littéraux XML](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
