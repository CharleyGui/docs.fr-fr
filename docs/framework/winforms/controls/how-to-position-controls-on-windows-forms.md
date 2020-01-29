---
title: positionner des contrôles
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 144a0021c74f0fb5afec1d511315168fb28528e9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735910"
---
# <a name="how-to-position-controls-on-windows-forms"></a>Comment : positionner des contrôles sur Windows Forms

Pour positionner des contrôles, utilisez la Concepteur Windows Forms dans Visual Studio ou spécifiez la propriété <xref:System.Windows.Forms.Control.Location%2A>.

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Positionner un contrôle sur l’aire de conception de l’Concepteur Windows Forms

Dans Visual Studio, faites glisser le contrôle vers l’emplacement approprié à l’aide de la souris.

> [!NOTE]
> Sélectionnez le contrôle et déplacez-le avec les touches de direction pour le positionner plus précisément. En outre, les *lignes d’alignement* vous aident à placer des contrôles avec précision dans votre formulaire. Pour plus d’informations, consultez [procédure pas à pas : Organisation des contrôles sur Windows Forms à l’aide des lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

## <a name="position-a-control-using-the-properties-window"></a>Positionner un contrôle à l’aide de l’Fenêtre Propriétés

1. Dans Visual Studio, sélectionnez le contrôle que vous souhaitez positionner.

2. Dans la fenêtre **Propriétés** , entrez les valeurs de la propriété <xref:System.Windows.Forms.Control.Location%2A>, séparées par une virgule, pour positionner le contrôle dans son conteneur.

   Le premier nombre (X) est la distance par rapport à la bordure gauche du conteneur. le deuxième nombre (Y) est la distance entre la bordure supérieure de la zone de conteneur, mesurée en pixels.

   > [!NOTE]
   > Vous pouvez développer la propriété <xref:System.Windows.Forms.Control.Location%2A> pour taper les valeurs **X** et **Y** individuellement.

## <a name="position-a-control-programmatically"></a>Positionner un contrôle par programmation

1. Affectez à la propriété <xref:System.Windows.Forms.Control.Location%2A> du contrôle la valeur d’une <xref:System.Drawing.Point>.

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

## <a name="increment-a-controls-location-programmatically"></a>Incrémenter l’emplacement d’un contrôle par programme

Définissez la sous-propriété <xref:System.Windows.Forms.Control.Left%2A> pour incrémenter la coordonnée X du contrôle.

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
> Utilisez la propriété <xref:System.Windows.Forms.Control.Location%2A> pour définir les positions X et Y d’un contrôle simultanément. Pour définir une position individuellement, utilisez la sous-propriété <xref:System.Windows.Forms.Control.Left%2A> (**X**) ou <xref:System.Windows.Forms.Control.Top%2A> (**Y**) du contrôle. N’essayez pas de définir implicitement les coordonnées X et Y de la structure <xref:System.Drawing.Point> qui représente l’emplacement du bouton, car cette structure contient une copie des coordonnées du bouton.

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
- [Comment : définir l’emplacement à l’écran d’Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
