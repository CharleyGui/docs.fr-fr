---
title: mettre en couche des objets
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1615b9c4df222edd95cda9bceae622ba6f1d8d78
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736337"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Comment : superposer des objets sur Windows Forms

Lorsque vous créez une interface utilisateur complexe ou que vous utilisez un formulaire d’interface multidocument (MDI), vous souhaiterez souvent superposer les contrôles et les formulaires enfants pour créer des interfaces utilisateur plus complexes. Pour déplacer et suivre les contrôles et les fenêtres dans le contexte d’un groupe, vous manipulez leur *ordre de plan*. L’ordre de plan est la superposition visuelle des contrôles sur un formulaire le long de l’axe z (profondeur) du formulaire. La fenêtre située en haut de l’ordre de plan chevauche toutes les autres fenêtres. Toutes les autres fenêtres chevauchent la fenêtre en bas de l’ordre de plan.

## <a name="to-layer-controls-at-design-time"></a>Pour superposer des contrôles au moment du design

1. Dans Visual Studio, sélectionnez un contrôle que vous souhaitez superposer.

2. Dans le menu **format** , sélectionnez **ordre**, puis sélectionnez **mettre au premier plan ou mettre** à l' **arrière**-plan.

## <a name="to-layer-controls-programmatically"></a>Pour superposer des contrôles par programmation

Utilisez les méthodes <xref:System.Windows.Forms.Control.BringToFront%2A> et <xref:System.Windows.Forms.Control.SendToBack%2A> pour manipuler l’ordre de plan des contrôles.

Par exemple, si un contrôle <xref:System.Windows.Forms.TextBox>, `txtFirstName`se trouve sous un autre contrôle et que vous souhaitez l’utiliser en premier, utilisez le code suivant :

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
> Windows Forms prend en charge la *relation contenant-contenu des contrôles*. La relation contenant-contenu de contrôle implique de placer un certain nombre de contrôles dans un contrôle conteneur, par exemple un certain nombre de contrôles <xref:System.Windows.Forms.RadioButton> dans un contrôle <xref:System.Windows.Forms.GroupBox>. Vous pouvez ensuite superposer les contrôles dans le contrôle conteneur. Le déplacement de la zone de groupe déplace également les contrôles, car ils sont contenus à l’intérieur de celui-ci.

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
