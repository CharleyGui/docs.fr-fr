---
title: Informations système
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- domain names [Windows Forms], retrieving
- SystemInformation class [Windows Forms]
- user names [Windows Forms], retrieving
- system information [Windows Forms]
ms.assetid: 30cf43a3-8cb2-4ff3-862b-6c34576616a8
ms.openlocfilehash: a91e2fd8db0ef338ce30f89f11869f1b6698af3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732581"
---
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="84046-102">Informations système et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84046-102">System Information and Windows Forms</span></span>
<span data-ttu-id="84046-103">Il est parfois nécessaire de recueillir des informations sur l’ordinateur sur lequel votre application s’exécute afin de prendre des décisions dans votre code.</span><span class="sxs-lookup"><span data-stu-id="84046-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="84046-104">Par exemple, vous pouvez avoir une fonction qui n’est applicable que lorsque vous êtes connecté à un domaine de réseau particulier ; dans ce cas, vous avez besoin d’un moyen de déterminer le domaine et de désactiver la fonction si le domaine n’est pas présent.</span><span class="sxs-lookup"><span data-stu-id="84046-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="84046-105">Windows Forms applications peuvent utiliser la classe <xref:System.Windows.Forms.SystemInformation> pour déterminer un certain nombre de choses sur un ordinateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="84046-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="84046-106">L’exemple suivant illustre l’utilisation de la classe <xref:System.Windows.Forms.SystemInformation> pour récupérer les <xref:System.Windows.Forms.SystemInformation.UserName%2A> et <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span><span class="sxs-lookup"><span data-stu-id="84046-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
```vb  
Dim User As String = Windows.Forms.SystemInformation.UserName  
Dim Domain As String = Windows.Forms.SystemInformation.UserDomainName  
  
MessageBox.Show("Good morning " & User & ". You are connected to " _  
& Domain)  
```  
  
```csharp  
string User = SystemInformation.UserName;  
string Domain = SystemInformation.UserDomainName;  
  
MessageBox.Show("Good morning " + User + ". You are connected to "
+ Domain);
```  
  
 <span data-ttu-id="84046-107">Tous les membres de la classe <xref:System.Windows.Forms.SystemInformation> sont en lecture seule ; vous ne pouvez pas modifier les paramètres d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="84046-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="84046-108">Il y a plus de 100 membres de la classe, qui retournent des informations sur tous les éléments du nombre d’écrans attachés à l’ordinateur (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) à l’espacement des icônes dans l’Explorateur Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> et <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span><span class="sxs-lookup"><span data-stu-id="84046-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="84046-109">Parmi les membres les plus utiles de la classe <xref:System.Windows.Forms.SystemInformation> figurent <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>et <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span><span class="sxs-lookup"><span data-stu-id="84046-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84046-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84046-110">See also</span></span>

- <xref:System.Windows.Forms.SystemInformation>
- [<span data-ttu-id="84046-111">Gestion de l'alimentation dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="84046-111">Power Management in Windows Forms</span></span>](power-management-in-windows-forms.md)
