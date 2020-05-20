---
title: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList, méthode
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
ms.openlocfilehash: 91f174cab4986882df795eb531baedfc0dd43962
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615863"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a>ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList, méthode
Obtient une valeur qui indique si le nom fourni correspond au nom d’un assembly dans la liste.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzAssemblyName`  
 dans Nom de l’assembly à rechercher.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La chaîne apparaît dans la liste.|  
|S_FALSE|La chaîne n’apparaît pas dans la liste.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Une fois que la méthode a retourné E_FAIL, le common language runtime n’est plus utilisable dans le processus. Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyIdentityManager, interface](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interface](ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interface](ihostassemblystore-interface.md)
