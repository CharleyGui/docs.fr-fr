---
title: La structure '<structurename>' doit contenir au moins une variable membre d'instance ou au moins une déclaration d'événement d'instance non marquée comme 'Custom'.
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 4e7ef82659c43be08ee444eaf3f4df663f7aaa53
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159649"
---
# <a name="bc30941-structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>BC30941 : la structure' \<structurename> 'doit contenir au moins une variable membre d’instance ou au moins une déclaration d’événement d’instance non marquée comme’Custom'

Une définition de structure n’inclut pas de variables non partagées ou d’événements non personnalisés non partagés.

 Chaque structure doit avoir une variable ou un événement qui s’applique à chaque instance spécifique (non partagée) au lieu de toutes les instances collectivement ([partagées](../modifiers/shared.md)). Les constantes, les propriétés et les procédures non partagées ne répondent pas à cette exigence. En outre, s’il n’existe aucune variable non partagée et un seul événement non partagé, cet événement ne peut pas être un `Custom` événement.

 **ID d’erreur :** BC30941

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Définissez au moins une variable ou un événement qui n’est pas `Shared` . Si vous ne définissez qu’un seul événement, celui-ci doit être non personnalisé et non partagé.

## <a name="see-also"></a>Voir aussi

- [Structures](../../programming-guide/language-features/data-types/structures.md)
- [Procédure : Déclarer une structure](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure, instruction](../statements/structure-statement.md)
