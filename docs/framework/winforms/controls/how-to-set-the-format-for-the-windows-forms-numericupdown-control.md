---
title: 'Procédure : définir le format du contrôle NumericUpDown Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 6db7a1b2aeb7282c3ac827cb8319706ed348fc22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949163"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Procédure : définir le format du contrôle NumericUpDown Windows Forms
Vous pouvez configurer la façon dont les valeurs sont affichées <xref:System.Windows.Forms.NumericUpDown> dans le contrôle Windows Forms. La <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> propriété détermine le nombre de nombres qui apparaissent après la virgule décimale; la valeur par défaut est 0. La <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> propriété détermine si un séparateur est inséré entre tous les trois chiffres décimaux; la valeur par `false`défaut est. Le contrôle peut afficher des valeurs au format hexadécimal au lieu du format décimal <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> , si la propriété `true`a la valeur; `false`la valeur par défaut est.  
  
### <a name="to-format-the-numeric-value"></a>Pour mettre en forme la valeur numérique  
  
- Affichez une valeur décimale en <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> affectant à la propriété un entier <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> et en `true` affectant à la propriété la valeur ou `false`.  
  
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
  
     ou  
  
- Affichez une valeur hexadécimale en <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> affectant `true`à la propriété la valeur.  
  
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
    > Même si la valeur est affichée dans le formulaire au format hexadécimal, tous les tests que vous <xref:System.Windows.Forms.NumericUpDown.Value%2A> effectuez sur la propriété testent sa valeur décimale.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown, contrôle](numericupdown-control-windows-forms.md)
- [Vue d’ensemble du contrôle NumericUpDown](numericupdown-control-overview-windows-forms.md)
