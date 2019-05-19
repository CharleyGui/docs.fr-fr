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
ms.openlocfilehash: f8fe28a7827c0f69f80a3078d604b1818f4134ac
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877420"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="0aae5-102">Procédure : définir une icône pour un bouton de barre d’outils à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="0aae5-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="0aae5-103">Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="0aae5-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="0aae5-104"><xref:System.Windows.Forms.ToolBar> boutons sont en mesure d’afficher des icônes pour faciliter l’identification par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="0aae5-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="0aae5-105">Cela s’effectue via l’ajout d’images à le <xref:System.Windows.Forms.ImageList> composant et son association avec la <xref:System.Windows.Forms.ToolBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="0aae5-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="0aae5-106">La procédure suivante nécessite un **Windows Application** projet avec un formulaire contenant un <xref:System.Windows.Forms.ToolBar> contrôle et un <xref:System.Windows.Forms.ImageList> composant.</span><span class="sxs-lookup"><span data-stu-id="0aae5-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="0aae5-107">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : Créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : Ajouter des contrôles aux Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0aae5-107">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aae5-108">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="0aae5-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0aae5-109">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="0aae5-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0aae5-110">Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0aae5-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="0aae5-111">Pour définir une icône pour un bouton de barre d’outils au moment du design</span><span class="sxs-lookup"><span data-stu-id="0aae5-111">To set an icon for a toolbar button at design time</span></span>  
  
1. <span data-ttu-id="0aae5-112">Ajouter des images à le <xref:System.Windows.Forms.ImageList> composant.</span><span class="sxs-lookup"><span data-stu-id="0aae5-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="0aae5-113">Pour plus d'informations, voir [Procédure : Ajouter ou supprimer des Images ImageList avec le concepteur](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="0aae5-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2. <span data-ttu-id="0aae5-114">Sélectionnez le <xref:System.Windows.Forms.ToolBar> contrôle sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="0aae5-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3. <span data-ttu-id="0aae5-115">Dans le **propriétés** fenêtre, définissez la <xref:System.Windows.Forms.ToolBar> du contrôle <xref:System.Windows.Forms.ToolBar.ImageList%2A> propriété le <xref:System.Windows.Forms.ImageList> composant.</span><span class="sxs-lookup"><span data-stu-id="0aae5-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4.  <span data-ttu-id="0aae5-116">Cliquez sur le <xref:System.Windows.Forms.ToolBar> du contrôle <xref:System.Windows.Forms.ToolBar.Buttons%2A> propriété pour le sélectionner, puis cliquez sur le bouton de sélection (![bouton les points de suspension (...) dans la fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) pour ouvrir le **ToolBarButton Collection Éditeur**.</span><span class="sxs-lookup"><span data-stu-id="0aae5-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5. <span data-ttu-id="0aae5-117">Utilisez le **ajouter** pour ajouter des boutons à la <xref:System.Windows.Forms.ToolBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="0aae5-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6. <span data-ttu-id="0aae5-118">Dans le **propriétés** fenêtre qui s’affiche dans le volet situé à droite de la **éditeur de collections ToolBarButton**, définissez le <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriété de chaque bouton de barre d’outils à une des valeurs dans la liste, qui est dessiné à partir d’images ajoutées à la <xref:System.Windows.Forms.ImageList> composant.</span><span class="sxs-lookup"><span data-stu-id="0aae5-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aae5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0aae5-119">See also</span></span>

- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="0aae5-120">Guide pratique pour Déclencher des événements de Menu pour les boutons de barre d’outils</span><span class="sxs-lookup"><span data-stu-id="0aae5-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [<span data-ttu-id="0aae5-121">ToolBar, contrôle</span><span class="sxs-lookup"><span data-stu-id="0aae5-121">ToolBar Control</span></span>](toolbar-control-windows-forms.md)
- [<span data-ttu-id="0aae5-122">ImageList, composant</span><span class="sxs-lookup"><span data-stu-id="0aae5-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)
