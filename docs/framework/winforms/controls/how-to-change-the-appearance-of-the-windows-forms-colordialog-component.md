---
title: Modifier l’apparence du composant ColorDialog
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746635"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Comment : modifier l'apparence du composant ColorDialog Windows Forms
Vous pouvez configurer l’apparence du composant Windows Forms <xref:System.Windows.Forms.ColorDialog> avec un nombre de ses propriétés. La boîte de dialogue comporte deux sections : une qui affiche les couleurs de base et une qui permet à l’utilisateur de définir des couleurs personnalisées.  
  
 La plupart des propriétés limitent les couleurs que l’utilisateur peut sélectionner dans la boîte de dialogue. Si la propriété <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> est définie sur `true`, l’utilisateur est autorisé à définir des couleurs personnalisées. La propriété <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> est `true` si la boîte de dialogue est développée pour définir des couleurs personnalisées ; dans le cas contraire, l’utilisateur doit cliquer sur le bouton « définir des couleurs personnalisées ». Lorsque la propriété <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> est définie sur `true`, la boîte de dialogue affiche toutes les couleurs disponibles dans le jeu de couleurs de base. Si la propriété <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> est définie sur `true`, l’utilisateur ne peut pas sélectionner les couleurs désélectionnées. seules les couleurs unies peuvent être sélectionnées.  
  
 Si la propriété <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> est définie sur `true`, un bouton aide s’affiche dans la boîte de dialogue. Quand l’utilisateur clique sur le bouton aide, l’événement <xref:System.Windows.Forms.CommonDialog.HelpRequest> du composant <xref:System.Windows.Forms.ColorDialog> est déclenché.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Pour configurer l’apparence de la boîte de dialogue couleur  
  
1. Définissez les propriétés <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>et <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> sur les valeurs souhaitées.  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog, composant](colordialog-component-windows-forms.md)
- [Vue d’ensemble du composant ColorDialog](colordialog-component-overview-windows-forms.md)
