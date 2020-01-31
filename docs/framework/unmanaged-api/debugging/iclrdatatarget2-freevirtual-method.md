---
title: ICLRDataTarget2::FreeVirtual, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: 7eda9bfff6de6b386c16ad0a188931d9d3adcb93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793657"
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual, méthode
Appelée par les services d’accès aux données common language runtime (CLR) pour libérer de la mémoire qui a été précédemment allouée dans l’espace d’adressage du processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `addr`  
 dans Valeur `CLRDATA_ADDRESS` qui spécifie l’adresse de départ de la mémoire à libérer.  
  
 `size`  
 dans Taille, en octets, de la mémoire à libérer.  
  
 `typeFlags`  
 dans Indicateurs qui contrôlent la libération de la mémoire. Consultez la fonction de `VirtualFree` Win32.  
  
## <a name="remarks"></a>Notes  
 La méthode `FreeVirtual` sert de wrapper logique pour la fonction `VirtualFree` Win32.  
  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget2, interface](iclrdatatarget2-interface.md)
- [AllocVirtual, méthode](iclrdatatarget2-allocvirtual-method.md)
