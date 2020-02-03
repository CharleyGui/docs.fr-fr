---
title: Créer des clés d’accès avec des contrôles Label
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
ms.openlocfilehash: 800afc03e71435e2721456b93bb9704af01f714a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731053"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="05f6d-102">Comment : créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05f6d-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="05f6d-103">Windows Forms contrôles <xref:System.Windows.Forms.Label> peuvent être utilisés pour définir des clés d’accès pour d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="05f6d-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="05f6d-104">Lorsque vous définissez une clé d’accès dans un contrôle Label, l’utilisateur peut appuyer sur la touche ALT et le caractère que vous désignez pour déplacer le focus sur le contrôle qui le suit dans l’ordre de tabulation.</span><span class="sxs-lookup"><span data-stu-id="05f6d-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="05f6d-105">Étant donné que les étiquettes ne peuvent pas recevoir le focus, le focus se déplace automatiquement vers le contrôle suivant dans l’ordre de tabulation.</span><span class="sxs-lookup"><span data-stu-id="05f6d-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="05f6d-106">Utilisez cette technique pour affecter des clés d’accès à des zones de texte, des zones de liste modifiable, des zones de liste et des grilles de données.</span><span class="sxs-lookup"><span data-stu-id="05f6d-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="05f6d-107">Pour assigner une touche d’accès à un contrôle à l’aide d’une étiquette</span><span class="sxs-lookup"><span data-stu-id="05f6d-107">To assign an access key to a control with a label</span></span>  
  
1. <span data-ttu-id="05f6d-108">Dessinez d’abord l’étiquette, puis dessinez l’autre contrôle.</span><span class="sxs-lookup"><span data-stu-id="05f6d-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="05f6d-109">-ou-</span><span class="sxs-lookup"><span data-stu-id="05f6d-109">-or-</span></span>  
  
     <span data-ttu-id="05f6d-110">Dessinez les contrôles dans n’importe quel ordre et affectez à la propriété <xref:System.Windows.Forms.Control.TabIndex%2A> de l’étiquette une valeur inférieure à celle de l’autre contrôle.</span><span class="sxs-lookup"><span data-stu-id="05f6d-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2. <span data-ttu-id="05f6d-111">Affectez à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> de l’étiquette la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="05f6d-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="05f6d-112">Utilisez une esperluette (&) dans la propriété <xref:System.Windows.Forms.Label.Text%2A> de l’étiquette pour affecter la touche d’accès pour l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="05f6d-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="05f6d-113">Pour plus d’informations, consultez [création de clés d’accès pour les contrôles Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="05f6d-113">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="05f6d-114">Vous souhaiterez peut-être afficher les perluète dans un contrôle Label, plutôt que de les utiliser pour créer des clés d’accès.</span><span class="sxs-lookup"><span data-stu-id="05f6d-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="05f6d-115">Cela peut se produire si vous liez un contrôle Label à un champ d’un Recordset dans lequel les données incluent des esperluettes.</span><span class="sxs-lookup"><span data-stu-id="05f6d-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="05f6d-116">Pour afficher les perluète dans un contrôle Label, affectez à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="05f6d-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="05f6d-117">Si vous souhaitez afficher les perluète et une touche d’accès, affectez à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> la valeur `true` et indiquez la touche d’accès avec une esperluette (&) et l’esperluette (et commercial) à afficher avec deux signes « et ».</span><span class="sxs-lookup"><span data-stu-id="05f6d-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="05f6d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05f6d-118">See also</span></span>

- [<span data-ttu-id="05f6d-119">Guide pratique pour dimensionner un contrôle Label Windows Forms en fonction de son contenu</span><span class="sxs-lookup"><span data-stu-id="05f6d-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="05f6d-120">Vue d'ensemble du contrôle Label</span><span class="sxs-lookup"><span data-stu-id="05f6d-120">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="05f6d-121">Label, contrôle</span><span class="sxs-lookup"><span data-stu-id="05f6d-121">Label Control</span></span>](label-control-windows-forms.md)
