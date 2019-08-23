---
title: 'Procédure : organiser les formulaires enfants MDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: 7e4d5a80961ae37951251dffa30cb8e75b20be27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955117"
---
# <a name="how-to-arrange-mdi-child-forms"></a>Procédure : organiser les formulaires enfants MDI
Les applications comportent souvent des commandes de menu qui permettent de disposer en mosaïque ou en cascade les formulaires MDI enfants ouverts, ou encore de les réorganiser. Vous pouvez utiliser la méthode <xref:System.Windows.Forms.Form.LayoutMdi%2A> avec l'une des valeurs de l'énumération <xref:System.Windows.Forms.MdiLayout> pour réorganiser les formulaires enfants dans un formulaire MDI parent.  
  
 Les valeurs de l'énumération <xref:System.Windows.Forms.MdiLayout> permettent d'afficher des formulaires enfants en cascade, en mosaïque horizontale ou verticale, ou sous forme d'icônes de formulaires enfants disposées dans la partie inférieure du formulaire MDI. Ces valeurs ont le même effet que les commandes Windows en **cascade**, **afficher les fenêtres côte à**côte, afficher les fenêtres **empilées**et **afficher le bureau**, respectivement.  
  
 Ces méthodes sont souvent utilisées en tant que gestionnaires d'événements appelés par l'événement <xref:System.Windows.Forms.Control.Click> d'un élément de menu. Ainsi, un élément de menu présentant le texte « Cascade » peut produire l'effet souhaité dans les fenêtres MDI enfants.  
  
### <a name="to-arrange-child-forms"></a>Pour réorganiser les formulaires enfants  
  
1. Dans une méthode, utilisez la méthode <xref:System.Windows.Forms.Form.LayoutMdi%2A> pour définir l'énumération <xref:System.Windows.Forms.MdiLayout> pour le formulaire MDI parent. L'exemple ci-dessous utilise la valeur d'énumération <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> pour les fenêtres enfants du formulaire MDI parent (`Form1`). L’énumération est utilisée dans le code lors du gestionnaire d' <xref:System.Windows.Forms.Control.Click> événements pour l’événement de l’élément de menu **fenêtres en cascade** .  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    > De la même façon, vous pouvez disposer les fenêtres en mosaïque et les afficher sous forme d'icônes en modifiant la valeur d'énumération <xref:System.Windows.Forms.MdiLayout> utilisée.  
  
2. Si vous utilisez Visual C#, placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d'événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Applications d’interface multidocument (MDI, Multiple Document Interface)](multiple-document-interface-mdi-applications.md)
- [Guide pratique pour Créer des formulaires MDI parents](how-to-create-mdi-parent-forms.md)
- [Guide pratique : Créer des formulaires MDI enfants](how-to-create-mdi-child-forms.md)
- [Guide pratique pour Déterminer l’enfant MDI actif](how-to-determine-the-active-mdi-child.md)
- [Guide pratique pour Envoyer des données à l’enfant MDI actif](how-to-send-data-to-the-active-mdi-child.md)
