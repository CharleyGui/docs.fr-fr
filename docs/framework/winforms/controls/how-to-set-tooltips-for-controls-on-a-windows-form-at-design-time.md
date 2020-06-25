---
title: "Comment : définir des info-bulles pour les contrôles d'un Windows Form au moment du design"
description: Découvrez comment définir des info-bulles pour les contrôles par programmation ou dans le Concepteur Windows Forms dans Visual Studio.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325974"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>Comment : définir des info-bulles pour les contrôles d’un Windows Form au moment du design

Vous pouvez définir une <xref:System.Windows.Forms.ToolTip> chaîne dans le code ou dans le Concepteur Windows Forms dans Visual Studio. Pour plus d’informations sur le <xref:System.Windows.Forms.ToolTip> composant, consultez [vue d’ensemble du composant ToolTip](tooltip-component-overview-windows-forms.md).

## <a name="set-a-tooltip-programmatically"></a>Définir une info-bulle par programmation

1. Ajoutez le contrôle qui affichera l’info-bulle.

2. Utilisez la <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> méthode du <xref:System.Windows.Forms.ToolTip> composant.

    ```vb
    ' In this example, Button1 is the control to display the ToolTip.
    ToolTip1.SetToolTip(Button1, "Save changes")
    ```

    ```csharp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1.SetToolTip(button1, "Save changes");
    ```

    ```cpp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1->SetToolTip(button1, "Save changes");
    ```

## <a name="set-a-tooltip-in-the-designer"></a>Définir une info-bulle dans le concepteur

1. Dans Visual Studio, ajoutez un <xref:System.Windows.Forms.ToolTip> composant au formulaire.

2. Sélectionnez le contrôle qui affichera l’info-bulle ou ajoutez-le au formulaire.

3. Dans la fenêtre **Propriétés** , affectez à l' **info-bulle de** la valeur ToolTip1 une chaîne de texte appropriée.

### <a name="to-remove-a-tooltip-programmatically"></a>Pour supprimer une info-bulle par programmation

1. Utilisez la <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> méthode du <xref:System.Windows.Forms.ToolTip> composant.

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a>Supprimer une info-bulle dans le concepteur

1. Dans Visual Studio, sélectionnez le contrôle qui affiche l’info-bulle.

2. Dans la fenêtre **Propriétés** , supprimez le texte de l' **info-bulle sur ToolTip1**.

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble du composant ToolTip](tooltip-component-overview-windows-forms.md)
- [Comment : modifier la durée avant affichage du composant ToolTip Windows Forms](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip, composant](tooltip-component-windows-forms.md)
