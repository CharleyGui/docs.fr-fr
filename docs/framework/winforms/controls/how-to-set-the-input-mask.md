---
title: 'Procédure : définir le masque d’entrée'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949149"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="c776f-102">Procédure : définir le masque d’entrée</span><span class="sxs-lookup"><span data-stu-id="c776f-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="c776f-103">Le contrôle de zone de texte masquée est un contrôle de zone de texte amélioré qui prend en charge une syntaxe déclarative pour accepter ou rejeter les entrées d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c776f-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="c776f-104">En définissant la propriété Mask, vous pouvez spécifier l’entrée utilisateur autorisée sans écrire de logique de validation personnalisée dans votre application.</span><span class="sxs-lookup"><span data-stu-id="c776f-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="c776f-105">Pour plus d’informations, consultez la section Notes de <xref:System.Windows.Forms.MaskedTextBox> la classe.</span><span class="sxs-lookup"><span data-stu-id="c776f-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="c776f-106">Définition manuelle de la propriété Mask</span><span class="sxs-lookup"><span data-stu-id="c776f-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="c776f-107">Si vous êtes familiarisé avec les caractères pris en charge par la propriété Mask, vous pouvez l’entrer manuellement.</span><span class="sxs-lookup"><span data-stu-id="c776f-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="c776f-108">Pour obtenir un résumé des caractères pris en charge par la propriété Mask, consultez la section Notes <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c776f-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="c776f-109">Pour définir manuellement la propriété Mask</span><span class="sxs-lookup"><span data-stu-id="c776f-109">To set the Mask property manually</span></span>  
  
1. <span data-ttu-id="c776f-110">En mode **conception** , sélectionnez un <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="c776f-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2. <span data-ttu-id="c776f-111">Dans la fenêtre **Propriétés** , recherchez la <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c776f-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3. <span data-ttu-id="c776f-112">Tapez le masque de votre choix.</span><span class="sxs-lookup"><span data-stu-id="c776f-112">Type the mask that you want.</span></span> <span data-ttu-id="c776f-113">Par exemple, tapez `###`.</span><span class="sxs-lookup"><span data-stu-id="c776f-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="c776f-114">Utilisation de la boîte de dialogue masque de saisie</span><span class="sxs-lookup"><span data-stu-id="c776f-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="c776f-115">La boîte de dialogue masque de saisie fournit des masques d’entrée prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="c776f-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="c776f-116">Vous pouvez également modifier les masques prédéfinis ou entrer votre propre masque manuellement.</span><span class="sxs-lookup"><span data-stu-id="c776f-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="c776f-117">Pour ouvrir la boîte de dialogue masque de saisie</span><span class="sxs-lookup"><span data-stu-id="c776f-117">To open the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="c776f-118">En mode **conception** , sélectionnez un <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="c776f-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1. <span data-ttu-id="c776f-119">Cliquez sur la balise active pour ouvrir le panneau **tâches MaskedTextBox** .</span><span class="sxs-lookup"><span data-stu-id="c776f-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2. <span data-ttu-id="c776f-120">Cliquez sur **définir un masque**.</span><span class="sxs-lookup"><span data-stu-id="c776f-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="c776f-121">\- ou -</span><span class="sxs-lookup"><span data-stu-id="c776f-121">\- or -</span></span>  
  
    1. <span data-ttu-id="c776f-122">Dans la fenêtre **Propriétés** , sélectionnez la <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c776f-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2. <span data-ttu-id="c776f-123">Cliquez sur le bouton de sélection dans la colonne valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c776f-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="c776f-124">La boîte de dialogue **masque de saisie** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c776f-124">The **Input Mask** dialog box appears.</span></span>  
  
### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="c776f-125">Pour utiliser la boîte de dialogue masque de saisie</span><span class="sxs-lookup"><span data-stu-id="c776f-125">To use the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="c776f-126">Facultatif Cliquez sur l’un des masques prédéfinis dans la liste.</span><span class="sxs-lookup"><span data-stu-id="c776f-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2. <span data-ttu-id="c776f-127">Facultatif Modifiez le masque prédéfini dans la zone **masque** .</span><span class="sxs-lookup"><span data-stu-id="c776f-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3. <span data-ttu-id="c776f-128">Facultatif Tapez un nouveau masque dans la zone **masque** .</span><span class="sxs-lookup"><span data-stu-id="c776f-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="c776f-129">Autrement dit, il n’est pas nécessaire d’utiliser l’un des masques prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="c776f-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c776f-130">La zone aperçu affiche les caractères que l’utilisateur voit dans le <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="c776f-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="c776f-131">Ces caractères sont un guide permettant à l’utilisateur d’entrer les données correctement.</span><span class="sxs-lookup"><span data-stu-id="c776f-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4. <span data-ttu-id="c776f-132">Activez ou désactivez la case à cocher **Utiliser ValidatingType** .</span><span class="sxs-lookup"><span data-stu-id="c776f-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="c776f-133">La case à cocher **utiliser le ValidatingType** spécifie si un type de données est utilisé pour vérifier les données entrées par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c776f-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="c776f-134">Pour plus d'informations, consultez la propriété <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c776f-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5. <span data-ttu-id="c776f-135">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c776f-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="c776f-136">Le masque est entré dans la propriété **masque** de la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="c776f-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c776f-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c776f-137">See also</span></span>

- [<span data-ttu-id="c776f-138">Procédure pas à pas : Utilisation du contrôle MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="c776f-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
