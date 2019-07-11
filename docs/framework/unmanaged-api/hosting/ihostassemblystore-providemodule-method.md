---
title: IHostAssemblyStore::ProvideModule, méthode
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9290fd70b17b5a6456d85cb4b037ebbc62e028f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763978"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule, méthode
Résout un fichier de ressources du module au sein d’un assembly ou un lié (mais non incorporé).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pBindInfo`  
 [in] Un pointeur vers un [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance qui décrit le module demandé <xref:System.AppDomain>, assembly et le nom de module.  
  
 `pdwModuleId`  
 [out] Un pointeur vers un identificateur unique pour le `IStream` contenant le module chargé.  
  
 `ppStmModuleImage`  
 [out] Un pointeur vers l’adresse d’un `IStream` de l’objet, qui contient l’image exécutable portable (PE) à charger, ou null si le module est introuvable.  
  
 `ppStmPDB`  
 [out] Un pointeur vers l’adresse d’un `IStream` de l’objet, qui contient les informations de débogage (PDB) de programme pour le module demandé, ou null si le fichier .pdb est introuvable.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ProvideModule` retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.|  
|HOST_E_TIMEOUT|L’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|L’assembly demandé ou une ressource liée n’a pas été trouvé.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` n’est pas assez grand pour contenir l’identificateur que l’hôte souhaite retourner.|  
  
## <a name="remarks"></a>Notes  
 La valeur d’identité retournée pour `pdwModuleId` est spécifié par l’hôte. Les identificateurs doivent être uniques au sein de la durée de vie d’un processus. Le CLR utilise cette valeur comme identificateur unique pour le flux associé. Il vérifie chaque valeur sur les valeurs de `pAssemblyId` retournées par les appels à [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) et les valeurs de `pdwModuleId` retourné par d’autres appels à `ProvideModule`. Si l’hôte retourne la même valeur d’identificateur pour un autre `IStream`, le CLR vérifie si le contenu de ce flux a déjà été mappé. Dans ce cas, le CLR charge la copie existante de l’image au lieu de mapper une nouvelle. Par conséquent, l’identificateur doit également se chevauchent pas avec les identificateurs de l’assembly retournés par `ProvideAssembly`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyReferenceList, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interface](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
