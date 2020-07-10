---
title: Afficher plusieurs lignes dans le contrôle TextBox
description: Découvrez comment afficher plusieurs lignes dans le contrôle Windows Forms zone de texte en définissant les propriétés Multiline, WordWrap et ScrollBars.
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174469"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="40ddd-103">Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40ddd-103">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="40ddd-104">Par défaut, le <xref:System.Windows.Forms.TextBox> contrôle Windows Forms affiche une seule ligne de texte et n’affiche pas de barres de défilement.</span><span class="sxs-lookup"><span data-stu-id="40ddd-104">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="40ddd-105">Si le texte est plus long que l’espace disponible, seule une partie du texte est visible.</span><span class="sxs-lookup"><span data-stu-id="40ddd-105">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="40ddd-106">Vous pouvez modifier ce comportement par défaut en définissant les <xref:System.Windows.Forms.TextBox.Multiline%2A> <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> Propriétés, et <xref:System.Windows.Forms.TextBox.ScrollBars%2A> sur les valeurs appropriées.</span><span class="sxs-lookup"><span data-stu-id="40ddd-106">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="40ddd-107">Pour afficher un retour chariot dans le contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="40ddd-107">To display a carriage return in the TextBox control</span></span>  
  
- <span data-ttu-id="40ddd-108">Pour afficher un retour chariot dans une ligne multiligne <xref:System.Windows.Forms.TextBox> , utilisez la <xref:System.Environment.NewLine%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="40ddd-108">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="40ddd-109">N’oubliez pas que l’interprétation des caractères d’échappement ( \\ ) est spécifique au langage.</span><span class="sxs-lookup"><span data-stu-id="40ddd-109">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="40ddd-110">Visual Basic utilise `Chr$(13) & Chr$(10)` pour la combinaison de retour chariot et de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="40ddd-110">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="40ddd-111">Pour afficher plusieurs lignes dans le contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="40ddd-111">To view multiple lines in the TextBox control</span></span>  
  
1. <span data-ttu-id="40ddd-112">Attribuez à la propriété <xref:System.Windows.Forms.TextBox.Multiline%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="40ddd-112">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="40ddd-113">Si <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> est `true` (valeur par défaut), le texte du contrôle apparaîtra sous la forme d’un ou de plusieurs paragraphes ; sinon, il apparaîtra sous la forme d’une liste, dans laquelle des lignes peuvent être découpées à la périphérie du contrôle.</span><span class="sxs-lookup"><span data-stu-id="40ddd-113">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2. <span data-ttu-id="40ddd-114">Affectez à la propriété <xref:System.Windows.Forms.TextBox.ScrollBars%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="40ddd-114">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="40ddd-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="40ddd-115">Value</span></span>|<span data-ttu-id="40ddd-116">Description</span><span class="sxs-lookup"><span data-stu-id="40ddd-116">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="40ddd-117">Utilisez cette valeur si le texte est un paragraphe qui correspond presque toujours au contrôle.</span><span class="sxs-lookup"><span data-stu-id="40ddd-117">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="40ddd-118">L’utilisateur peut utiliser le pointeur de la souris pour se déplacer dans le contrôle si le texte est trop long pour être affiché en une seule fois.</span><span class="sxs-lookup"><span data-stu-id="40ddd-118">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="40ddd-119">Utilisez cette valeur si vous souhaitez afficher une liste de lignes, dont certaines peuvent être plus longues que la largeur du <xref:System.Windows.Forms.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="40ddd-119">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="40ddd-120">Utilisez cette valeur si la liste peut être plus longue que la hauteur du contrôle.</span><span class="sxs-lookup"><span data-stu-id="40ddd-120">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3. <span data-ttu-id="40ddd-121">Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="40ddd-121">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="40ddd-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="40ddd-122">Value</span></span>|<span data-ttu-id="40ddd-123">Description</span><span class="sxs-lookup"><span data-stu-id="40ddd-123">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="40ddd-124">Le texte dans le contrôle ne sera pas automatiquement renvoyé à la ligne. il défilera vers la droite jusqu’à ce qu’un saut de ligne soit atteint.</span><span class="sxs-lookup"><span data-stu-id="40ddd-124">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="40ddd-125">Utilisez cette valeur si vous avez choisi <xref:System.Windows.Forms.ScrollBars.Horizontal> barres de défilement ou <xref:System.Windows.Forms.ScrollBars.Both> , ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="40ddd-125">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="40ddd-126">`true` (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="40ddd-126">`true` (default)</span></span>|<span data-ttu-id="40ddd-127">La barre de défilement horizontale n’apparaît pas.</span><span class="sxs-lookup"><span data-stu-id="40ddd-127">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="40ddd-128">Utilisez cette valeur si vous avez choisi des <xref:System.Windows.Forms.ScrollBars.Vertical> barres <xref:System.Windows.Forms.ScrollBars.None> de défilement ou, ci-dessus, pour afficher un ou plusieurs paragraphes.</span><span class="sxs-lookup"><span data-stu-id="40ddd-128">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40ddd-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40ddd-129">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="40ddd-130">Vue d'ensemble du contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="40ddd-130">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="40ddd-131">Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40ddd-131">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="40ddd-132">Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40ddd-132">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="40ddd-133">Comment : créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="40ddd-133">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="40ddd-134">Comment : insérer des guillemets dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="40ddd-134">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="40ddd-135">Comment : sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40ddd-135">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="40ddd-136">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="40ddd-136">TextBox Control</span></span>](textbox-control-windows-forms.md)
