---
title: Impression plus sécurisée
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 6285b76d01660bfa761ea606421f264bdc0c0af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734881"
---
# <a name="more-secure-printing-in-windows-forms"></a>Impression plus sécurisée dans les Windows Forms
Windows Forms applications incluent souvent des fonctionnalités d’impression. L' .NET Framework utilise la classe <xref:System.Drawing.Printing.PrintingPermission> pour contrôler l’accès aux fonctionnalités d’impression et la valeur d’énumération <xref:System.Drawing.Printing.PrintingPermissionLevel> associée pour indiquer le niveau d’accès. Par défaut, l’impression est activée par défaut dans les zones Intranet local et Internet. Toutefois, le niveau d’accès est limité dans les deux zones. Le fait que votre application puisse imprimer, nécessite une interaction de l’utilisateur ou ne peut pas imprimer dépend de la valeur d’autorisation accordée à l’application. Par défaut, la zone Intranet local reçoit <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> accès et la zone intranet reçoit <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> accès.  
  
 Le tableau suivant présente les fonctionnalités disponibles à chaque niveau d’autorisation d’impression.  
  
|PrintingPermissionLevel|Description|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Fournit un accès complet à toutes les imprimantes installées.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Active l’impression par programmation sur l’imprimante par défaut et l’impression plus sécurisée via une boîte de dialogue d’impression restrictive. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Permet d’imprimer uniquement à partir d’une boîte de dialogue plus restreinte. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Empêche l’accès aux imprimantes. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> est un sous-ensemble de <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Voir aussi

- [Accès plus sécurisé aux fichiers et aux données dans les Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Considérations supplémentaires sur la sécurité des Windows Forms](additional-security-considerations-in-windows-forms.md)
- [Vue d’ensemble de la sécurité dans les Windows Forms](security-in-windows-forms-overview.md)
- [Sécurité de Windows Forms](windows-forms-security.md)
