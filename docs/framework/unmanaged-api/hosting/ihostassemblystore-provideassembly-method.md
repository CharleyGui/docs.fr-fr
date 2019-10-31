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
ms.openlocfilehash: a93d700c9c398076d87156cd2eb9c6d0d08cccfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124487"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly, méthode
Obtient une référence à un assembly qui n’est pas référencé par l' [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) retourné par [IHostAssemblyManager :: GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). Le common language runtime (CLR) appelle `ProvideAssembly` pour chaque assembly qui n’apparaît pas dans la liste.  
  
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
 dans Pointeur vers une instance [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) que l’hôte utilise pour déterminer certaines caractéristiques de liaison, y compris la présence ou l’absence de toute stratégie de contrôle de version, et l’assembly auquel effectuer la liaison.  
  
 `pAssemblyId`  
 à Pointeur vers un identificateur unique pour l’assembly demandé pour ce `IStream`.  
  
 `pHostContext`  
 à Pointeur vers des données spécifiques à l’hôte qui est utilisé pour déterminer la preuve de l’assembly demandé sans appel de code non managé. `pHostContext` correspond à la propriété <xref:System.Reflection.Assembly.HostContext%2A> de la classe <xref:System.Reflection.Assembly> managée.  
  
 `ppStmAssemblyImage`  
 à Pointeur vers l’adresse d’un `IStream` qui contient l’image exécutable portable (PE) à charger, ou null si l’assembly est introuvable.  
  
 `ppStmPDB`  
 à Pointeur vers l’adresse d’un `IStream` qui contient les informations de débogage de programme (PDB), ou null si le fichier. pdb est introuvable.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|L’assembly demandé est introuvable.|  
|E_NOT_SUFFICIENT_BUFFER|La taille de la mémoire tampon spécifiée par `pAssemblyId` n’est pas assez grande pour contenir l’identificateur que l’hôte souhaite retourner.|  
  
## <a name="remarks"></a>Notes  
 La valeur d’identité retournée pour `pAssemblyId` est spécifiée par l’hôte. Les identificateurs doivent être uniques dans la durée de vie d’un processus. Le CLR utilise cette valeur comme identificateur unique pour le flux. Il vérifie chaque valeur par rapport aux valeurs de `pAssemblyId` retournées par d’autres appels à `ProvideAssembly`. Si l’hôte retourne la même valeur `pAssemblyId` pour une autre `IStream`, le CLR vérifie si le contenu de ce flux a déjà été mappé. Dans ce cas, le runtime charge la copie existante de l’image au lieu d’en mapper une nouvelle.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyReferenceList, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
