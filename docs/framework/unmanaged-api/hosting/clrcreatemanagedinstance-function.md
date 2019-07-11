---
title: ClrCreateManagedInstance, fonction
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1ae530b8488dcd375e91058a227316dd38cf4ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779159"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance, fonction
Crée une instance du type managé spécifié.  
  
 Cette fonction a été déconseillée dans le .NET Framework 4. Utiliser l’activation de COM pour créer une instance du type managé ou utilisez l’hébergement (consultez [CLR Interfaces d’hébergement ajoutées dans le .NET Framework 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pTypeName`  
 [in] Un pointeur vers le nom du type d’instance demandé.  
  
 `riid`  
 [in] Le `IID` type de l’instance demandé.  
  
 `ppObject`  
 [out] Pointeur vers un pointeur vers une instance du type managé qui a été demandée par l’appelant.  
  
## <a name="remarks"></a>Notes  
 Le common language runtime doit déjà être chargé dans un processus. Par exemple, il peut être chargé à l’aide d’un appel à la [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) fonctionner avant du `ClrCreateManagedInstance` fonction est appelée. Si le runtime n’est pas chargé, `ClrCreateManagedInstance` essaie d’abord charger v1.0.3705 du runtime. Si cette tentative échoue, il tente de charger la dernière version du runtime.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
