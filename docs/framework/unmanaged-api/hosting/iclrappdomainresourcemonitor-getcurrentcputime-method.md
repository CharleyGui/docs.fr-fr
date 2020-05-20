---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime, méthode
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
ms.openlocfilehash: b411190ff36410c1d293f1e48b31975be8a13aee
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616032"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>ICLRAppDomainResourceMonitor::GetCurrentCpuTime, méthode
Obtient le temps processeur total utilisé par tous les threads lors de l’exécution dans le domaine d’application actuel, depuis la création du domaine d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwAppDomainId`  
 dans ID du domaine d’application demandé.  
  
 `pMilliseconds`  
 à Pointeur vers le temps processeur total qui a été utilisé par tous les threads lors de l’exécution dans le domaine d’application actuel depuis la création du domaine d’application. Ce paramètre peut être `null`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|COR_E_APPDOMAINUNLOADED|Le domaine d’application a été déchargé ou n’existe pas.|  
|E_FAIL|L’analyse des ressources du domaine d’application n’est pas activée.<br /><br /> -ou-<br /><br /> Tous les autres échecs.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est l’équivalent non managé de la propriété managée <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAppDomainResourceMonitor, interface](iclrappdomainresourcemonitor-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Analyse des ressources du domaine d’application](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Hébergement](index.md)
