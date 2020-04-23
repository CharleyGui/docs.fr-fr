---
title: 'Comment : poursuivre un service Windows (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
ms.openlocfilehash: a10e05b0460608a9e67ee4527adf80be3d47438e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053636"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Comment : poursuivre un service Windows (Visual Basic)
Cet exemple utilise le composant <xref:System.ServiceProcess.ServiceController> pour continuer le service d’administration IIS sur l’ordinateur local.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve dans **Système d’exploitation Windows > Services Windows**. Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Une référence de projet à System.serviceprocess.dll.  
  
- Un accès aux membres de l’espace de noms <xref:System.ServiceProcess>. Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Programmation fiable  
 La propriété <xref:System.ServiceProcess.ServiceController.MachineName%2A> de la classe <xref:System.ServiceProcess.ServiceController> est l’ordinateur local par défaut. Pour référencer des services Windows sur un autre ordinateur, remplacez la propriété <xref:System.ServiceProcess.ServiceController.MachineName%2A> par le nom de cet ordinateur.  
  
 Vous pouvez appeler la méthode <xref:System.ServiceProcess.ServiceController.Continue%2A> sur un service seulement si l’état du contrôleur de service est <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.  
  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Le service ne peut pas être repris. (<xref:System.InvalidOperationException>)  
  
- Une erreur s'est produite lors de l'accès à une API système. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Vous pouvez restreindre le contrôle des services sur l’ordinateur à l’aide de l’énumération <xref:System.ServiceProcess.ServiceControllerPermissionAccess>, qui permet de définir des autorisations dans la classe <xref:System.ServiceProcess.ServiceControllerPermission>.  
  
 Vous pouvez restreindre l’accès aux informations de service à l’aide de l’énumération <xref:System.Security.Permissions.PermissionState>, qui permet de définir des autorisations dans la classe <xref:System.Security.Permissions.SecurityPermission>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [Comment : interrompre un service Windows (Visual Basic)](how-to-pause-a-windows-service-visual-basic.md)
