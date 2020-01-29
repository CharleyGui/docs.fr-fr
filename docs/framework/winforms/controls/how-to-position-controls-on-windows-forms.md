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
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="7b455-102">Comment : positionner des contrôles sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b455-102">How to: Position controls on Windows Forms</span></span>

<span data-ttu-id="7b455-103">Pour positionner des contrôles, utilisez la Concepteur Windows Forms dans Visual Studio ou spécifiez la propriété <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b455-103">To position controls, use the Windows Forms Designer in Visual Studio or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="7b455-104">Positionner un contrôle sur l’aire de conception de l’Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b455-104">Position a control on the design surface of the Windows Forms Designer</span></span>

<span data-ttu-id="7b455-105">Dans Visual Studio, faites glisser le contrôle vers l’emplacement approprié à l’aide de la souris.</span><span class="sxs-lookup"><span data-stu-id="7b455-105">In Visual Studio, drag the control to the appropriate location with the mouse.</span></span>

> [!NOTE]
> <span data-ttu-id="7b455-106">Sélectionnez le contrôle et déplacez-le avec les touches de direction pour le positionner plus précisément.</span><span class="sxs-lookup"><span data-stu-id="7b455-106">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="7b455-107">En outre, les *lignes d’alignement* vous aident à placer des contrôles avec précision dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="7b455-107">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="7b455-108">Pour plus d’informations, consultez [procédure pas à pas : Organisation des contrôles sur Windows Forms à l’aide des lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="7b455-108">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

## <a name="position-a-control-using-the-properties-window"></a><span data-ttu-id="7b455-109">Positionner un contrôle à l’aide de l’Fenêtre Propriétés</span><span class="sxs-lookup"><span data-stu-id="7b455-109">Position a control using the Properties window</span></span>

1. <span data-ttu-id="7b455-110">Dans Visual Studio, sélectionnez le contrôle que vous souhaitez positionner.</span><span class="sxs-lookup"><span data-stu-id="7b455-110">In Visual Studio, select the control you want to position.</span></span>

2. <span data-ttu-id="7b455-111">Dans la fenêtre **Propriétés** , entrez les valeurs de la propriété <xref:System.Windows.Forms.Control.Location%2A>, séparées par une virgule, pour positionner le contrôle dans son conteneur.</span><span class="sxs-lookup"><span data-stu-id="7b455-111">In the **Properties** window, enter values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>

   <span data-ttu-id="7b455-112">Le premier nombre (X) est la distance par rapport à la bordure gauche du conteneur. le deuxième nombre (Y) est la distance entre la bordure supérieure de la zone de conteneur, mesurée en pixels.</span><span class="sxs-lookup"><span data-stu-id="7b455-112">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>

   > [!NOTE]
   > <span data-ttu-id="7b455-113">Vous pouvez développer la propriété <xref:System.Windows.Forms.Control.Location%2A> pour taper les valeurs **X** et **Y** individuellement.</span><span class="sxs-lookup"><span data-stu-id="7b455-113">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>

## <a name="position-a-control-programmatically"></a><span data-ttu-id="7b455-114">Positionner un contrôle par programmation</span><span class="sxs-lookup"><span data-stu-id="7b455-114">Position a control programmatically</span></span>

1. <span data-ttu-id="7b455-115">Affectez à la propriété <xref:System.Windows.Forms.Control.Location%2A> du contrôle la valeur d’une <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="7b455-115">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. <span data-ttu-id="7b455-116">Modifiez la coordonnée X de l’emplacement du contrôle à l’aide de la <xref:System.Windows.Forms.Control.Left%2A> sous-propriété.</span><span class="sxs-lookup"><span data-stu-id="7b455-116">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a><span data-ttu-id="7b455-117">Incrémenter l’emplacement d’un contrôle par programme</span><span class="sxs-lookup"><span data-stu-id="7b455-117">Increment a control's location programmatically</span></span>

<span data-ttu-id="7b455-118">Définissez la sous-propriété <xref:System.Windows.Forms.Control.Left%2A> pour incrémenter la coordonnée X du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7b455-118">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>

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
> <span data-ttu-id="7b455-119">Utilisez la propriété <xref:System.Windows.Forms.Control.Location%2A> pour définir les positions X et Y d’un contrôle simultanément.</span><span class="sxs-lookup"><span data-stu-id="7b455-119">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="7b455-120">Pour définir une position individuellement, utilisez la sous-propriété <xref:System.Windows.Forms.Control.Left%2A> (**X**) ou <xref:System.Windows.Forms.Control.Top%2A> (**Y**) du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7b455-120">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="7b455-121">N’essayez pas de définir implicitement les coordonnées X et Y de la structure <xref:System.Drawing.Point> qui représente l’emplacement du bouton, car cette structure contient une copie des coordonnées du bouton.</span><span class="sxs-lookup"><span data-stu-id="7b455-121">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b455-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b455-122">See also</span></span>

- [<span data-ttu-id="7b455-123">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b455-123">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="7b455-124">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement</span><span class="sxs-lookup"><span data-stu-id="7b455-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="7b455-125">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7b455-125">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="7b455-126">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7b455-126">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="7b455-127">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b455-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="7b455-128">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b455-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="7b455-129">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7b455-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- <span data-ttu-id="7b455-130">[Comment : définir l’emplacement à l’écran d’Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7b455-130">[How to: Set the Screen Location of Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))</span></span>
