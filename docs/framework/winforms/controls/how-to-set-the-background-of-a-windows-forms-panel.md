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
ms.openlocfilehash: 36e552475334c25b9d5a6fafb82155c6ebcba266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182108"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Comment : définir l'arrière-plan d'un panneau Windows Forms
Un contrôle <xref:System.Windows.Forms.Panel> windows Forms peut afficher à la fois une couleur de fond et une image de fond. La <xref:System.Windows.Forms.Control.BackColor%2A> propriété définit la couleur de fond pour les commandes contenues, telles que les étiquettes et les boutons radio. Si <xref:System.Windows.Forms.Control.BackgroundImage%2A> la propriété n’est pas définie, la <xref:System.Windows.Forms.Control.BackColor%2A> sélection remplira l’ensemble du panneau. Si <xref:System.Windows.Forms.Control.BackgroundImage%2A> la propriété est définie, l’image s’affiche derrière les commandes contenues.  
  
### <a name="to-set-the-background-programmatically"></a>Définir l’arrière-plan de façon programmatique  
  
1. Définissez la <xref:System.Windows.Forms.Control.BackColor%2A> propriété du panneau <xref:System.Drawing.Color?displayProperty=nameWithType>à une valeur de type .  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Définissez la <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriété du <xref:System.Drawing.Image.FromFile%2A> panneau <xref:System.Drawing.Image?displayProperty=nameWithType> en utilisant la méthode de la classe.  
  
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
