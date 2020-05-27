---
title: IHostSecurityManager, interface
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
ms.openlocfilehash: b2c334c7a757c2f4044d08787bdae93ffc2804e4
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803893"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager, interface
Fournit des méthodes qui autorisent l’accès et le contrôle sur le contexte de sécurité du thread en cours d’exécution.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetSecurityContext, méthode](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Obtient le [IHostSecurityContext](ihostsecuritycontext-interface.md) demandé à partir de l’hôte.|  
|[ImpersonateLoggedOnUser, méthode](ihostsecuritymanager-impersonateloggedonuser-method.md)|Demande que le code soit exécuté à l’aide des informations d’identification de l’identité de l’utilisateur actuel.|  
|[OpenThreadToken, méthode](ihostsecuritymanager-openthreadtoken-method.md)|Ouvre le jeton d’accès discrétionnaire associé au thread actuel.|  
|[RevertToSelf, méthode](ihostsecuritymanager-reverttoself-method.md)|Termine l’emprunt d’identité de l’identité de l’utilisateur actuel et retourne le jeton de thread d’origine.|  
|[SetSecurityContext, méthode](ihostsecuritymanager-setsecuritycontext-method.md)|Définit le contexte de sécurité pour le thread en cours d’exécution.|  
|[SetThreadToken, méthode](ihostsecuritymanager-setthreadtoken-method.md)|Définit un handle pour le thread en cours d’exécution.|  
  
## <a name="remarks"></a>Notes  
 Un hôte peut contrôler tout l’accès du code aux jetons de thread à la fois par le common language runtime (CLR) et le code utilisateur. Il peut également s’assurer que les informations de contexte de sécurité complètes sont transmises sur des opérations asynchrones ou des points de code avec accès restreint au code. `IHostSecurityContext`encapsule ces informations de contexte de sécurité, qui sont opaques pour le CLR.  
  
 Le CLR gère le contexte de thread managé en interne. Il interroge la spécifique au processus `IHostSecurityManager` dans les situations suivantes :  
  
- Sur le thread finaliseur, pendant l’exécution du finaliseur.  
  
- Pendant l’exécution du constructeur de module et de classe.  
  
- À des points asynchrones sur le thread de travail, dans les appels à la méthode [IHostThreadPoolManager :: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) .  
  
- Dans la maintenance des ports de terminaison d’e/s.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostSecurityContext, interface](ihostsecuritycontext-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
