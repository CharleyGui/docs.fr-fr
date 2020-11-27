---
title: 'Résolution des problèmes : impossibilité d’installer une application de service'
description: Résolvez les problèmes si votre application de service ne s’installe pas. Assurez-vous que la propriété ServiceName pour la classe de service est définie correctement.
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
ms.openlocfilehash: 02ac95c22007caa6e30300fb8a98178f11cecd14
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270352"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="eee3a-104">Résolution des problèmes : impossibilité d’installer une application de service</span><span class="sxs-lookup"><span data-stu-id="eee3a-104">Troubleshooting: Service Application Won't Install</span></span>

<span data-ttu-id="eee3a-105">Si votre application de service ne s’installe pas correctement, vérifiez que la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> de la classe de service est définie avec la même valeur que celle indiquée dans le programme d’installation de ce service.</span><span class="sxs-lookup"><span data-stu-id="eee3a-105">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="eee3a-106">Pour que votre service s’installe correctement, la valeur doit être la même dans les deux instances.</span><span class="sxs-lookup"><span data-stu-id="eee3a-106">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eee3a-107">Vous pouvez également passer en revue les journaux d’installation pour récupérer des commentaires sur le processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="eee3a-107">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="eee3a-108">Déterminez également si un autre service portant le même nom est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="eee3a-108">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="eee3a-109">Pour que l’installation réussisse, les noms de service doivent être uniques.</span><span class="sxs-lookup"><span data-stu-id="eee3a-109">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee3a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eee3a-110">See also</span></span>

- [<span data-ttu-id="eee3a-111">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="eee3a-111">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
