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
ms.openlocfilehash: 51c06a7f8ea22fc73236131954781d8755274041
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789086"
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
  
## <a name="parameters"></a>Parameters  
 `addr`  
 dans Valeur `CLRDATA_ADDRESS` qui spécifie l’adresse de départ demandée de la mémoire à allouer.  
  
 `size`  
 dans Taille, en octets, de la mémoire à allouer.  
  
 `typeFlags`  
 dans Indicateurs qui contrôlent l’allocation de mémoire. Consultez la fonction de `VirtualAlloc` Win32.  
  
 `protectFlags`  
 dans Attributs de protection pour la mémoire allouée. Consultez la fonction de `VirtualAlloc` Win32.  
  
 `virt`  
 à Pointeur vers une valeur `CLRDATA_ADDRESS` qui spécifie l’adresse de départ réelle de la mémoire allouée.  
  
## <a name="remarks"></a>Notes  
 La méthode `AllocVirtual` sert de wrapper logique pour la fonction `VirtualAlloc` Win32.  
  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget2, interface](iclrdatatarget2-interface.md)
- [FreeVirtual, méthode](iclrdatatarget2-freevirtual-method.md)
