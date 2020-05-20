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
ms.openlocfilehash: ecd618ecf08836ea5e38ce738f97fc91ee6426f4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616812"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance, fonction
Crée une instance du type managé spécifié.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4. Utilisez l’activation COM pour créer une instance du type managé ou utilisez l’hébergement (voir [interfaces d’hébergement CLR ajoutées au .NET Framework 4 et 4,5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
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
 dans `IID`Du type d’instance demandé.  
  
 `ppObject`  
 à Pointeur vers un pointeur vers une instance du type managé qui a été demandé par l’appelant.  
  
## <a name="remarks"></a>Notes  
 Le common language runtime doit déjà être chargé dans un processus. Par exemple, il peut être chargé à l’aide d’un appel à la fonction [CorBindToRuntimeEx](corbindtoruntimeex-function.md) avant l’appel de la `ClrCreateManagedInstance` fonction. Si le runtime n’est pas chargé, `ClrCreateManagedInstance` tente d’abord de charger le v 1.0.3705 du Runtime. En cas d’échec, il tente de charger la version la plus récente du Runtime.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
- [Hébergement](index.md)
