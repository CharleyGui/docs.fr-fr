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
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="8941d-102">Procédure : Positionner les contrôles sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8941d-102">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="8941d-103">Pour positionner des contrôles, utilisez la Concepteur Windows Forms dans Visual Studio ou spécifiez la <xref:System.Windows.Forms.Control.Location%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="8941d-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="8941d-104">Positionner un contrôle sur l’aire de conception de l’Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8941d-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="8941d-105">Dans Visual Studio, faites glisser le contrôle vers l’emplacement approprié à l’aide de la souris.</span><span class="sxs-lookup"><span data-stu-id="8941d-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="8941d-106">Sélectionnez le contrôle et déplacez-le avec les touches de direction pour le positionner plus précisément.</span><span class="sxs-lookup"><span data-stu-id="8941d-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="8941d-107">En outre, les *lignes d’alignement* vous aident à placer des contrôles avec précision dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="8941d-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="8941d-108">Pour plus d’informations, consultez [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)l’aide des lignes d’alignement.</span><span class="sxs-lookup"><span data-stu-id="8941d-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="8941d-109">Positionner un contrôle à l’aide de l’Fenêtre Propriétés</span><span class="sxs-lookup"><span data-stu-id="8941d-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="8941d-110">Dans Visual Studio, sélectionnez le contrôle que vous souhaitez positionner.</span><span class="sxs-lookup"><span data-stu-id="8941d-110">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="8941d-111">Dans la fenêtre **Propriétés** , entrez les valeurs de <xref:System.Windows.Forms.Control.Location%2A> la propriété, séparées par une virgule, pour positionner le contrôle dans son conteneur.</span><span class="sxs-lookup"><span data-stu-id="8941d-111">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="8941d-112">Le premier nombre (X) est la distance par rapport à la bordure gauche du conteneur. le deuxième nombre (Y) est la distance entre la bordure supérieure de la zone de conteneur, mesurée en pixels.</span><span class="sxs-lookup"><span data-stu-id="8941d-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="8941d-113">Vous pouvez développer la <xref:System.Windows.Forms.Control.Location%2A> propriété pour taper les valeurs **X** et **Y** individuellement.</span><span class="sxs-lookup"><span data-stu-id="8941d-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="8941d-114">Positionner un contrôle par programmation</span><span class="sxs-lookup"><span data-stu-id="8941d-114">Position a control programmatically</span></span>

1. <span data-ttu-id="8941d-115"><xref:System.Windows.Forms.Control.Location%2A> Affectez<xref:System.Drawing.Point>à la propriété du contrôle la valeur.</span><span class="sxs-lookup"><span data-stu-id="8941d-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="8941d-116">Modifiez la coordonnée X de l’emplacement du contrôle <xref:System.Windows.Forms.Control.Left%2A> à l’aide de la sous-propriété.</span><span class="sxs-lookup"><span data-stu-id="8941d-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="8941d-117">Incrémenter l’emplacement d’un contrôle par programme</span><span class="sxs-lookup"><span data-stu-id="8941d-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="8941d-118">Définissez la <xref:System.Windows.Forms.Control.Left%2A> sous-propriété pour incrémenter la coordonnée X du contrôle.</span><span class="sxs-lookup"><span data-stu-id="8941d-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="8941d-119">Utilisez la <xref:System.Windows.Forms.Control.Location%2A> propriété pour définir simultanément les positions X et Y d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="8941d-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="8941d-120">Pour définir une position individuellement, utilisez la sous- <xref:System.Windows.Forms.Control.Left%2A> propriété (**X**) <xref:System.Windows.Forms.Control.Top%2A> ou (**Y**) du contrôle.</span><span class="sxs-lookup"><span data-stu-id="8941d-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="8941d-121">N’essayez pas de définir implicitement les coordonnées X et Y de la <xref:System.Drawing.Point> structure qui représente l’emplacement du bouton, car cette structure contient une copie des coordonnées du bouton.</span><span class="sxs-lookup"><span data-stu-id="8941d-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="8941d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8941d-122">See also</span></span>

- [<span data-ttu-id="8941d-123">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8941d-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="8941d-124">Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide de lignes d’alignement</span><span class="sxs-lookup"><span data-stu-id="8941d-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="8941d-125">Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8941d-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="8941d-126">Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8941d-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="8941d-127">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8941d-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="8941d-128">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8941d-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="8941d-129">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8941d-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="8941d-130">[Guide pratique : Définir l’emplacement de l’écran de Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8941d-130">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
