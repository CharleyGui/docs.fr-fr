---
title: positionner des contrôles
description: Découvrez comment utiliser la Concepteur Windows Forms dans Visual Studio ou la propriété Location pour positionner vos contrôles.
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
ms.openlocfilehash: 0aa3faade71e0f7e0a9d5e676327a80747524b8c
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904297"
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="a6898-103">Comment : positionner des contrôles sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6898-103">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="a6898-104">Pour positionner des contrôles, utilisez la Concepteur Windows Forms dans Visual Studio ou spécifiez la <xref:System.Windows.Forms.Control.Location%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="a6898-104">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="a6898-105">Positionner un contrôle sur l’aire de conception de l’Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6898-105">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="a6898-106">Dans Visual Studio, faites glisser le contrôle vers l’emplacement approprié à l’aide de la souris.</span><span class="sxs-lookup"><span data-stu-id="a6898-106">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="a6898-107">Sélectionnez le contrôle et déplacez-le avec les touches de direction pour le positionner plus précisément.</span><span class="sxs-lookup"><span data-stu-id="a6898-107">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="a6898-108">En outre, les *lignes d’alignement* vous aident à placer des contrôles avec précision dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="a6898-108">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="a6898-109">Pour plus d’informations, consultez [procédure pas à pas : Organisation des contrôles sur Windows Forms à l’aide des lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="a6898-109">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="a6898-110">Positionner un contrôle à l’aide de l’Fenêtre Propriétés</span><span class="sxs-lookup"><span data-stu-id="a6898-110">Position a control using the Properties window</span></span>

1. <span data-ttu-id="a6898-111">Dans Visual Studio, sélectionnez le contrôle que vous souhaitez positionner.</span><span class="sxs-lookup"><span data-stu-id="a6898-111">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="a6898-112">Dans la fenêtre **Propriétés** , entrez les valeurs de la <xref:System.Windows.Forms.Control.Location%2A> propriété, séparées par une virgule, pour positionner le contrôle dans son conteneur.</span><span class="sxs-lookup"><span data-stu-id="a6898-112">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="a6898-113">Le premier nombre (X) est la distance par rapport à la bordure gauche du conteneur. le deuxième nombre (Y) est la distance entre la bordure supérieure de la zone de conteneur, mesurée en pixels.</span><span class="sxs-lookup"><span data-stu-id="a6898-113">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a6898-114">Vous pouvez développer la <xref:System.Windows.Forms.Control.Location%2A> propriété pour taper les valeurs **X** et **Y** individuellement.</span><span class="sxs-lookup"><span data-stu-id="a6898-114">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="a6898-115">Positionner un contrôle par programmation</span><span class="sxs-lookup"><span data-stu-id="a6898-115">Position a control programmatically</span></span>

1. <span data-ttu-id="a6898-116">Affectez <xref:System.Windows.Forms.Control.Location%2A> à la propriété du contrôle la valeur <xref:System.Drawing.Point> .</span><span class="sxs-lookup"><span data-stu-id="a6898-116">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="a6898-117">Modifiez la coordonnée X de l’emplacement du contrôle à l’aide de la sous- <xref:System.Windows.Forms.Control.Left%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="a6898-117">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="a6898-118">Incrémenter l’emplacement d’un contrôle par programme</span><span class="sxs-lookup"><span data-stu-id="a6898-118">Increment a control's location programmatically</span></span>

<span data-ttu-id="a6898-119">Définissez la sous- <xref:System.Windows.Forms.Control.Left%2A> propriété pour incrémenter la coordonnée X du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a6898-119">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="a6898-120">Utilisez la <xref:System.Windows.Forms.Control.Location%2A> propriété pour définir simultanément les positions X et Y d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="a6898-120">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="a6898-121">Pour définir une position individuellement, utilisez la sous- <xref:System.Windows.Forms.Control.Left%2A> propriété (**X**) ou <xref:System.Windows.Forms.Control.Top%2A> (**Y**) du contrôle.</span><span class="sxs-lookup"><span data-stu-id="a6898-121">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="a6898-122">N’essayez pas de définir implicitement les coordonnées X et Y de la <xref:System.Drawing.Point> structure qui représente l’emplacement du bouton, car cette structure contient une copie des coordonnées du bouton.</span><span class="sxs-lookup"><span data-stu-id="a6898-122">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6898-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6898-123">See also</span></span>

- [<span data-ttu-id="a6898-124">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6898-124">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="a6898-125">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement (SnapLines)</span><span class="sxs-lookup"><span data-stu-id="a6898-125">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="a6898-126">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a6898-126">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="a6898-127">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="a6898-127">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="a6898-128">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6898-128">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="a6898-129">Contrôles à utiliser sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6898-129">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="a6898-130">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a6898-130">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="a6898-131">[Comment : définir l'emplacement à l'écran des Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a6898-131">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
