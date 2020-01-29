---
title: Supprimer des éléments des contrôles DomainUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: e52af5c5add4fda93e2b51c8afdb90c92e8d2f62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735771"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Comment : supprimer des éléments des contrôles DomainUpDown Windows Forms
Vous pouvez supprimer des éléments du contrôle Windows Forms <xref:System.Windows.Forms.DomainUpDown> en appelant la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> de la classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>. La méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> supprime un élément spécifique, tandis que la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> supprime un élément en fonction de sa position.  
  
### <a name="to-remove-an-item"></a>Pour supprimer un élément  
  
- Utilisez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> de la classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> pour supprimer un élément par son nom.  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     \- ou -  
  
- Utilisez la méthode <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> pour supprimer un élément en fonction de sa position.  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [DomainUpDown, contrôle](domainupdown-control-windows-forms.md)
- [Vue d’ensemble du contrôle DomainUpDown](domainupdown-control-overview-windows-forms.md)
