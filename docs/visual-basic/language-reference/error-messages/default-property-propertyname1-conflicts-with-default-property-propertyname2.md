---
title: La propriété par défaut '<propertyname1>' est en conflit avec la propriété par défaut '<propertyname2>' de la classe '<classname>' et devrait donc être déclarée 'Shadows'
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: b857a9ae7875a156179602cbe77558333d07b7b9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874511"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>La propriété par défaut '\<propertyname1>' est en conflit avec la propriété par défaut '\<propertyname2>' de la classe '\<classname>' et devrait donc être déclarée 'Shadows'

Une propriété est déclarée avec le même nom qu’une propriété définie dans la classe de base. Dans ce cas, la propriété de cette classe doit occulter la propriété de la classe de base.  
  
 Ce message est un avertissement. `Shadows` est supposé par défaut. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40007  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Ajoutez le `Shadows` mot clé à la déclaration ou modifiez le nom de la propriété déclarée.  
  
## <a name="see-also"></a>Voir aussi

- [Shadows](../modifiers/shadows.md)
- [Occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
