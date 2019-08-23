---
title: 'Procédure : superposer des objets dans des Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 818f36633575b248d92da475c462cc0f211fe969
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966537"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Procédure : superposer des objets dans des Windows Forms
Lorsque vous créez une interface utilisateur complexe ou que vous utilisez un formulaire d’interface multidocument (MDI), vous souhaiterez souvent superposer les contrôles et les formulaires enfants pour créer des interfaces utilisateur plus complexes. Pour déplacer et suivre les contrôles et les fenêtres dans le contexte d’un groupe, vous manipulez leur ordre de plan. L' *ordre de plan* est la superposition visuelle des contrôles sur un formulaire le long de l’axe Z (profondeur) du formulaire. La fenêtre située en haut de l’ordre de plan chevauche toutes les autres fenêtres. Toutes les autres fenêtres chevauchent la fenêtre en bas de l’ordre de plan.

## <a name="to-layer-controls-at-design-time"></a>Pour superposer des contrôles au moment du design

1. Sélectionnez un contrôle que vous souhaitez coucher.

2. Dans le menu **format** , pointez sur **ordre**, puis cliquez sur **mettre au premier plan** ou mettre à l' **arrière**-plan.

## <a name="to-layer-controls-programmatically"></a>Pour superposer des contrôles par programmation

- Utilisez les <xref:System.Windows.Forms.Control.BringToFront%2A> méthodes <xref:System.Windows.Forms.Control.SendToBack%2A> et pour manipuler l’ordre de plan des contrôles.

     Par exemple, si un <xref:System.Windows.Forms.TextBox> contrôle, `txtFirstName`, se trouve sous un autre contrôle et que vous souhaitez l’utiliser en premier, utilisez le code suivant:

    ```vb
    txtFirstName.BringToFront()
    ```

    ```csharp
    txtFirstName.BringToFront();
    ```

    ```cpp
    txtFirstName->BringToFront();
    ```

> [!NOTE]
> Windows Forms prend en charge la *relation contenant-contenu des contrôles*. La relation contenant-contenu de contrôle implique de placer un certain nombre de contrôles dans un contrôle conteneur <xref:System.Windows.Forms.RadioButton> , tel qu' <xref:System.Windows.Forms.GroupBox> un certain nombre de contrôles dans un contrôle. Vous pouvez ensuite superposer les contrôles dans le contrôle conteneur. Le déplacement de la zone de groupe déplace également les contrôles, car ils sont contenus à l’intérieur de celui-ci.

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Disposition des contrôles dans les Windows Forms](arranging-controls-on-windows-forms.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
