---
title: 'Procédure : créer des clés d’accès avec les contrôles Label Windows Forms'
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
ms.openlocfilehash: dd7f238f8c20ba990158f23344e36376d3b1cb7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950539"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Procédure : créer des clés d’accès avec les contrôles Label Windows Forms
Les <xref:System.Windows.Forms.Label> contrôles Windows Forms peuvent être utilisés pour définir des clés d’accès pour d’autres contrôles. Lorsque vous définissez une clé d’accès dans un contrôle Label, l’utilisateur peut appuyer sur la touche ALT et le caractère que vous désignez pour déplacer le focus sur le contrôle qui le suit dans l’ordre de tabulation. Étant donné que les étiquettes ne peuvent pas recevoir le focus, le focus se déplace automatiquement vers le contrôle suivant dans l’ordre de tabulation. Utilisez cette technique pour affecter des clés d’accès à des zones de texte, des zones de liste modifiable, des zones de liste et des grilles de données.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Pour assigner une touche d’accès à un contrôle à l’aide d’une étiquette  
  
1. Dessinez d’abord l’étiquette, puis dessinez l’autre contrôle.  
  
     ou  
  
     Dessinez les contrôles dans n’importe quel ordre <xref:System.Windows.Forms.Control.TabIndex%2A> et affectez à la propriété de l’étiquette une valeur inférieure à celle de l’autre contrôle.  
  
2. Affectez à `true`la <xref:System.Windows.Forms.Label.UseMnemonic%2A> propriété de l’étiquette la valeur.  
  
3. Utilisez une esperluette (&) dans la propriété de <xref:System.Windows.Forms.Label.Text%2A> l’étiquette pour affecter la touche d’accès pour l’étiquette. Pour plus d’informations, consultez [création de clés d’accès pour les contrôles Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    > Vous souhaiterez peut-être afficher les perluète dans un contrôle Label, plutôt que de les utiliser pour créer des clés d’accès. Cela peut se produire si vous liez un contrôle Label à un champ d’un Recordset dans lequel les données incluent des esperluettes. Pour afficher les perluète dans un contrôle Label, affectez <xref:System.Windows.Forms.Label.UseMnemonic%2A> à `false`la propriété la valeur. Si vous souhaitez afficher les perluète et une touche d’accès, affectez à <xref:System.Windows.Forms.Label.UseMnemonic%2A> `true` la propriété la valeur et indiquez la touche d’accès avec une esperluette (&) et l’esperluette (et commercial) à afficher avec deux signes &.  
  
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

- [Guide pratique pour Dimensionner un contrôle Label Windows Forms pour l’adapter à son contenu](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Vue d'ensemble du contrôle Label](label-control-overview-windows-forms.md)
- [Label, contrôle](label-control-windows-forms.md)
