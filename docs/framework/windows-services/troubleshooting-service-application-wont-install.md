---
title: "Dépannage : impossibilité d'installer une application de service"
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
ms.openlocfilehash: c45ab03ec4577d88953b0e43531082a46c29e8fd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053536"
---
# <a name="troubleshooting-service-application-wont-install"></a>Dépannage : impossibilité d'installer une application de service
Si votre application de service ne s’installe pas correctement, vérifiez que la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> de la classe de service est définie avec la même valeur que celle indiquée dans le programme d’installation de ce service. Pour que votre service s’installe correctement, la valeur doit être la même dans les deux instances.  
  
> [!NOTE]
> Vous pouvez également passer en revue les journaux d’installation pour récupérer des commentaires sur le processus d’installation.  
  
 Déterminez également si un autre service portant le même nom est déjà installé. Pour que l’installation réussisse, les noms de service doivent être uniques.  
  
## <a name="see-also"></a>Voir aussi

- [Présentation des applications de service Windows](introduction-to-windows-service-applications.md)
