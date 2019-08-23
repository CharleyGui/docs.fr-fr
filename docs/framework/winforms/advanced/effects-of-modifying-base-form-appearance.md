---
title: Conséquences de la modification de l'aspect d'un formulaire de base
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: b24bd2db564c7acb0a748c47095ee0777ea1eb88
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955144"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a>Effets de la modification de l’apparence d’un formulaire de base

Pendant le développement d’applications, vous êtes souvent amené à modifier l’apparence du formulaire de base dont héritent d’autres formulaires du projet (ou d’autres projets).

Au moment du design, les modifications apportées à l’aspect du formulaire de base (qu’il s’agisse de la définition de propriétés ou de l’addition et de la soustraction de contrôles) sont répercutées dans les formulaires hérités lors de la génération du projet contenant le formulaire de base. Il ne suffit pas d’enregistrer les modifications apportées au formulaire de base. Pour générer un projet, sélectionnez **Générer** dans le menu **Générer**.

Les modifications apportées au formulaire à l’exécution n’ont aucune incidence sur les formulaires hérités déjà instanciés.

## <a name="see-also"></a>Voir aussi

- [base](../../../csharp/language-reference/keywords/base.md)
- [Guide pratique pour Hériter Windows Forms](how-to-inherit-windows-forms.md)
- [Héritage visuel des Windows Forms](windows-forms-visual-inheritance.md)
