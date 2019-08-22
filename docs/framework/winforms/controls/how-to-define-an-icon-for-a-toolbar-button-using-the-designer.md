---
title: 'Procédure : définir une icône pour un bouton de barre d’outils à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 49e93f12bebbf409e6b3a06634556b9103c85f44
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666205"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="1b578-102">Procédure : définir une icône pour un bouton de barre d’outils à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="1b578-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>

> [!NOTE]
> <span data-ttu-id="1b578-103">Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="1b578-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>

<span data-ttu-id="1b578-104"><xref:System.Windows.Forms.ToolBar>les boutons peuvent afficher des icônes pour faciliter leur identification par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="1b578-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="1b578-105">Pour ce faire, vous pouvez ajouter des <xref:System.Windows.Forms.ImageList> images au composant et les <xref:System.Windows.Forms.ToolBar> associer au contrôle.</span><span class="sxs-lookup"><span data-stu-id="1b578-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>

<span data-ttu-id="1b578-106">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.ToolBar> un contrôle et <xref:System.Windows.Forms.ImageList> un composant.</span><span class="sxs-lookup"><span data-stu-id="1b578-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="1b578-107">Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1b578-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="1b578-108">Pour définir une icône pour un bouton de barre d’outils au moment du design</span><span class="sxs-lookup"><span data-stu-id="1b578-108">To set an icon for a toolbar button at design time</span></span>

1. <span data-ttu-id="1b578-109">Ajoutez des <xref:System.Windows.Forms.ImageList> images au composant.</span><span class="sxs-lookup"><span data-stu-id="1b578-109">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="1b578-110">Pour plus d’informations, consultez [Guide pratique pour Ajoutez ou supprimez des images ImageList avec](how-to-add-or-remove-imagelist-images-with-the-designer.md)le concepteur.</span><span class="sxs-lookup"><span data-stu-id="1b578-110">For more information, see [How to: Add or Remove ImageList Images with the Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>

2. <span data-ttu-id="1b578-111">Sélectionnez le <xref:System.Windows.Forms.ToolBar> contrôle sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="1b578-111">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>

3. <span data-ttu-id="1b578-112">Dans la fenêtre **Propriétés** , définissez la <xref:System.Windows.Forms.ToolBar> propriété du <xref:System.Windows.Forms.ToolBar.ImageList%2A> contrôle sur le <xref:System.Windows.Forms.ImageList> composant.</span><span class="sxs-lookup"><span data-stu-id="1b578-112">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>

4. <span data-ttu-id="1b578-113">Cliquez sur <xref:System.Windows.Forms.ToolBar> la propriété <xref:System.Windows.Forms.ToolBar.Buttons%2A> du contrôle pour le sélectionner,![puis cliquez sur le bouton de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio](./media/visual-studio-ellipsis-button.png).) pour ouvrir l' **éditeur de collections ToolBarButton**.</span><span class="sxs-lookup"><span data-stu-id="1b578-113">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **ToolBarButton Collection Editor**.</span></span>

5. <span data-ttu-id="1b578-114">Utilisez le bouton **Ajouter** pour ajouter des <xref:System.Windows.Forms.ToolBar> boutons au contrôle.</span><span class="sxs-lookup"><span data-stu-id="1b578-114">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>

6. <span data-ttu-id="1b578-115">Dans la fenêtre **Propriétés** qui s’affiche dans le volet situé à droite de l' **éditeur de collections ToolBarButton**, affectez à la <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriété de chaque bouton de la barre d’outils l’une des valeurs de la liste, qui est tirée des images que vous avez ajoutées au <xref:System.Windows.Forms.ImageList> composant.</span><span class="sxs-lookup"><span data-stu-id="1b578-115">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b578-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b578-116">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="1b578-117">Guide pratique pour Déclencher des événements de menu pour les boutons de barre d’outils</span><span class="sxs-lookup"><span data-stu-id="1b578-117">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="1b578-118">ToolBar, contrôle</span><span class="sxs-lookup"><span data-stu-id="1b578-118">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="1b578-119">ImageList, composant</span><span class="sxs-lookup"><span data-stu-id="1b578-119">ImageList Component</span></span>](imagelist-component-windows-forms.md)
