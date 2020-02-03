---
title: Dimensionner un contrôle Label pour l’adapter à son contenu
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743773"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="663c7-102">Comment : dimensionner un contrôle Label Windows Forms en fonction de son contenu</span><span class="sxs-lookup"><span data-stu-id="663c7-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="663c7-103">Le contrôle Windows Forms <xref:System.Windows.Forms.Label> peut être une seule ligne ou plusieurs lignes, et sa taille peut être fixe ou peut se redimensionner automatiquement pour s’adapter à sa légende.</span><span class="sxs-lookup"><span data-stu-id="663c7-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="663c7-104">La propriété <xref:System.Windows.Forms.Label.AutoSize%2A> vous permet de dimensionner les contrôles pour qu’ils s’ajustent aux légendes les plus grandes ou les plus petites, ce qui est particulièrement utile si la légende change au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="663c7-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="663c7-105">Pour faire en sorte qu’un contrôle Label se redimensionne dynamiquement pour s’adapter à son contenu</span><span class="sxs-lookup"><span data-stu-id="663c7-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1. <span data-ttu-id="663c7-106">Affectez à sa propriété <xref:System.Windows.Forms.Label.AutoSize%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="663c7-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="663c7-107">Si <xref:System.Windows.Forms.Label.AutoSize%2A> a la valeur `false`, les mots spécifiés dans la propriété <xref:System.Windows.Forms.Label.Text%2A> sont renvoyés à la ligne suivante, si possible, mais le contrôle ne s’agrandit pas.</span><span class="sxs-lookup"><span data-stu-id="663c7-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="663c7-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="663c7-108">See also</span></span>

- [<span data-ttu-id="663c7-109">Guide pratique pour créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms</span><span class="sxs-lookup"><span data-stu-id="663c7-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="663c7-110">Vue d'ensemble du contrôle Label</span><span class="sxs-lookup"><span data-stu-id="663c7-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="663c7-111">Label, contrôle</span><span class="sxs-lookup"><span data-stu-id="663c7-111">Label Control</span></span>](label-control-windows-forms.md)
