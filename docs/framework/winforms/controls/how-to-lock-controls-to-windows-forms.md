---
title: verrouiller des contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 16eb151dc435614e1edc82bf9f0acf3974f36690
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736240"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Comment : verrouiller des contrôles pour Windows Forms

Lorsque vous concevez l’interface utilisateur de votre application Windows, vous pouvez verrouiller les contrôles une fois qu’ils sont positionnés correctement, afin de ne pas les déplacer ou les redimensionner par inadvertance lors de la définition d’autres propriétés.

En outre, vous pouvez verrouiller et déverrouiller tous les contrôles du formulaire à la fois, ce qui est utile pour les formulaires avec de nombreux contrôles, ou vous pouvez déverrouiller des contrôles individuels. Une fois que vous avez placé tous les contrôles à l’emplacement souhaité sur le formulaire, verrouillez-les pour éviter tout mouvement erroné.

## <a name="to-lock-a-control"></a>Pour verrouiller un contrôle

Dans la fenêtre **Propriétés** de Visual Studio, sélectionnez la propriété **verrouillé** , puis sélectionnez **true**. (Si vous double-cliquez sur le nom, le paramètre de propriété est activé.)

Vous pouvez également cliquer avec le bouton droit sur le contrôle et choisir **verrouiller les contrôles**.

> [!NOTE]
> Le verrouillage des contrôles empêche leur déplacement vers une nouvelle taille ou un nouvel emplacement sur l’aire de conception. Toutefois, vous pouvez toujours modifier la taille ou l’emplacement des contrôles à l’aide de la fenêtre **Propriétés** ou dans le code.

## <a name="to-lock-all-the-controls-on-a-form"></a>Pour verrouiller tous les contrôles d’un formulaire

Dans le menu **format** , choisissez **verrouiller les contrôles**.

> [!NOTE]
> Cette commande verrouille également la taille du formulaire, car un formulaire est un contrôle.

## <a name="to-unlock-all-locked-controls-on-a-form"></a>Pour déverrouiller tous les contrôles verrouillés dans un formulaire

Dans le menu **format** , choisissez **verrouiller les contrôles**.

Tous les contrôles précédemment verrouillés sur le formulaire sont maintenant déverrouillés.

## <a name="to-unlock-locked-controls-individually"></a>Pour déverrouiller des contrôles verrouillés individuellement

Dans la fenêtre **Propriétés** , sélectionnez la propriété **verrouillé** , puis sélectionnez **false**. (Si vous double-cliquez sur le nom, le paramètre de propriété est activé.)

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
