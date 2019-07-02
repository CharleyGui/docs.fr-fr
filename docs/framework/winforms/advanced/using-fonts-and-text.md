---
title: Utilisation de polices et de texte
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: 73a4af5fe7367e777fcb83af8c84c09be91e5b1e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505110"
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="e6134-102">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="e6134-102">Using Fonts and Text</span></span>
<span data-ttu-id="e6134-103">Il existe plusieurs classes offertes par GDI + et GDI pour dessiner du texte dans les Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e6134-103">There are several classes offered by GDI+ and GDI for drawing text on Windows Forms.</span></span> <span data-ttu-id="e6134-104">GDI + <xref:System.Drawing.Graphics> classe dispose de plusieurs <xref:System.Drawing.Graphics.DrawString%2A> méthodes qui vous permettent de spécifier diverses fonctionnalités de texte, comme l’emplacement, le rectangle englobant, police et le format.</span><span class="sxs-lookup"><span data-stu-id="e6134-104">The GDI+ <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="e6134-105">En outre, vous pouvez dessiner et mesurer le texte avec GDI à l’aide de la méthode statique <xref:System.Windows.Forms.TextRenderer.DrawText%2A> et <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> méthodes proposées par le `TextRenderer` classe.</span><span class="sxs-lookup"><span data-stu-id="e6134-105">In addition, you can draw and measure text with GDI using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="e6134-106">Les méthodes GDI vous permettent également de spécifier la police, l’emplacement et le format.</span><span class="sxs-lookup"><span data-stu-id="e6134-106">The GDI methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="e6134-107">Vous pouvez choisir GDI ou GDI + pour le rendu de texte. Toutefois, GDI offre généralement de meilleures performances et une mesure de texte plus précis.</span><span class="sxs-lookup"><span data-stu-id="e6134-107">You can choose either GDI or GDI+ for text rendering; however, GDI generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="e6134-108">Incluent d’autres classes qui contribuent au rendu de texte `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, et `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="e6134-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6134-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e6134-109">In This Section</span></span>  
 [<span data-ttu-id="e6134-110">Guide pratique pour Construire des familles de polices et des polices</span><span class="sxs-lookup"><span data-stu-id="e6134-110">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="e6134-111">Montre comment créer `Font` et `FontFamily` objets.</span><span class="sxs-lookup"><span data-stu-id="e6134-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="e6134-112">Guide pratique pour Dessiner du texte à un emplacement spécifié</span><span class="sxs-lookup"><span data-stu-id="e6134-112">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="e6134-113">Décrit comment dessiner du texte dans un emplacement donné à l’aide de GDI + et GDI.</span><span class="sxs-lookup"><span data-stu-id="e6134-113">Describes how to draw text in a certain location using GDI+ and GDI.</span></span>  
  
 [<span data-ttu-id="e6134-114">Guide pratique pour Dessiner du texte encapsulé dans un Rectangle</span><span class="sxs-lookup"><span data-stu-id="e6134-114">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="e6134-115">Explique comment dessiner du texte dans un rectangle à l’aide de GDI + et GDI.</span><span class="sxs-lookup"><span data-stu-id="e6134-115">Explains how to draw text in a rectangle using GDI+ and GDI.</span></span>  
  
 [<span data-ttu-id="e6134-116">Guide pratique pour Dessiner du texte avec GDI</span><span class="sxs-lookup"><span data-stu-id="e6134-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="e6134-117">Montre comment utiliser GDI pour dessiner du texte.</span><span class="sxs-lookup"><span data-stu-id="e6134-117">Demonstrates how to use GDI for drawing text.</span></span>  
  
 [<span data-ttu-id="e6134-118">Guide pratique pour Aligner le texte écrit</span><span class="sxs-lookup"><span data-stu-id="e6134-118">How to: Align Drawn Text</span></span>](how-to-align-drawn-text.md)  
 <span data-ttu-id="e6134-119">Montre comment mettre en forme texte GDI + et GDI.</span><span class="sxs-lookup"><span data-stu-id="e6134-119">Shows how to format GDI+ and GDI text.</span></span>  
  
 [<span data-ttu-id="e6134-120">Guide pratique pour Créer du texte Vertical</span><span class="sxs-lookup"><span data-stu-id="e6134-120">How to: Create Vertical Text</span></span>](how-to-create-vertical-text.md)  
 <span data-ttu-id="e6134-121">Décrit comment dessiner le texte aligné verticalement avec GDI +.</span><span class="sxs-lookup"><span data-stu-id="e6134-121">Describes how to draw vertically aligned text with GDI+.</span></span>  
  
 [<span data-ttu-id="e6134-122">Guide pratique pour Définir des taquets de tabulation dans du texte dessiné</span><span class="sxs-lookup"><span data-stu-id="e6134-122">How to: Set Tab Stops in Drawn Text</span></span>](how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="e6134-123">Montre comment dessiner du texte avec des taquets de tabulation avec GDI +.</span><span class="sxs-lookup"><span data-stu-id="e6134-123">Shows how draw text with tab stops with GDI+.</span></span>  
  
 [<span data-ttu-id="e6134-124">Guide pratique pour Énumérer les polices installées</span><span class="sxs-lookup"><span data-stu-id="e6134-124">How to: Enumerate Installed Fonts</span></span>](how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="e6134-125">Explique comment répertorier les noms de polices installées.</span><span class="sxs-lookup"><span data-stu-id="e6134-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="e6134-126">Guide pratique pour Créer une Collection de polices privées</span><span class="sxs-lookup"><span data-stu-id="e6134-126">How to: Create a Private Font Collection</span></span>](how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="e6134-127">Décrit comment créer un <xref:System.Drawing.Text.PrivateFontCollection> objet.</span><span class="sxs-lookup"><span data-stu-id="e6134-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="e6134-128">Guide pratique pour Obtenir des métriques de police</span><span class="sxs-lookup"><span data-stu-id="e6134-128">How to: Obtain Font Metrics</span></span>](how-to-obtain-font-metrics.md)  
 <span data-ttu-id="e6134-129">Montre comment obtenir des métriques de police telles que le jambage ascendant et descendant.</span><span class="sxs-lookup"><span data-stu-id="e6134-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="e6134-130">Guide pratique pour Utiliser l’anticrénelage avec du texte</span><span class="sxs-lookup"><span data-stu-id="e6134-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="e6134-131">Explique comment utiliser l’anticrénelage lors du dessin de texte.</span><span class="sxs-lookup"><span data-stu-id="e6134-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e6134-132">Référence</span><span class="sxs-lookup"><span data-stu-id="e6134-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="e6134-133">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="e6134-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="e6134-134">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="e6134-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="e6134-135">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="e6134-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="e6134-136">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="e6134-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="e6134-137">Décrit cette classe et contient des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="e6134-137">Describes this class and contains links to all of its members.</span></span>
