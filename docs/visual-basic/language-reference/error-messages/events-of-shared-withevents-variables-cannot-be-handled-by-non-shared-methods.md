---
title: Les événements des variables WithEvents partagées ne peuvent pas être gérés par des méthodes non partagées
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 02039b81251e59a951a0fe37ec2c9534b458b6a5
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161918"
---
# <a name="bc30594-events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>BC30594 : les événements des variables WithEvents partagées ne peuvent pas être gérés par des méthodes non partagées

Une variable déclarée avec le `Shared` modificateur est une variable partagée. Une variable partagée identifie exactement un emplacement de stockage. Une variable déclarée avec le `WithEvents` modificateur déclare que le type auquel la variable appartient gère l’ensemble des événements déclenchés par la variable. Quand une valeur est assignée à la variable, la propriété créée par la `WithEvents` déclaration décroche un gestionnaire d’événements existant et raccorde le nouveau gestionnaire d’événements via la `Add` méthode.

 **ID d’erreur :** BC30594

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Déclarez votre gestionnaire d’événements `Shared` .

## <a name="see-also"></a>Voir aussi

- [Partagé](../modifiers/shared.md)
- [WithEvents](../modifiers/withevents.md)
