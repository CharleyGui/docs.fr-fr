---
title: 'Procédure : supprimer des éléments dans des contrôles DomainUpDown Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: f56bc2b7b7b8a783ac298b220c83281f38da29da
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662353"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Procédure : supprimer des éléments dans des contrôles DomainUpDown Windows Forms
Vous pouvez supprimer des éléments de formulaires Windows <xref:System.Windows.Forms.DomainUpDown> contrôle en appelant le <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> ou <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> méthode de la <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> classe. Le <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> méthode supprime un élément spécifique, tandis que le <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> méthode supprime un élément par sa position.  
  
### <a name="to-remove-an-item"></a>Pour supprimer un élément  
  
- Utilisez le <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> méthode de la <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> classe pour supprimer un élément par nom.  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     ou  
  
- Utilisez le <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> méthode pour supprimer un élément par sa position.  
  
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
