---
title: 'Procédure : étendre des lignes et des colonnes dans un contrôle TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039702"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="9cf2c-102">Procédure : étendre des lignes et des colonnes dans un contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="9cf2c-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="9cf2c-103">Les contrôles d' <xref:System.Windows.Forms.TableLayoutPanel> un contrôle peuvent couvrir des lignes et des colonnes adjacentes.</span><span class="sxs-lookup"><span data-stu-id="9cf2c-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>

## <a name="to-span-columns-and-rows"></a><span data-ttu-id="9cf2c-104">Pour étendre les colonnes et les lignes</span><span class="sxs-lookup"><span data-stu-id="9cf2c-104">To span columns and rows</span></span>

1. <span data-ttu-id="9cf2c-105">Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="9cf2c-105">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="9cf2c-106">Faites glisser <xref:System.Windows.Forms.Button> un contrôle de la **boîte à outils** vers la cellule supérieure <xref:System.Windows.Forms.TableLayoutPanel> gauche du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9cf2c-106">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="9cf2c-107">Affectez <xref:System.Windows.Forms.Button> à la propriété **ColumnSpan** du contrôle la valeur **2**.</span><span class="sxs-lookup"><span data-stu-id="9cf2c-107">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="9cf2c-108">Notez que le <xref:System.Windows.Forms.Button> contrôle s’étend sur la première et la deuxième colonne.</span><span class="sxs-lookup"><span data-stu-id="9cf2c-108">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>

4. <span data-ttu-id="9cf2c-109">Affectez <xref:System.Windows.Forms.Button> à la propriété **RowSpan** du contrôle la valeur **2**.</span><span class="sxs-lookup"><span data-stu-id="9cf2c-109">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="9cf2c-110">Notez que le <xref:System.Windows.Forms.Button> contrôle s’étend sur la première et la deuxième ligne.</span><span class="sxs-lookup"><span data-stu-id="9cf2c-110">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>

5. <span data-ttu-id="9cf2c-111">Affectez <xref:System.Windows.Forms.Button> à la propriété **ColumnSpan** du contrôle la valeur **1**.</span><span class="sxs-lookup"><span data-stu-id="9cf2c-111">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="9cf2c-112">Notez que le <xref:System.Windows.Forms.Button> contrôle se déplace dans la première colonne et s’étend sur la première et la deuxième ligne.</span><span class="sxs-lookup"><span data-stu-id="9cf2c-112">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>

## <a name="see-also"></a><span data-ttu-id="9cf2c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cf2c-113">See also</span></span>

- [<span data-ttu-id="9cf2c-114">TableLayoutPanel, contrôle</span><span class="sxs-lookup"><span data-stu-id="9cf2c-114">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
