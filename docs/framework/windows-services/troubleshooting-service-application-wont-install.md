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
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="b454b-102">Dépannage : impossibilité d'installer une application de service</span><span class="sxs-lookup"><span data-stu-id="b454b-102">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="b454b-103">Si votre application de service ne s’installe pas correctement, vérifiez que la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> de la classe de service est définie avec la même valeur que celle indiquée dans le programme d’installation de ce service.</span><span class="sxs-lookup"><span data-stu-id="b454b-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="b454b-104">Pour que votre service s’installe correctement, la valeur doit être la même dans les deux instances.</span><span class="sxs-lookup"><span data-stu-id="b454b-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b454b-105">Vous pouvez également passer en revue les journaux d’installation pour récupérer des commentaires sur le processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="b454b-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="b454b-106">Déterminez également si un autre service portant le même nom est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="b454b-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="b454b-107">Pour que l’installation réussisse, les noms de service doivent être uniques.</span><span class="sxs-lookup"><span data-stu-id="b454b-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b454b-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b454b-108">See also</span></span>

- [<span data-ttu-id="b454b-109">Présentation des applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="b454b-109">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
