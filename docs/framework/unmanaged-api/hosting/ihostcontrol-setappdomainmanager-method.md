---
title: IHostControl::SetAppDomainManager, méthode
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
ms.openlocfilehash: 2f4c004db39c14e7a71b0caa55a6089e8f69ca3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680653"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>IHostControl::SetAppDomainManager, méthode

Avertit l’hôte qu’un domaine d’application a été créé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwAppDomainID`  
 dans Identificateur numérique du sélectionné <xref:System.AppDomain> .  
  
 `pUnkAppDomainManager`  
 dans Pointeur vers l' <xref:System.AppDomainManager> objet que l’hôte implémente en tant que `IUnknown` .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  

 Le <xref:System.AppDomainManager> fournit à l’hôte un mécanisme de démarrage dans le code managé et de contrôle de la création et des paramètres de chaque <xref:System.AppDomain> . Le <xref:System.AppDomainManager> est chargé dans chaque <xref:System.AppDomain> lors de la <xref:System.AppDomain> création de. Si c’est le cas, le CLR avertit l’hôte que le domaine d’application a été créé en définissant la valeur du `pUnkAppDomainManager` paramètre.  
  
 Dans son implémentation de la `SetAppDomainManager` méthode, l’hôte peut définir le nom et le type de l’assembly pour le gestionnaire de domaine d’application.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [IHostControl, interface](ihostcontrol-interface.md)
