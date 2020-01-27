---
title: Afficher une page Web à partir du contrôle LinkLabel (Visual Basic)
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
ms.openlocfilehash: 75373d55b7bc5ef11e39d5b9546996cb1c4f6f7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745928"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a><span data-ttu-id="68f36-102">Comment : afficher une page web à partir d’un contrôle LinkLabel Windows Forms (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68f36-102">How to: Display a Web Page from a Windows Forms LinkLabel Control (Visual Basic)</span></span>
<span data-ttu-id="68f36-103">Cet exemple affiche une page Web dans le navigateur par défaut lorsqu’un utilisateur clique sur un contrôle Windows Forms <xref:System.Windows.Forms.LinkLabel>.</span><span class="sxs-lookup"><span data-stu-id="68f36-103">This example displays a Web page in the default browser when a user clicks a Windows Forms <xref:System.Windows.Forms.LinkLabel> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68f36-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="68f36-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="68f36-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="68f36-105">Compiling the Code</span></span>  
 <span data-ttu-id="68f36-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="68f36-106">This example requires:</span></span>  
  
- <span data-ttu-id="68f36-107">Un Windows Form nommé `Form1`.</span><span class="sxs-lookup"><span data-stu-id="68f36-107">A Windows Form named `Form1`.</span></span>  
  
- <span data-ttu-id="68f36-108">un contrôle <xref:System.Windows.Forms.LinkLabel> nommé `LinkLabel1` ;</span><span class="sxs-lookup"><span data-stu-id="68f36-108">A <xref:System.Windows.Forms.LinkLabel> control named `LinkLabel1`.</span></span>  
  
- <span data-ttu-id="68f36-109">Une connexion Internet active.</span><span class="sxs-lookup"><span data-stu-id="68f36-109">An active Internet connection.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="68f36-110">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="68f36-110">.NET Framework Security</span></span>  
 <span data-ttu-id="68f36-111">L’appel à la méthode <xref:System.Diagnostics.Process.Start%2A> requiert une confiance totale.</span><span class="sxs-lookup"><span data-stu-id="68f36-111">The call to the <xref:System.Diagnostics.Process.Start%2A> method requires full trust.</span></span> <span data-ttu-id="68f36-112">Pour plus d'informations, consultez <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="68f36-112">For more information, see <xref:System.Security.SecurityException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f36-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68f36-113">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel>
- [<span data-ttu-id="68f36-114">LinkLabel, contrôle</span><span class="sxs-lookup"><span data-stu-id="68f36-114">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
