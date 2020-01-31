---
title: définir l’arrière-plan d’un panneau
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
ms.openlocfilehash: ba2619354403793aea7ca15d43649da9637079a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744741"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Comment : définir l'arrière-plan d'un panneau Windows Forms
Un contrôle Windows Forms <xref:System.Windows.Forms.Panel> peut afficher une couleur d’arrière-plan et une image d’arrière-plan. La propriété <xref:System.Windows.Forms.Control.BackColor%2A> définit la couleur d’arrière-plan des contrôles contenus, tels que les étiquettes et les cases d’option. Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> n’est pas définie, la sélection <xref:System.Windows.Forms.Control.BackColor%2A> remplit tout le panneau. Si la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> est définie, l’image est affichée derrière les contrôles contenus.  
  
### <a name="to-set-the-background-programmatically"></a>Pour définir l’arrière-plan par programmation  
  
1. Affectez à la propriété <xref:System.Windows.Forms.Control.BackColor%2A> du panneau une valeur de type <xref:System.Drawing.Color?displayProperty=nameWithType>.  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Définissez la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> du panneau à l’aide de la méthode <xref:System.Drawing.Image.FromFile%2A> de la classe <xref:System.Drawing.Image?displayProperty=nameWithType>.  
  
    ```vb  
    ' You should replace the bolded image   
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel, contrôle](panel-control-windows-forms.md)
- [Vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md)
