---
title: ICLRAssemblyIdentityManager, interface
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: f06c8228d5eb850c0d5ff94d12be03d7fb75023b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615915"
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager, interface
Fournit des méthodes qui prennent en charge la communication entre l’hôte et le common language runtime (CLR) à propos des assemblys.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBindingIdentityFromFile, méthode](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|Obtient les données de liaison de l’identité de l’assembly pour l’assembly dans le chemin d’accès au fichier spécifié.|  
|[GetBindingIdentityFromStream, méthode](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|Obtient les données d’identité d’assembly canoniques pour l’assembly dans le flux spécifié.|  
|[GetCLRAssemblyReferenceList, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|Obtient une instance [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) à partir de la liste d’identités d’assembly partielle fournie.|  
|[GetProbingAssembliesFromReference, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|Obtient un énumérateur [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) pour les identités d’assembly référencées par l’assembly avec l’identité spécifiée.|  
|[GetReferencedAssembliesFromFile, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|Obtient une instance [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) qui contient une liste d’assemblys référencés par l’assembly dans le chemin d’accès au fichier spécifié.|  
|[GetReferencedAssembliesFromStream, méthode](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|Obtient un pointeur vers un `ICLRReferenceAssemblyEnum` objet qui contient les données d’identité de l’assembly pour les assemblys référencés par l’assembly dans le flux spécifié.|  
|[IsStronglyNamed, méthode](iclrassemblyidentitymanager-isstronglynamed-method.md)|Obtient une valeur qui indique si l’assembly spécifié porte un nom fort.|  
  
## <a name="remarks"></a>Notes  
 Utilisez `ICLRAssemblyIdentityManager` pour récupérer des instances de `ICLRAssemblyReferenceList` et pour énumérer les identités d’assembly.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyReferenceList, interface](iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum, interface](iclrprobingassemblyenum-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
