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
# <a name="system-information-and-windows-forms"></a>Informations système et Windows Forms
Il est parfois nécessaire de recueillir des informations sur l’ordinateur sur lequel votre application s’exécute afin de prendre des décisions dans votre code. Par exemple, vous pouvez avoir une fonction qui n’est applicable que lorsque vous êtes connecté à un domaine de réseau particulier ; dans ce cas, vous avez besoin d’un moyen de déterminer le domaine et de désactiver la fonction si le domaine n’est pas présent.  
  
 Windows Forms applications peuvent utiliser la classe <xref:System.Windows.Forms.SystemInformation> pour déterminer un certain nombre de choses sur un ordinateur au moment de l’exécution. L’exemple suivant illustre l’utilisation de la classe <xref:System.Windows.Forms.SystemInformation> pour récupérer les <xref:System.Windows.Forms.SystemInformation.UserName%2A> et <xref:System.Windows.Forms.SystemInformation.UserDomainName%2A>:  
  
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
  
 Tous les membres de la classe <xref:System.Windows.Forms.SystemInformation> sont en lecture seule ; vous ne pouvez pas modifier les paramètres d’un utilisateur. Il y a plus de 100 membres de la classe, qui retournent des informations sur tous les éléments du nombre d’écrans attachés à l’ordinateur (<xref:System.Windows.Forms.SystemInformation.MonitorCount%2A>) à l’espacement des icônes dans l’Explorateur Windows (<xref:System.Windows.Forms.SystemInformation.IconHorizontalSpacing%2A> et <xref:System.Windows.Forms.SystemInformation.IconVerticalSpacing%2A>).  
  
 Parmi les membres les plus utiles de la classe <xref:System.Windows.Forms.SystemInformation> figurent <xref:System.Windows.Forms.SystemInformation.ComputerName%2A>, <xref:System.Windows.Forms.SystemInformation.DbcsEnabled%2A>, <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>et <xref:System.Windows.Forms.SystemInformation.TerminalServerSession%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.SystemInformation>
- [Gestion de l'alimentation dans Windows Forms](power-management-in-windows-forms.md)
