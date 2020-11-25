---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived, méthode
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
ms.openlocfilehash: eba9caece91e369cd46aed652b559ace49c77725
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704902"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived, méthode

Obtient le nombre d’octets qui ont survécu au dernier garbage collection de blocage complet et qui sont référencés par le domaine d’application actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a>Paramètres  

 `dwAppDomainId`  
 dans ID du domaine d’application demandé.  
  
 `pAppDomainBytesSurvived`  
 à Pointeur vers le nombre d’octets qui ont survécu après le dernier garbage collection détenu par ce domaine d’application. Après une collection complète, ce nombre est exact et complet. Après une collection éphémère, ce nombre est potentiellement incomplet. Ce paramètre peut être `null`.  
  
 `pRuntimeBytesSurvived`  
 à Pointeur vers le nombre total d’octets qui ont survécu à partir du dernier garbage collection. Après une collection complète, ce nombre représente le nombre d’octets conservés dans les tas managés. Après une collection éphémère, ce nombre représente le nombre d’octets maintenus actifs dans les générations éphémères. Ce paramètre peut être `null`.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|COR_E_APPDOMAINUNLOADED|Le domaine d’application a été déchargé ou n’existe pas.|  
  
## <a name="remarks"></a>Remarques  

 Les statistiques sont mises à jour uniquement après un garbage collection de blocage complet ; autrement dit, une collection qui comprend toutes les générations et qui arrête l’application pendant que la collection se produit. Par exemple, la <xref:System.GC.Collect?displayProperty=nameWithType> surcharge de méthode effectue une collection bloquante complète. Garbage collection simultanée se produit en arrière-plan et ne bloque pas l’application.  
  
 La `GetCurrentSurvived` méthode est l’équivalent non managé de la propriété managée <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAppDomainResourceMonitor, interface](iclrappdomainresourcemonitor-interface.md)
- [Analyse des ressources du domaine d’application](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
