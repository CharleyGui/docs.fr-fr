---
title: ICLRErrorReportingManager::BeginCustomDump, méthode
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 4c83ffaf920abe005ba987e0a744e13aa0d3c016
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615668"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a>ICLRErrorReportingManager::BeginCustomDump, méthode
Spécifie la configuration des dumps de tas personnalisés pour le rapport d’erreurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `dwFlavor`  
 dans Valeur [ECustomDumpFlavor,](ecustomdumpflavor-enumeration.md) qui indique le type de dump du tas sur lequel générer le dump du tas personnalisé.  
  
 `dwNumItems`  
 dans Longueur du `items` tableau. Si `dwFlavor` n’est pas DUMP_FLAVOR_Mini, `dwNumItems` doit être égal à zéro.  
  
 `items`  
 dans Tableau d’instances [CustomDumpItem](customdumpitem-structure.md) , spécifiant les éléments à ajouter au mini-vidage. Si `dwFlavor` n’est pas DUMP_FLAVOR_Mini, `items` doit avoir la valeur null.  
  
 `dwReserved`  
 [in] Réservé pour une future utilisation.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Retour réussi de la méthode.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Notes  
 La `BeginCustomDump` méthode définit une configuration de vidage de tas personnalisée. La méthode [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) efface la configuration du dump du tas personnalisé et libère tous les États associés. Elle doit être appelée une fois que le dump du tas personnalisé est terminé.  
  
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
