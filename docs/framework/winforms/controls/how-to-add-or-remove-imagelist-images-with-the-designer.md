---
title: 'Comment : ajouter ou supprimer des images ImageList avec le concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: cdc7b563a0ee4f8779b99b4e9a6786e78f8d500f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628720"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="ba193-102">Comment : ajouter ou supprimer des images ImageList avec le concepteur</span><span class="sxs-lookup"><span data-stu-id="ba193-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="ba193-103">Vous pouvez ajouter des images à un composant <xref:System.Windows.Forms.ImageList> de plusieurs façons différentes.</span><span class="sxs-lookup"><span data-stu-id="ba193-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="ba193-104">Vous pouvez ajouter des images très rapidement à l’aide de la balise active associée au <xref:System.Windows.Forms.ImageList>ou, si vous définissez plusieurs autres propriétés sur le <xref:System.Windows.Forms.ImageList>, il peut s’avérer plus pratique d’ajouter des images avec le Fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="ba193-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="ba193-105">Vous pouvez également ajouter des images à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="ba193-105">You can also add images by using code.</span></span> <span data-ttu-id="ba193-106">Pour plus d’informations sur l’ajout d’images avec du code, consultez [Comment : ajouter ou supprimer des images avec le composant Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="ba193-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="ba193-107">En général, vous remplissez le composant <xref:System.Windows.Forms.ImageList> avec des images avant qu’il ne soit associé à un contrôle, mais cela n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ba193-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="ba193-108">Pour ajouter ou supprimer des images à l’aide de l’Fenêtre Propriétés</span><span class="sxs-lookup"><span data-stu-id="ba193-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="ba193-109">Sélectionnez le composant <xref:System.Windows.Forms.ImageList> ou ajoutez-en un au formulaire.</span><span class="sxs-lookup"><span data-stu-id="ba193-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="ba193-110">Dans l’Fenêtre Propriétés, cliquez sur le bouton de sélection (![le bouton de sélection (...) dans le Fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.ImageList.Images%2A>.</span><span class="sxs-lookup"><span data-stu-id="ba193-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="ba193-111">Dans l' **éditeur de collections d’images**, cliquez sur **Ajouter** ou **supprimer** pour ajouter ou supprimer des images dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ba193-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="ba193-112">Pour ajouter ou supprimer des images à l’aide de la balise active</span><span class="sxs-lookup"><span data-stu-id="ba193-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="ba193-113">Sélectionnez le composant <xref:System.Windows.Forms.ImageList> ou ajoutez-en un au formulaire.</span><span class="sxs-lookup"><span data-stu-id="ba193-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="ba193-114">Cliquez sur le glyphe actions du concepteur (</span><span class="sxs-lookup"><span data-stu-id="ba193-114">Click the designer actions glyph (</span></span>![Petite flèche noire](./media/designer-actions-glyph.gif)<span data-ttu-id="ba193-116">)</span><span class="sxs-lookup"><span data-stu-id="ba193-116">)</span></span>

3. <span data-ttu-id="ba193-117">Dans la boîte de dialogue **tâches ImageList** , sélectionnez **choisir les images**.</span><span class="sxs-lookup"><span data-stu-id="ba193-117">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="ba193-118">Dans l **'éditeur de collections images** , cliquez sur **Ajouter** ou sur **supprimer** pour ajouter ou supprimer des images dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ba193-118">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba193-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba193-119">See also</span></span>

- [<span data-ttu-id="ba193-120">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="ba193-120">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="ba193-121">Procédure pas à pas : effectuer des tâches courantes à l’aide d’actions de concepteur</span><span class="sxs-lookup"><span data-stu-id="ba193-121">Walkthrough: Perform common tasks using designer actions</span></span>](perform-common-tasks-design-actions.md)
- [<span data-ttu-id="ba193-122">ImageList, composant</span><span class="sxs-lookup"><span data-stu-id="ba193-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)
