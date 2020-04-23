---
title: 'Résolution des problèmes : débogage des services Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
author: ghogen
ms.openlocfilehash: cbedb0051cbb08c2875e145a2bad35ae4d02a74e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053507"
---
# <a name="troubleshooting-debugging-windows-services"></a>Résolution des problèmes : débogage des services Windows
Quand vous déboguez une application de service Windows, votre service et le **Gestionnaire des services Windows** interagissent. Le **Gestionnaire des services** démarre votre service en appelant la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, puis attend 30 secondes que la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retourne une valeur. Si la méthode ne retourne aucune valeur au terme de ce délai, le gestionnaire affiche une erreur indiquant que le service ne peut pas être démarré.  
  
 Quand vous déboguez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> comme décrit dans [Guide pratique pour déboguer des applications de service Windows](how-to-debug-windows-service-applications.md), tenez compte de ce délai de 30 secondes. Si vous placez un point d’arrêt dans la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et que vous n’effectuez aucun pas à pas détaillé dans un délai de 30 secondes, le gestionnaire ne démarre pas le service.  
  
## <a name="see-also"></a>Voir aussi

- [Comment : déboguer des applications de service Windows](how-to-debug-windows-service-applications.md)
- [Présentation des applications de service Windows](introduction-to-windows-service-applications.md)
