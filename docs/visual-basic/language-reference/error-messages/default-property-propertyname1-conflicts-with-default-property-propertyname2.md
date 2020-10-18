---
title: La propriété par défaut '<propertyname1>' est en conflit avec la propriété par défaut '<propertyname2>' de la classe '<classname>' et devrait donc être déclarée 'Shadows'
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 290971a3173c59f08fbd279b6fffe3bcb618cb72
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160605"
---
# <a name="bc40007-default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>BC40007 : la propriété par défaut' \<propertyname1> 'est en conflit avec la propriété par défaut' \<propertyname2> 'dans' \<classname> 'et doit donc être déclarée’Shadows'

Une propriété est déclarée avec le même nom qu’une propriété définie dans la classe de base. Dans ce cas, la propriété de cette classe doit occulter la propriété de la classe de base.

 Ce message est un avertissement. `Shadows` est supposé par défaut. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC40007

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Ajoutez le `Shadows` mot clé à la déclaration ou modifiez le nom de la propriété déclarée.

## <a name="see-also"></a>Voir aussi

- [Ombres](../modifiers/shadows.md)
- [Occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
