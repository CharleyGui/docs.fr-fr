---
title: Modifier le délai du composant ToolTip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746591"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Comment : modifier la durée avant affichage du composant ToolTip Windows Forms
Il existe plusieurs valeurs de délai que vous pouvez définir pour un composant Windows Forms <xref:System.Windows.Forms.ToolTip>. L’unité de mesure pour toutes ces propriétés est en millisecondes. La propriété <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> détermine la durée pendant laquelle l’utilisateur doit pointer sur le contrôle associé pour que la chaîne d’info-bulle s’affiche. La propriété <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> définit le nombre de millisecondes nécessaires pour que les chaînes d’info-bulle suivantes s’affichent lorsque la souris passe d’un contrôle associé à une info-bulle à un autre. La propriété <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> détermine la durée d’affichage de la chaîne d’info-bulle. Vous pouvez définir ces valeurs individuellement ou en définissant la valeur de la propriété <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> ; les autres propriétés de délai sont définies en fonction de la valeur affectée à la propriété <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>. Par exemple, lorsque <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> a la valeur N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> a la valeur N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> est définie sur la valeur de <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divisée par cinq (ou N/5) et <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> est définie sur une valeur qui est cinq fois la valeur de la propriété <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> (ou 5N).  
  
### <a name="to-set-the-delay"></a>Pour définir le délai  
  
1. Définissez les propriétés suivantes comme indiqué dans cet exemple.  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du composant ToolTip](tooltip-component-overview-windows-forms.md)
- [Guide pratique pour définir des info-bulles pour les contrôles d'un Windows Form au moment du design](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [ToolTip, composant](tooltip-component-windows-forms.md)
