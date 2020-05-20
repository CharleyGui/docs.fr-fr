---
title: ICLRErrorReportingManager::EndCustomDump, méthode
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
ms.openlocfilehash: 704d8d0921e671e4172fa6e0ae3f14c4908f289a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615655"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a>ICLRErrorReportingManager::EndCustomDump, méthode
Supprime la configuration de vidage de la pile personnalisée spécifiée dans un appel antérieur à la méthode [ICLRErrorReportingManager :: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`EndCustomDump`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 La `EndCustomDump` méthode efface la configuration de vidage de pile personnalisée définie par un appel antérieur à la `BeginCustomDump` méthode et libère tout état associé. Elle doit être appelée une fois que le vidage de pile personnalisé est terminé.  
  
> [!IMPORTANT]
> L’échec de l’appel `EndCustomDump` entraîne une fuite de mémoire.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CustomDumpItem, structure](customdumpitem-structure.md)
- [ECustomDumpFlavor, énumération](ecustomdumpflavor-enumeration.md)
- [ICLRErrorReportingManager, interface](iclrerrorreportingmanager-interface.md)
