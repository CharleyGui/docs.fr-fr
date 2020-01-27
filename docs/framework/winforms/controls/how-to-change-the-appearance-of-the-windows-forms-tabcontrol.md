---
title: Modifier l’apparence de TabControl
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746613"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a>Comment : modifier l'apparence du contrôle TabControl Windows Forms
Vous pouvez modifier l’apparence des onglets dans Windows Forms à l’aide des propriétés du <xref:System.Windows.Forms.TabControl> et des objets <xref:System.Windows.Forms.TabPage> qui composent les onglets individuels sur le contrôle. En définissant ces propriétés, vous pouvez afficher des images sur les onglets, afficher les onglets verticalement plutôt que horizontalement, afficher plusieurs lignes d’onglets et activer ou désactiver les onglets par programmation.  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a>Pour afficher une icône sur la partie étiquette d’un onglet  
  
1. Ajoutez un contrôle <xref:System.Windows.Forms.ImageList> au formulaire.  
  
2. Ajoutez des images à la liste d’images.  
  
     Pour plus d’informations sur les listes d’images, consultez [composant ImageList](imagelist-component-windows-forms.md) et [Comment : ajouter ou supprimer des images avec le composant ImageList Windows Forms](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3. Affectez à la propriété <xref:System.Windows.Forms.TabControl.ImageList%2A> du <xref:System.Windows.Forms.TabControl> le contrôle <xref:System.Windows.Forms.ImageList>.  
  
4. Affectez à la propriété <xref:System.Windows.Forms.TabPage.ImageIndex%2A> du <xref:System.Windows.Forms.TabPage> l’index d’une image appropriée dans la liste.  
  
### <a name="to-create-multiple-rows-of-tabs"></a>Pour créer plusieurs lignes d’onglets  
  
1. Ajoutez le nombre de pages d’onglets souhaitées.  
  
2. Affectez à la propriété <xref:System.Windows.Forms.TabControl.Multiline%2A> du <xref:System.Windows.Forms.TabControl> la valeur `true`.  
  
3. Si les onglets n’apparaissent pas encore dans plusieurs lignes, affectez à la propriété <xref:System.Windows.Forms.Control.Width%2A> de la <xref:System.Windows.Forms.TabControl> la valeur plus étroite que tous les onglets.  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a>Pour organiser les onglets sur le côté du contrôle  
  
- Affectez à la propriété <xref:System.Windows.Forms.TabControl.Alignment%2A> du <xref:System.Windows.Forms.TabControl> la valeur <xref:System.Windows.Forms.TabAlignment.Left> ou <xref:System.Windows.Forms.TabAlignment.Right>.  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a>Pour activer ou désactiver tous les contrôles d’un onglet par programmation  
  
1. Affectez à la propriété <xref:System.Windows.Forms.TabPage.Enabled%2A> du <xref:System.Windows.Forms.TabPage> la valeur `true` ou `false`.  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a>Pour afficher les onglets en tant que boutons  
  
- Affectez à la propriété <xref:System.Windows.Forms.TabControl.Appearance%2A> du <xref:System.Windows.Forms.TabControl> la valeur <xref:System.Windows.Forms.TabAppearance.Buttons> ou <xref:System.Windows.Forms.TabAppearance.FlatButtons>.  
  
## <a name="see-also"></a>Voir aussi

- [TabControl, contrôle](tabcontrol-control-windows-forms.md)
- [Vue d’ensemble du contrôle TabControl](tabcontrol-control-overview-windows-forms.md)
- [Guide pratique pour ajouter un contrôle à une page d'onglet](how-to-add-a-control-to-a-tab-page.md)
- [Guide pratique pour désactiver les pages d'onglets](how-to-disable-tab-pages.md)
- [Guide pratique pour ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
