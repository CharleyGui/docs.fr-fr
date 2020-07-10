---
title: Marge et marge intérieure dans les contrôles
description: Découvrez comment ajouter des marges et des marges dans les contrôles Windows Forms avec les propriétés de marge et de marge intérieure.
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 4279f39bb4f89fbda8be472f49c8e60853abcac6
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174482"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="9383e-103">Marge et marge intérieure dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9383e-103">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="9383e-104">Le positionnement précis des contrôles sur votre formulaire constitue une haute priorité pour de nombreuses applications.</span><span class="sxs-lookup"><span data-stu-id="9383e-104">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="9383e-105">L’espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> propose pour cela de nombreuses fonctionnalités de disposition.</span><span class="sxs-lookup"><span data-stu-id="9383e-105">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="9383e-106">Deux des plus importantes sont les propriétés <xref:System.Windows.Forms.Control.Margin%2A> et <xref:System.Windows.Forms.Control.Padding%2A>.</span><span class="sxs-lookup"><span data-stu-id="9383e-106">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="9383e-107">La propriété <xref:System.Windows.Forms.Control.Margin%2A> définit l'espace autour du contrôle qui maintient les autres contrôles à une distance spécifiée des bordures du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9383e-107">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="9383e-108">La propriété <xref:System.Windows.Forms.Control.Padding%2A> définit l'espace à l'intérieur d'un contrôle qui maintient le contenu du contrôle (par exemple la valeur de sa propriété <xref:System.Windows.Forms.Control.Text%2A>) à une distance spécifiée des bordures du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9383e-108">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="9383e-109">L'illustration suivante montre les propriétés <xref:System.Windows.Forms.Control.Padding%2A> et <xref:System.Windows.Forms.Control.Margin%2A> d'un contrôle.</span><span class="sxs-lookup"><span data-stu-id="9383e-109">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="9383e-110">![Remplissage et marge pour les contrôles Windows Forms](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="9383e-110">![Padding And Margin for Windows Forms Controls](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="9383e-111">Cette fonctionnalité est prise en charge au moment du design dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9383e-111">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="9383e-112">Consultez également [procédure pas à pas : disposition des contrôles Windows Forms avec le remplissage, les marges et la propriété AutoSize](windows-forms-controls-padding-autosize.md).</span><span class="sxs-lookup"><span data-stu-id="9383e-112">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9383e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9383e-113">See also</span></span>

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
