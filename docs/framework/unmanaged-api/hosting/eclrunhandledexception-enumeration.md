---
title: EClrUnhandledException, énumération
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 63b07dda2293d3e05bd3c8fcdc45f20a498ea54c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616305"
---
# <a name="eclrunhandledexception-enumeration"></a>EClrUnhandledException, énumération
Décrit les options disponibles pour gérer les exceptions qui ne sont pas gérées dans le code utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|Spécifie que le comportement par défaut se produit. Le processus est détruit.|  
|`eHostDeterminedPolicy`|Spécifie que le common language runtime (CLR) ignore les exceptions non gérées et laisse l’hôte déterminer toute action supplémentaire.|  
  
## <a name="remarks"></a>Notes  
 Pour spécifier que le CLR se comporte comme des versions antérieures, utilisez le `eHostDeterminedPolicy` membre.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrFailure, énumération](eclrfailure-enumeration.md)
- [EClrOperation, énumération](eclroperation-enumeration.md)
- [ICLRPolicyManager, interface](iclrpolicymanager-interface.md)
- [SetUnhandledExceptionPolicy, méthode](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [IHostPolicyManager, interface](ihostpolicymanager-interface.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
