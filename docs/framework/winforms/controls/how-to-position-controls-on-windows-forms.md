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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1cc2cb4c749b7290a6edf914a8e6a697006ef43c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987073"
---
# <a name="how-to-position-controls-on-windows-forms"></a>Procédure : Positionner les contrôles sur Windows Forms

Pour positionner des contrôles, utilisez la Concepteur Windows Forms dans Visual Studio ou spécifiez la <xref:System.Windows.Forms.Control.Location%2A> propriété.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Positionner un contrôle sur l’aire de conception de l’Concepteur Windows Forms

Dans Visual Studio, faites glisser le contrôle vers l’emplacement approprié à l’aide de la souris.

> [!NOTE]
> Sélectionnez le contrôle et déplacez-le avec les touches de direction pour le positionner plus précisément. En outre, les *lignes d’alignement* vous aident à placer des contrôles avec précision dans votre formulaire. Pour plus d’informations, consultez [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)l’aide des lignes d’alignement.

## <a name="position-a-control-using-the-properties-window"></a>Positionner un contrôle à l’aide de l’Fenêtre Propriétés

1. Dans Visual Studio, sélectionnez le contrôle que vous souhaitez positionner.

2. Dans la fenêtre **Propriétés** , entrez les valeurs de <xref:System.Windows.Forms.Control.Location%2A> la propriété, séparées par une virgule, pour positionner le contrôle dans son conteneur.

   Le premier nombre (X) est la distance par rapport à la bordure gauche du conteneur. le deuxième nombre (Y) est la distance entre la bordure supérieure de la zone de conteneur, mesurée en pixels.

   > [!NOTE]
   > Vous pouvez développer la <xref:System.Windows.Forms.Control.Location%2A> propriété pour taper les valeurs **X** et **Y** individuellement.

## <a name="position-a-control-programmatically"></a>Positionner un contrôle par programmation

1. <xref:System.Windows.Forms.Control.Location%2A> Affectez<xref:System.Drawing.Point>à la propriété du contrôle la valeur.

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. Modifiez la coordonnée X de l’emplacement du contrôle <xref:System.Windows.Forms.Control.Left%2A> à l’aide de la sous-propriété.

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a>Incrémenter l’emplacement d’un contrôle par programme

Définissez la <xref:System.Windows.Forms.Control.Left%2A> sous-propriété pour incrémenter la coordonnée X du contrôle.

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
> Utilisez la <xref:System.Windows.Forms.Control.Location%2A> propriété pour définir simultanément les positions X et Y d’un contrôle. Pour définir une position individuellement, utilisez la sous- <xref:System.Windows.Forms.Control.Left%2A> propriété (**X**) <xref:System.Windows.Forms.Control.Top%2A> ou (**Y**) du contrôle. N’essayez pas de définir implicitement les coordonnées X et Y de la <xref:System.Drawing.Point> structure qui représente l’emplacement du bouton, car cette structure contient une copie des coordonnées du bouton.

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide de lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
- [Guide pratique : Définir l’emplacement de l’écran de Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
