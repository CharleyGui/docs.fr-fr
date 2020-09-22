---
title: Les références d'entité XML ne sont pas prises en charge
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 470e5577654ce8b6bbc2732a41c130a85ddc96e5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874994"
---
# <a name="xml-entity-references-are-not-supported"></a>Les références d'entité XML ne sont pas prises en charge

Une référence d’entité (par exemple, `©` ) qui n’est pas définie dans la spécification xml 1,0 est incluse comme valeur pour un LITTÉRAL XML. Seules `&` `"` `<` `>` `'` les références d’entité XML,,, et sont prises en charge dans les littéraux XML.  
  
 **ID d’erreur :** BC31180  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Supprimez la référence d’entité non prise en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Littéraux XML et spécification XML 1.0](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [Littéraux XML](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
