---
title: 'Procédure : ajouter ou supprimer des images ImageList avec le concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 63692a797ad49f0adc3a0c5b0bfff1aebbc65257
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038270"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="33e92-102">Procédure : ajouter ou supprimer des images ImageList avec le concepteur</span><span class="sxs-lookup"><span data-stu-id="33e92-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="33e92-103">Vous pouvez ajouter des images à <xref:System.Windows.Forms.ImageList> un composant de plusieurs façons différentes.</span><span class="sxs-lookup"><span data-stu-id="33e92-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="33e92-104">Vous pouvez ajouter des images très rapidement à l’aide de la balise <xref:System.Windows.Forms.ImageList>active associée au ou, si vous définissez plusieurs autres propriétés <xref:System.Windows.Forms.ImageList>sur le, il peut s’avérer plus pratique d’ajouter des images avec le fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="33e92-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="33e92-105">Vous pouvez également ajouter des images à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="33e92-105">You can also add images by using code.</span></span> <span data-ttu-id="33e92-106">Pour plus d’informations sur l’ajout d’images avec du code [, consultez Procédure: Ajoutez ou supprimez des images avec le composant](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)ImageList Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="33e92-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="33e92-107">En général, vous <xref:System.Windows.Forms.ImageList> remplissez le composant avec des images avant qu’il ne soit associé à un contrôle, mais cela n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="33e92-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>


### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="33e92-108">Pour ajouter ou supprimer des images à l’aide de l’Fenêtre Propriétés</span><span class="sxs-lookup"><span data-stu-id="33e92-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="33e92-109">Sélectionnez le <xref:System.Windows.Forms.ImageList> composant ou ajoutez-en un au formulaire.</span><span class="sxs-lookup"><span data-stu-id="33e92-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="33e92-110">Dans la fenêtre Propriétés, cliquez sur le bouton de![sélection (le bouton de sélection (...) dans le fenêtre Propriétés de](./media/visual-studio-ellipsis-button.png)Visual Studio.) <xref:System.Windows.Forms.ImageList.Images%2A> en regard de la propriété.</span><span class="sxs-lookup"><span data-stu-id="33e92-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="33e92-111">Dans l' **éditeur de collections d’images**, cliquez sur **Ajouter** ou **supprimer** pour ajouter ou supprimer des images dans la liste.</span><span class="sxs-lookup"><span data-stu-id="33e92-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="33e92-112">Pour ajouter ou supprimer des images à l’aide de la balise active</span><span class="sxs-lookup"><span data-stu-id="33e92-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="33e92-113">Sélectionnez le <xref:System.Windows.Forms.ImageList> composant ou ajoutez-en un au formulaire.</span><span class="sxs-lookup"><span data-stu-id="33e92-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="33e92-114">Cliquer sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="33e92-114">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>

3. <span data-ttu-id="33e92-115">Dans la boîte de dialogue **tâches ImageList** , sélectionnez **choisir les images**.</span><span class="sxs-lookup"><span data-stu-id="33e92-115">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="33e92-116">Dans l **'éditeur de collections images** , cliquez sur **Ajouter** ou sur **supprimer** pour ajouter ou supprimer des images dans la liste.</span><span class="sxs-lookup"><span data-stu-id="33e92-116">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="33e92-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33e92-117">See also</span></span>

- [<span data-ttu-id="33e92-118">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="33e92-118">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="33e92-119">Procédure pas à pas : Exécution de tâches courantes à l’aide de balises actives sur des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33e92-119">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="33e92-120">ImageList, composant</span><span class="sxs-lookup"><span data-stu-id="33e92-120">ImageList Component</span></span>](imagelist-component-windows-forms.md)
