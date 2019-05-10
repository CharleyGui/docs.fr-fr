---
title: 'Procédure : afficher une page web à partir d’un contrôle LinkLabel Windows Forms (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- LinkLabel1_LinkClicked
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Web pages [Windows Forms], displaying
- linking [Windows Forms], to Web pages from forms
- Windows Forms, linking to Web pages
- LinkLabel control [Windows Forms], examples
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
ms.openlocfilehash: f36f5bbaaf28963fc95440a4f3a174b8b48f6276
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651798"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>Procédure : afficher une page web à partir d’un contrôle LinkLabel Windows Forms (Visual Basic)
Cet exemple affiche une page Web dans le navigateur par défaut lorsqu’un utilisateur clique sur un formulaire Windows <xref:System.Windows.Forms.LinkLabel> contrôle.  
  
## <a name="example"></a>Exemple  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Un formulaire Windows nommé `Form1`.  
  
- un contrôle <xref:System.Windows.Forms.LinkLabel> nommé `LinkLabel1` ;  
  
- Une connexion Internet active.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 L’appel à la <xref:System.Diagnostics.Process.Start%2A> méthode requiert une confiance totale. Pour plus d'informations, consultez <xref:System.Security.SecurityException>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.LinkLabel>
- [LinkLabel, contrôle](linklabel-control-windows-forms.md)
