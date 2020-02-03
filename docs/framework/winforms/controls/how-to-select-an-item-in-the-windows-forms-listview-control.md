---
title: Sélectionner un élément dans le contrôle ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 57e985af9d0347510d7d7782f68d5b414d36e077
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743233"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="fdb3c-102">Comment : sélectionner un élément dans le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fdb3c-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="fdb3c-103">Cet exemple montre comment sélectionner par programmation un élément dans un contrôle Windows Forms <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="fdb3c-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="fdb3c-104">La sélection d’un élément par programme ne change pas automatiquement le focus en contrôle de <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="fdb3c-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="fdb3c-105">Pour cette raison, vous souhaiterez généralement également définir l’élément comme ayant le focus lors de la sélection d’un élément.</span><span class="sxs-lookup"><span data-stu-id="fdb3c-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdb3c-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="fdb3c-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fdb3c-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fdb3c-107">Compiling the Code</span></span>  
 <span data-ttu-id="fdb3c-108">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="fdb3c-108">This example requires:</span></span>  
  
- <span data-ttu-id="fdb3c-109">Un contrôle <xref:System.Windows.Forms.ListView> nommé `listView1` qui contient au moins un élément.</span><span class="sxs-lookup"><span data-stu-id="fdb3c-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
- <span data-ttu-id="fdb3c-110">Références aux espaces de noms <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fdb3c-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb3c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdb3c-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
