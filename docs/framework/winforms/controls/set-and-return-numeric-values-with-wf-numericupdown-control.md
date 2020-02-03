---
title: Définir et retourner des valeurs numériques avec le contrôle NumericUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
ms.openlocfilehash: a0b264fec9619b467c293bcb96278c4517775ac3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743025"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>Comment : définir et retourner des valeurs numériques à l'aide du contrôle NumericUpDown Windows Forms
La valeur numérique du contrôle <xref:System.Windows.Forms.NumericUpDown> Windows Forms est déterminée par sa propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A>. Vous pouvez écrire des tests conditionnels pour la valeur du contrôle comme avec n’importe quelle autre propriété. Une fois la propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A> définie, vous pouvez l’ajuster directement en écrivant du code pour effectuer des opérations sur celle-ci, ou vous pouvez appeler les méthodes <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> et <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
### <a name="to-set-the-numeric-value"></a>Pour définir la valeur numérique  
  
1. Assignez une valeur à la propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A> dans le code ou dans le Fenêtre Propriétés.  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     -ou-  
  
2. Appelez la méthode <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> ou <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> pour augmenter ou diminuer la valeur de la quantité spécifiée dans la propriété <xref:System.Windows.Forms.NumericUpDown.Increment%2A>.  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a>Pour retourner la valeur numérique  
  
- Accédez à la propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A> dans le code.  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [NumericUpDown, contrôle](numericupdown-control-windows-forms.md)
- [Vue d’ensemble du contrôle NumericUpDown](numericupdown-control-overview-windows-forms.md)
