---
title: 'Procédure : modifier l’aspect du contrôle TabControl Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: e8ab97c545577dd393fd7d9844b396973621e6a7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650857"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="45ff3-102">Procédure : modifier l’aspect du contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45ff3-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="45ff3-103">Vous pouvez modifier l’apparence des onglets dans les Windows Forms à l’aide des propriétés de la <xref:System.Windows.Forms.TabControl> et <xref:System.Windows.Forms.TabPage> objets qui composent les différents onglets du contrôle.</span><span class="sxs-lookup"><span data-stu-id="45ff3-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="45ff3-104">En définissant ces propriétés, vous pouvez afficher des images sur les onglets, afficher des onglets verticalement plutôt qu’horizontalement, afficher plusieurs lignes d’onglets et activer ou désactiver les onglets par programmation.</span><span class="sxs-lookup"><span data-stu-id="45ff3-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="45ff3-105">Pour afficher une icône sur la partie de l’étiquette d’un onglet</span><span class="sxs-lookup"><span data-stu-id="45ff3-105">To display an icon on the label part of a tab</span></span>  
  
1. <span data-ttu-id="45ff3-106">Ajouter un <xref:System.Windows.Forms.ImageList> contrôle au formulaire.</span><span class="sxs-lookup"><span data-stu-id="45ff3-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2. <span data-ttu-id="45ff3-107">Ajouter des images à la liste d’images.</span><span class="sxs-lookup"><span data-stu-id="45ff3-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="45ff3-108">Pour plus d’informations sur les listes d’images, consultez [composant ImageList](imagelist-component-windows-forms.md) et [Comment : Ajouter ou supprimer des Images avec les Windows Forms composant ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="45ff3-108">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3. <span data-ttu-id="45ff3-109">Définir le <xref:System.Windows.Forms.TabControl.ImageList%2A> propriété de la <xref:System.Windows.Forms.TabControl> à la <xref:System.Windows.Forms.ImageList> contrôle.</span><span class="sxs-lookup"><span data-stu-id="45ff3-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4. <span data-ttu-id="45ff3-110">Définir le <xref:System.Windows.Forms.TabPage.ImageIndex%2A> propriété de la <xref:System.Windows.Forms.TabPage> à l’index d’une image appropriée dans la liste.</span><span class="sxs-lookup"><span data-stu-id="45ff3-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="45ff3-111">Pour créer plusieurs lignes d’onglets</span><span class="sxs-lookup"><span data-stu-id="45ff3-111">To create multiple rows of tabs</span></span>  
  
1. <span data-ttu-id="45ff3-112">Ajoutez le nombre de pages d’onglets.</span><span class="sxs-lookup"><span data-stu-id="45ff3-112">Add the number of tab pages you want.</span></span>  
  
2. <span data-ttu-id="45ff3-113">Définir le <xref:System.Windows.Forms.TabControl.Multiline%2A> propriété de la <xref:System.Windows.Forms.TabControl> à `true`.</span><span class="sxs-lookup"><span data-stu-id="45ff3-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3. <span data-ttu-id="45ff3-114">Si les onglets n’apparaissent pas déjà dans plusieurs lignes, définissez la <xref:System.Windows.Forms.Control.Width%2A> propriété de la <xref:System.Windows.Forms.TabControl> à être plus restrictif que tous les onglets.</span><span class="sxs-lookup"><span data-stu-id="45ff3-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="45ff3-115">Pour réorganiser les onglets sur le côté du contrôle</span><span class="sxs-lookup"><span data-stu-id="45ff3-115">To arrange tabs on the side of the control</span></span>  
  
- <span data-ttu-id="45ff3-116">Définir le <xref:System.Windows.Forms.TabControl.Alignment%2A> propriété de la <xref:System.Windows.Forms.TabControl> à <xref:System.Windows.Forms.TabAlignment.Left> ou <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="45ff3-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="45ff3-117">Pour activer ou désactiver tous les contrôles sur un onglet par programme</span><span class="sxs-lookup"><span data-stu-id="45ff3-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1. <span data-ttu-id="45ff3-118">Définir le <xref:System.Windows.Forms.TabPage.Enabled%2A> propriété de la <xref:System.Windows.Forms.TabPage> à `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="45ff3-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="45ff3-119">Pour afficher les onglets sous forme de boutons</span><span class="sxs-lookup"><span data-stu-id="45ff3-119">To display tabs as buttons</span></span>  
  
- <span data-ttu-id="45ff3-120">Définir le <xref:System.Windows.Forms.TabControl.Appearance%2A> propriété de la <xref:System.Windows.Forms.TabControl> à <xref:System.Windows.Forms.TabAppearance.Buttons> ou <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="45ff3-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ff3-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45ff3-121">See also</span></span>

- [<span data-ttu-id="45ff3-122">TabControl, contrôle</span><span class="sxs-lookup"><span data-stu-id="45ff3-122">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="45ff3-123">Vue d’ensemble du contrôle TabControl</span><span class="sxs-lookup"><span data-stu-id="45ff3-123">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="45ff3-124">Guide pratique pour Ajouter un contrôle à une Page d’onglets</span><span class="sxs-lookup"><span data-stu-id="45ff3-124">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="45ff3-125">Guide pratique pour Désactiver les Pages d’onglets</span><span class="sxs-lookup"><span data-stu-id="45ff3-125">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="45ff3-126">Guide pratique pour Ajouter et supprimer des onglets avec le contrôle TabControl de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45ff3-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
