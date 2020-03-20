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
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176537"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance, fonction
Crée une instance du type géré spécifié.  
  
 Cette fonction a été dépréciée dans le cadre .NET 4. Utilisez l’activation COM pour créer une instance du type géré, ou utilisez l’hébergement (voir [interfaces d’hébergement CLR ajoutées dans le cadre .NET 4 et 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
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
 [dans] Un pointeur sur le nom du type d’instance demandé.  
  
 `riid`  
 [dans] Le `IID` type d’instance demandé.  
  
 `ppObject`  
 [out] Un pointeur à un pointeur à une instance du type géré qui a été demandé par l’appelant.  
  
## <a name="remarks"></a>Notes   
 L’heure d’exécution de langue commune devrait déjà être chargée dans un processus. Par exemple, il peut être chargé en utilisant un appel à `ClrCreateManagedInstance` la fonction [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) avant que la fonction ne soit appelée. Si le temps d’exécution n’est pas chargé, `ClrCreateManagedInstance` tente d’abord de charger v1.0.3705 du temps d’exécution. Si cela échoue, il tente de charger la dernière version de l’exécution.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
