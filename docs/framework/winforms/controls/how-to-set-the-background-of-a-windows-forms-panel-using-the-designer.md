---
title: Définir l’arrière-plan d’un panneau à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731922"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a><span data-ttu-id="a7aa4-102">Comment : définir l’arrière-plan d’un panneau Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="a7aa4-102">How to: Set the background of a Windows Forms panel using the Designer</span></span>

<span data-ttu-id="a7aa4-103">Un contrôle Windows Forms <xref:System.Windows.Forms.Panel> peut afficher une couleur d’arrière-plan et une image d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="a7aa4-104">La propriété <xref:System.Windows.Forms.Control.BackColor%2A> définit la couleur d’arrière-plan des contrôles contenus dans le panneau, tels que les étiquettes et les cases d’option.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for controls that are contained in the panel, such as labels and radio buttons.</span></span> <span data-ttu-id="a7aa4-105">Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> n’est pas définie, la sélection <xref:System.Windows.Forms.Control.BackColor%2A> remplit tout le panneau.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill all of the panel.</span></span> <span data-ttu-id="a7aa4-106">Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> est définie, l’image s’affiche derrière les contrôles contenus dans le panneau.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the controls that are contained in the panel.</span></span>

<span data-ttu-id="a7aa4-107">La procédure suivante requiert un projet d' **application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-107">The following procedure requires a **Windows Application** project with a form that contains a <xref:System.Windows.Forms.Panel> control.</span></span> <span data-ttu-id="a7aa4-108">Pour plus d’informations sur la façon de configurer un tel projet dans Visual Studio, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a7aa4-108">For information about how to set up such a project in Visual Studio, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="set-the-background-in-the-windows-forms-designer"></a><span data-ttu-id="a7aa4-109">Définir l’arrière-plan dans le Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7aa4-109">Set the background in the Windows Forms Designer</span></span>

1. <span data-ttu-id="a7aa4-110">Ouvrez le projet dans Visual Studio et sélectionnez le contrôle <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-110">Open the project in Visual Studio and select the <xref:System.Windows.Forms.Panel> control.</span></span>

2. <span data-ttu-id="a7aa4-111">Dans la fenêtre **Propriétés** , cliquez sur le bouton fléché en regard de la propriété <xref:System.Windows.Forms.Control.BackColor%2A> pour afficher une fenêtre avec trois onglets.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-111">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackColor%2A> property to display a window with three tabs.</span></span>

3. <span data-ttu-id="a7aa4-112">Sélectionnez l’onglet **personnalisé** pour afficher une palette de couleurs.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-112">Select the **Custom** tab to display a palette of colors.</span></span>

4. <span data-ttu-id="a7aa4-113">Sélectionnez l’onglet **Web** ou **système** pour afficher une liste de noms prédéfinis pour les couleurs, puis sélectionnez une couleur.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-113">Select the **Web** or **System** tab to display a list of predefined names for colors, and then select a color.</span></span>

5. <span data-ttu-id="a7aa4-114">Dans la fenêtre **Propriétés** , cliquez sur le bouton fléché en regard de la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-114">In the **Properties** window, click the arrow button next to the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property.</span></span>

6. <span data-ttu-id="a7aa4-115">Dans la boîte de dialogue **ouvrir** , sélectionnez le fichier que vous souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="a7aa4-115">In the **Open** dialog box, select the file that you want to display.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7aa4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7aa4-116">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="a7aa4-117">Panel, contrôle</span><span class="sxs-lookup"><span data-stu-id="a7aa4-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="a7aa4-118">Vue d’ensemble du contrôle Panel</span><span class="sxs-lookup"><span data-stu-id="a7aa4-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="a7aa4-119">Guide pratique pour grouper les contrôles avec le contrôle Panel Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="a7aa4-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](group-controls-with-wf-panel-control-using-the-designer.md)
