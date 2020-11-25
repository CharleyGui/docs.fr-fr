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
ms.openlocfilehash: 9aed79138499f1aa7b6fa3a28ad4505edd51b041
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731766"
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
 dans `IID` Du type d’instance demandé.  
  
 `ppObject`  
 à Pointeur vers un pointeur vers une instance du type managé qui a été demandé par l’appelant.  
  
## <a name="remarks"></a>Remarques  

 Le common language runtime doit déjà être chargé dans un processus. Par exemple, il peut être chargé à l’aide d’un appel à la fonction [CorBindToRuntimeEx](corbindtoruntimeex-function.md) avant l’appel de la `ClrCreateManagedInstance` fonction. Si le runtime n’est pas chargé, `ClrCreateManagedInstance` tente d’abord de charger le v 1.0.3705 du Runtime. En cas d’échec, il tente de charger la version la plus récente du Runtime.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
- [Hébergement](index.md)
