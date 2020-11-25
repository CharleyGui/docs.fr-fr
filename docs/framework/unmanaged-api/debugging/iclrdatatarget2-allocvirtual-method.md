---
title: ICLRDataTarget2::AllocVirtual, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
ms.openlocfilehash: 6d3985919ea7e766db7d07e4ed81484851156ca5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723662"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual, méthode

Appelée par les services d’accès aux données common language runtime (CLR) pour allouer de la mémoire dans l’espace d’adressage de ce processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `addr`  
 dans `CLRDATA_ADDRESS` Valeur qui spécifie l’adresse de départ demandée de la mémoire à allouer.  
  
 `size`  
 dans Taille, en octets, de la mémoire à allouer.  
  
 `typeFlags`  
 dans Indicateurs qui contrôlent l’allocation de mémoire. Consultez la `VirtualAlloc` fonction Win32.  
  
 `protectFlags`  
 dans Attributs de protection pour la mémoire allouée. Consultez la `VirtualAlloc` fonction Win32.  
  
 `virt`  
 à Pointeur vers une `CLRDATA_ADDRESS` valeur qui spécifie l’adresse de départ réelle de la mémoire allouée.  
  
## <a name="remarks"></a>Remarques  

 La `AllocVirtual` méthode sert de wrapper logique pour la fonction Win32 `VirtualAlloc` .  
  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget2, interface](iclrdatatarget2-interface.md)
- [FreeVirtual, méthode](iclrdatatarget2-freevirtual-method.md)
