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
ms.openlocfilehash: 4e672030ae83b57da6f9ab66630513d79f28b8f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131989"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance, fonction
Crée une instance du type managé spécifié.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4. Utilisez l’activation COM pour créer une instance du type managé ou utilisez l’hébergement (voir [interfaces d’hébergement CLR ajoutées au .NET Framework 4 et 4,5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
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
 dans Pointeur vers le nom du type d’instance demandé.  
  
 `riid`  
 dans `IID` du type d’instance demandé.  
  
 `ppObject`  
 à Pointeur vers un pointeur vers une instance du type managé qui a été demandé par l’appelant.  
  
## <a name="remarks"></a>Notes  
 Le common language runtime doit déjà être chargé dans un processus. Par exemple, il peut être chargé à l’aide d’un appel à la fonction [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) avant l’appel de la fonction `ClrCreateManagedInstance`. Si le runtime n’est pas chargé, `ClrCreateManagedInstance` essaie tout d’abord de charger le v 1.0.3705 du Runtime. En cas d’échec, il tente de charger la version la plus récente du Runtime.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
