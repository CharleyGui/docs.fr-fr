---
title: IHostAssemblyStore::ProvideAssembly, méthode
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5fab4ef0d67ab6b86510bd4b2f814d9456213fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763995"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly, méthode
Obtient une référence à un assembly qui n’est pas référencé par le [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) qui est retourné à partir de [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). Le common language runtime (CLR) appelle `ProvideAssembly` pour chaque assembly qui n’apparaît pas dans la liste.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pBindInfo`  
 [in] Un pointeur vers un [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance que l’hôte utilise pour déterminer certaines caractéristiques de liaison, y compris la présence ou l’absence de toute stratégie de contrôle de version et l’assembly à lier.  
  
 `pAssemblyId`  
 [out] Un pointeur vers un identificateur unique pour l’assembly demandé pour ce `IStream`.  
  
 `pHostContext`  
 [out] Un pointeur vers les données spécifiques à l’hôte qui sont utilisés pour déterminer la preuve de l’assembly demandé sans avoir besoin d’une plateforme de l’appel. `pHostContext` correspond à la <xref:System.Reflection.Assembly.HostContext%2A> propriété de managé <xref:System.Reflection.Assembly> classe.  
  
 `ppStmAssemblyImage`  
 [out] Un pointeur vers l’adresse d’un `IStream` qui contient l’image exécutable portable (PE) à charger, ou null si l’assembly est introuvable.  
  
 `ppStmPDB`  
 [out] Un pointeur vers l’adresse d’un `IStream` qui contient les informations de débogage (PDB) de programme, ou null si le fichier .pdb est introuvable.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|L’assembly demandé n’a pas pu être localisé.|  
|E_NOT_SUFFICIENT_BUFFER|La taille de mémoire tampon spécifiée par `pAssemblyId` n’est pas suffisamment grande pour contenir l’identificateur que l’hôte souhaite retourner.|  
  
## <a name="remarks"></a>Notes  
 La valeur d’identité retournée pour `pAssemblyId` est spécifié par l’hôte. Les identificateurs doivent être uniques au sein de la durée de vie d’un processus. Le CLR utilise cette valeur comme identificateur unique pour le flux. Il vérifie chaque valeur sur les valeurs de `pAssemblyId` retourné par d’autres appels à `ProvideAssembly`. Si l’hôte renvoie le même type `pAssemblyId` valeur pour un autre `IStream`, le CLR vérifie si le contenu de ce flux a déjà été mappé. Dans ce cas, le runtime charge la copie existante de l’image au lieu de mapper une nouvelle.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyReferenceList, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
