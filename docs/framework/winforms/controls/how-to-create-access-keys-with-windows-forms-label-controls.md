---
title: Créer des clés d’accès avec des contrôles Label
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
ms.openlocfilehash: 800afc03e71435e2721456b93bb9704af01f714a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731053"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Comment : créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms
Windows Forms contrôles <xref:System.Windows.Forms.Label> peuvent être utilisés pour définir des clés d’accès pour d’autres contrôles. Lorsque vous définissez une clé d’accès dans un contrôle Label, l’utilisateur peut appuyer sur la touche ALT et le caractère que vous désignez pour déplacer le focus sur le contrôle qui le suit dans l’ordre de tabulation. Étant donné que les étiquettes ne peuvent pas recevoir le focus, le focus se déplace automatiquement vers le contrôle suivant dans l’ordre de tabulation. Utilisez cette technique pour affecter des clés d’accès à des zones de texte, des zones de liste modifiable, des zones de liste et des grilles de données.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Pour assigner une touche d’accès à un contrôle à l’aide d’une étiquette  
  
1. Dessinez d’abord l’étiquette, puis dessinez l’autre contrôle.  
  
     \- ou -  
  
     Dessinez les contrôles dans n’importe quel ordre et affectez à la propriété <xref:System.Windows.Forms.Control.TabIndex%2A> de l’étiquette une valeur inférieure à celle de l’autre contrôle.  
  
2. Affectez à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> de l’étiquette la valeur `true`.  
  
3. Utilisez une esperluette (&) dans la propriété <xref:System.Windows.Forms.Label.Text%2A> de l’étiquette pour affecter la touche d’accès pour l’étiquette. Pour plus d’informations, consultez [création de clés d’accès pour les contrôles Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    > Vous souhaiterez peut-être afficher les perluète dans un contrôle Label, plutôt que de les utiliser pour créer des clés d’accès. Cela peut se produire si vous liez un contrôle Label à un champ d’un Recordset dans lequel les données incluent des esperluettes. Pour afficher les perluète dans un contrôle Label, affectez à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> la valeur `false`. Si vous souhaitez afficher les perluète et une touche d’accès, affectez à la propriété <xref:System.Windows.Forms.Label.UseMnemonic%2A> la valeur `true` et indiquez la touche d’accès avec une esperluette (&) et l’esperluette (et commercial) à afficher avec deux signes « et ».  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour dimensionner un contrôle Label Windows Forms en fonction de son contenu](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Vue d'ensemble du contrôle Label](label-control-overview-windows-forms.md)
- [Label, contrôle](label-control-windows-forms.md)
