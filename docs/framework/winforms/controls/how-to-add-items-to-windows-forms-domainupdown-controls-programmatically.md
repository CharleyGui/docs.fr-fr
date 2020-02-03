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
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Comment : ajouter par programme des éléments aux contrôles DomainUpDown Windows Forms
Vous pouvez ajouter des éléments à la Windows Forms <xref:System.Windows.Forms.DomainUpDown> contrôle dans le code. Appelez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> de la classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> pour ajouter des éléments à la propriété <xref:System.Windows.Forms.DomainUpDown.Items%2A> du contrôle. La méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> ajoute un élément à la fin d’une collection, tandis que la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> ajoute un élément à une position spécifiée.  
  
### <a name="to-add-a-new-item"></a>Pour ajouter un nouvel élément  
  
1. Utilisez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> pour ajouter un élément à la fin de la liste d’éléments.  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     -ou-  
  
2. Utilisez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> pour insérer un élément dans la liste à une position spécifiée.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [DomainUpDown, contrôle](domainupdown-control-windows-forms.md)
- [Vue d’ensemble du contrôle DomainUpDown](domainupdown-control-overview-windows-forms.md)
