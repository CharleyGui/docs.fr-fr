---
title: Informations système et Windows Forms
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
ms.openlocfilehash: 2edc2e867259f8884467c3d5b0ae3d22ba391a77
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380119"
---
# <a name="system-information-and-windows-forms"></a><span data-ttu-id="e9a85-102">Informations système et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9a85-102">System Information and Windows Forms</span></span>
<span data-ttu-id="e9a85-103">Il est parfois nécessaire de rassembler des informations sur l’ordinateur de votre application est exécuté afin de prendre des décisions dans votre code.</span><span class="sxs-lookup"><span data-stu-id="e9a85-103">Sometimes it is necessary to gather information about the computer that your application is running on in order to make decisions in your code.</span></span> <span data-ttu-id="e9a85-104">Par exemple, vous pouvez avoir une fonction qui est uniquement applicable lorsque connecté à un domaine de réseau particulier ; Dans ce cas, vous devez permettent de déterminer le domaine et de désactiver la fonction si le domaine n’est pas présent.</span><span class="sxs-lookup"><span data-stu-id="e9a85-104">For example, you might have a function that is only applicable when connected to a particular network domain; in this case you would need a way to determine the domain and disable the function if the domain is not present.</span></span>  
  
 <span data-ttu-id="e9a85-105">Les applications Windows Forms peuvent utiliser la <xref:System.Windows.Forms.SystemInformation> classe pour déterminer un certain nombre de choses sur un ordinateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e9a85-105">Windows Forms applications can use the <xref:System.Windows.Forms.SystemInformation> class to determine a number of things about a computer at run time.</span></span> <span data-ttu-id="e9a85-106">L’exemple suivant montre comment utiliser le <xref:System.Windows.Forms.SystemInformation> classe à récupérer le <xref:System.Windows.Forms.SystemInformation.UserName%2A> et <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span><span class="sxs-lookup"><span data-stu-id="e9a85-106">The following example demonstrates using the <xref:System.Windows.Forms.SystemInformation> class to retrieve the <xref:System.Windows.Forms.SystemInformation.UserName%2A> and <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:</span></span>  
  
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
  
 <span data-ttu-id="e9a85-107">Tous les membres de la <xref:System.Windows.Forms.SystemInformation> classe sont en lecture seule ; vous ne pouvez pas modifier les paramètres d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e9a85-107">All members of the <xref:System.Windows.Forms.SystemInformation> class are read-only; you cannot modify a user's settings.</span></span> <span data-ttu-id="e9a85-108">Il existe plus de 100 membres de la classe, en retournant des informations sur tous les éléments à partir du nombre d’écrans connectés à l’ordinateur (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) de l’espacement des icônes dans l’Explorateur Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> et <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span><span class="sxs-lookup"><span data-stu-id="e9a85-108">There are over 100 members of the class, returning information on everything from the number of monitors attached to the computer (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) to the spacing of icons in Windows Explorer (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> and <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).</span></span>  
  
 <span data-ttu-id="e9a85-109">Membres les plus utiles de la <xref:System.Windows.Forms.SystemInformation> classe inclure <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, et <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span><span class="sxs-lookup"><span data-stu-id="e9a85-109">Some of the more useful members of the <xref:System.Windows.Forms.SystemInformation> class include <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>, and <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a85-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9a85-110">See also</span></span>

- <xref:System.Windows.Forms.SystemInformation>
- [<span data-ttu-id="e9a85-111">Gestion de l'alimentation dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e9a85-111">Power Management in Windows Forms</span></span>](power-management-in-windows-forms.md)
