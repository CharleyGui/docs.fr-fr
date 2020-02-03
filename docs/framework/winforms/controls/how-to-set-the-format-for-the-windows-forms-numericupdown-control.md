---
title: Définir le format du contrôle NumericUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 5ef1c801e96bef7b92e7e69dc36491144c456eeb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742176"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Comment : définir le format du contrôle NumericUpDown Windows Forms
Vous pouvez configurer la façon dont les valeurs sont affichées dans le contrôle Windows Forms <xref:System.Windows.Forms.NumericUpDown>. La propriété <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> détermine le nombre de nombres apparaissant après la virgule décimale ; la valeur par défaut est 0. La propriété <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> détermine si un séparateur est inséré entre tous les trois chiffres décimaux ; la valeur par défaut est `false`. Le contrôle peut afficher des valeurs au format hexadécimal au lieu du format décimal, si la propriété <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> est définie sur `true`; la valeur par défaut est `false`.  
  
### <a name="to-format-the-numeric-value"></a>Pour mettre en forme la valeur numérique  
  
- Affichez une valeur décimale en affectant à la propriété <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> la valeur d’un entier et en affectant à la propriété <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> la valeur `true` ou `false`.  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     -ou-  
  
- Affichez une valeur hexadécimale en affectant à la propriété <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> la valeur `true`.  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    > Même si la valeur est affichée dans le formulaire au format hexadécimal, tous les tests que vous effectuez sur la propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A> testeront sa valeur décimale.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown, contrôle](numericupdown-control-windows-forms.md)
- [Vue d’ensemble du contrôle NumericUpDown](numericupdown-control-overview-windows-forms.md)
