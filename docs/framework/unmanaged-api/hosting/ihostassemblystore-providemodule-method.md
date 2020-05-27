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
ms.openlocfilehash: 002f4177f19c2aae99e91e3fe1029b81e17481dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805012"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule, méthode
Résout un module dans un assembly ou un fichier de ressources lié (mais pas incorporé).  
  
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
 dans Pointeur vers une instance [ModuleBindInfo](modulebindinfo-structure.md) qui décrit le nom du module, de l' <xref:System.AppDomain> assembly et du nom du module demandés.  
  
 `pdwModuleId`  
 à Pointeur vers un identificateur unique pour le `IStream` contenant le module chargé.  
  
 `ppStmModuleImage`  
 à Pointeur vers l’adresse d’un `IStream` objet, qui contient l’image PE (Portable Executable) à charger, ou null si le module est introuvable.  
  
 `ppStmPDB`  
 à Pointeur vers l’adresse d’un `IStream` objet, qui contient les informations de débogage de programme pour le module demandé, ou null si le fichier. pdb est introuvable.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ProvideModule`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|L’assembly ou la ressource liée demandé est introuvable.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId`n’est pas assez grand pour contenir l’identificateur que l’hôte souhaite retourner.|  
  
## <a name="remarks"></a>Notes  
 La valeur d’identité retournée pour `pdwModuleId` est spécifiée par l’hôte. Les identificateurs doivent être uniques dans la durée de vie d’un processus. Le CLR utilise cette valeur comme identificateur unique pour le flux associé. Il vérifie chaque valeur par rapport aux valeurs `pAssemblyId` retournées par les appels à [ProvideAssembly](ihostassemblystore-provideassembly-method.md) et aux valeurs `pdwModuleId` retournées par d’autres appels à `ProvideModule` . Si l’hôte retourne la même valeur d’identificateur pour un autre `IStream` , le CLR vérifie si le contenu de ce flux a déjà été mappé. Si c’est le cas, le CLR charge la copie existante de l’image au lieu d’en mapper une nouvelle. Par conséquent, l’identificateur ne doit pas non plus chevaucher les identificateurs d’assembly retournés par `ProvideAssembly` .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interface](ihostassemblystore-interface.md)
