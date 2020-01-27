---
title: ajouter des éléments à des contrôles DomainUpDown programmatiquement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 2e9f51fa051bf9b62e95f289db97bffd83450036
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745582"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a><span data-ttu-id="76a28-102">Comment : ajouter par programme des éléments aux contrôles DomainUpDown Windows Forms</span><span class="sxs-lookup"><span data-stu-id="76a28-102">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>
<span data-ttu-id="76a28-103">Vous pouvez ajouter des éléments à la Windows Forms <xref:System.Windows.Forms.DomainUpDown> contrôle dans le code.</span><span class="sxs-lookup"><span data-stu-id="76a28-103">You can add items to the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span> <span data-ttu-id="76a28-104">Appelez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> de la classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> pour ajouter des éléments à la propriété <xref:System.Windows.Forms.DomainUpDown.Items%2A> du contrôle.</span><span class="sxs-lookup"><span data-stu-id="76a28-104">Call the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to add items to the control's <xref:System.Windows.Forms.DomainUpDown.Items%2A> property.</span></span> <span data-ttu-id="76a28-105">La méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> ajoute un élément à la fin d’une collection, tandis que la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> ajoute un élément à une position spécifiée.</span><span class="sxs-lookup"><span data-stu-id="76a28-105">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method adds an item to the end of a collection, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method adds an item at a specified position.</span></span>  
  
### <a name="to-add-a-new-item"></a><span data-ttu-id="76a28-106">Pour ajouter un nouvel élément</span><span class="sxs-lookup"><span data-stu-id="76a28-106">To add a new item</span></span>  
  
1. <span data-ttu-id="76a28-107">Utilisez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> pour ajouter un élément à la fin de la liste d’éléments.</span><span class="sxs-lookup"><span data-stu-id="76a28-107">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method to add an item to the end of the list of items.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     <span data-ttu-id="76a28-108">\- ou -</span><span class="sxs-lookup"><span data-stu-id="76a28-108">-or-</span></span>  
  
2. <span data-ttu-id="76a28-109">Utilisez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> pour insérer un élément dans la liste à une position spécifiée.</span><span class="sxs-lookup"><span data-stu-id="76a28-109">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method to insert an item into the list at a specified position.</span></span>  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="76a28-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76a28-110">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [<span data-ttu-id="76a28-111">DomainUpDown, contrôle</span><span class="sxs-lookup"><span data-stu-id="76a28-111">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="76a28-112">Vue d’ensemble du contrôle DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="76a28-112">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)
