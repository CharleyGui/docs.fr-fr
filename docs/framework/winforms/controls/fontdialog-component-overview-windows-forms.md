---
title: Vue d'ensemble du composant FontDialog
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745705"
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="fcea7-102">Vue d'ensemble du composant FontDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fcea7-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="fcea7-103">Le composant Windows Forms <xref:System.Windows.Forms.FontDialog> est une boîte de dialogue préconfigurée, qui est la boîte de dialogue **police** Windows standard utilisée pour exposer les polices qui sont actuellement installées sur le système.</span><span class="sxs-lookup"><span data-stu-id="fcea7-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="fcea7-104">Utilisez-le au sein de votre application Windows comme une solution simple pour la sélection des polices au lieu de configurer votre propre boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="fcea7-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="fcea7-105">Par défaut, la boîte de dialogue affiche les zones de liste pour la police, le style de police et la taille ; cases à cocher pour les effets tels que barré et souligné ; liste déroulante de script ; et un exemple de la façon dont la police s’affiche.</span><span class="sxs-lookup"><span data-stu-id="fcea7-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="fcea7-106">(Le script fait référence à différents scripts de caractères disponibles pour une police donnée, par exemple l’hébreu ou le japonais.) Pour afficher la boîte de dialogue police, appelez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcea7-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="fcea7-107">Propriétés de clé</span><span class="sxs-lookup"><span data-stu-id="fcea7-107">Key Properties</span></span>  
 <span data-ttu-id="fcea7-108">Le composant possède un certain nombre de propriétés qui configurent son apparence.</span><span class="sxs-lookup"><span data-stu-id="fcea7-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="fcea7-109">Les propriétés qui définissent les sélections de la boîte de dialogue sont <xref:System.Windows.Forms.FontDialog.Font%2A> et <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcea7-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="fcea7-110">La propriété <xref:System.Windows.Forms.FontDialog.Font%2A> définit la police, le style, la taille, le script et les effets. par exemple, `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="fcea7-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcea7-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcea7-111">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="fcea7-112">FontDialog, composant</span><span class="sxs-lookup"><span data-stu-id="fcea7-112">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
