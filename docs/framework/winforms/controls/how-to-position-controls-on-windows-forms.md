---
title: 'Procédure : positionner des contrôles dans des Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
ms.openlocfilehash: 241edbe60c327493c9123c6cf7bdc19b7ba2b724
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211653"
---
# <a name="how-to-position-controls-on-windows-forms"></a>Procédure : positionner des contrôles dans des Windows Forms

Pour positionner des contrôles, utiliser le Concepteur de formulaires Windows dans Visual Studio ou spécifiez le <xref:System.Windows.Forms.Control.Location%2A> propriété.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Positionner un contrôle sur l’aire de conception du Concepteur Windows Forms

Dans Visual Studio, faites glisser le contrôle vers l’emplacement approprié avec la souris.

> [!NOTE]
> Sélectionnez le contrôle et les déplacer avec la flèche touches pour positionner plus précisément. En outre, *les lignes d’alignement* vous aident à placer les contrôles avec précision sur votre formulaire. Pour plus d’informations, consultez [Procédure pas à pas : Organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

## <a name="position-a-control-using-the-properties-window"></a>Positionner un contrôle à l’aide de la fenêtre Propriétés

1. Dans Visual Studio, cliquez sur le contrôle que vous souhaitez positionner.

2. Dans le **propriétés** fenêtre, les valeurs de type pour le <xref:System.Windows.Forms.Control.Location%2A> propriété séparés par une virgule, pour positionner le contrôle dans son conteneur.

     Le premier nombre (X) est la distance entre la bordure gauche du conteneur ; le deuxième nombre (Y) est la distance entre la bordure supérieure de la zone conteneur, en pixels.

    > [!NOTE]
    > Vous pouvez développer le <xref:System.Windows.Forms.Control.Location%2A> propriété permettant de taper le **X** et **Y** valeurs individuellement.

## <a name="position-a-control-programmatically"></a>Positionner un contrôle par programmation

1. Définir le <xref:System.Windows.Forms.Control.Location%2A> propriété du contrôle à un <xref:System.Drawing.Point>.

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. Modifiez la coordonnée X de l’emplacement du contrôle à l’aide de la <xref:System.Windows.Forms.Control.Left%2A> sous-propriété.

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a>Incrémenter l’emplacement d’un contrôle par programmation

Définir le <xref:System.Windows.Forms.Control.Left%2A> sous-propriété pour incrémenter la coordonnée X du contrôle.

```vb
Button1.Left += 200
```

```csharp
button1.Left += 200;
```

```cpp
button1->Left += 200;
```

> [!NOTE]
> Utilisez le <xref:System.Windows.Forms.Control.Location%2A> propriété à définir d’un contrôle X et Y place simultanément. Pour définir une position individuellement, utilisez le contrôle <xref:System.Windows.Forms.Control.Left%2A> (**X**) ou <xref:System.Windows.Forms.Control.Top%2A> (**Y**) sous-propriété. N’essayez pas de définir implicitement les coordonnées X et Y de la <xref:System.Drawing.Point> structure qui représente la position du bouton, car cette structure contient une copie des coordonnées du bouton.

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Procédure pas à pas : Organisation des contrôles dans les formulaires de Windows à l’aide des lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Procédure pas à pas : Organisation des contrôles dans les formulaires de Windows à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : Organisation des contrôles dans les formulaires de Windows à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Disposition des contrôles dans les Windows Forms](arranging-controls-on-windows-forms.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
- [Guide pratique pour Définir l’emplacement de l’écran des Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
