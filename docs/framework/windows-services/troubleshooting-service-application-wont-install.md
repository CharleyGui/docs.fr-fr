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
author: ghogen
ms.openlocfilehash: 4a57fb6975a6ded48abf7c8fd7eacec16e4f94d8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925525"
---
# <a name="troubleshooting-service-application-wont-install"></a><span data-ttu-id="3ab27-104">Résolution des problèmes : impossibilité d’installer une application de service</span><span class="sxs-lookup"><span data-stu-id="3ab27-104">Troubleshooting: Service Application Won't Install</span></span>
<span data-ttu-id="3ab27-105">Si votre application de service ne s’installe pas correctement, vérifiez que la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> de la classe de service est définie avec la même valeur que celle indiquée dans le programme d’installation de ce service.</span><span class="sxs-lookup"><span data-stu-id="3ab27-105">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="3ab27-106">Pour que votre service s’installe correctement, la valeur doit être la même dans les deux instances.</span><span class="sxs-lookup"><span data-stu-id="3ab27-106">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ab27-107">Vous pouvez également passer en revue les journaux d’installation pour récupérer des commentaires sur le processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="3ab27-107">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="3ab27-108">Déterminez également si un autre service portant le même nom est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="3ab27-108">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="3ab27-109">Pour que l’installation réussisse, les noms de service doivent être uniques.</span><span class="sxs-lookup"><span data-stu-id="3ab27-109">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ab27-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ab27-110">See also</span></span>

- [<span data-ttu-id="3ab27-111">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="3ab27-111">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
