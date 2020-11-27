---
title: 'Résolution des problèmes : débogage des services Windows'
description: Prise en main du débogage des services Windows. Quand vous déboguez une application de service Windows, votre service et le Gestionnaire des services Windows interagissent.
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
ms.openlocfilehash: 2c1180ef8e3e44c50f10a263d86dcae830d9cd0e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270391"
---
# <a name="troubleshooting-debugging-windows-services"></a>Résolution des problèmes : débogage des services Windows

Quand vous déboguez une application de service Windows, votre service et le **Gestionnaire des services Windows** interagissent. Le **Gestionnaire des services** démarre votre service en appelant la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A>, puis attend 30 secondes que la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> retourne une valeur. Si la méthode ne retourne aucune valeur au terme de ce délai, le gestionnaire affiche une erreur indiquant que le service ne peut pas être démarré.  
  
 Quand vous déboguez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> comme décrit dans [Guide pratique pour déboguer des applications de service Windows](how-to-debug-windows-service-applications.md), tenez compte de ce délai de 30 secondes. Si vous placez un point d’arrêt dans la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et que vous n’effectuez aucun pas à pas détaillé dans un délai de 30 secondes, le gestionnaire ne démarre pas le service.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : déboguer les applications de service Windows](how-to-debug-windows-service-applications.md)
- [Introduction aux applications de service Windows](introduction-to-windows-service-applications.md)
