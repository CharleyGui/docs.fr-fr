---
title: ICLRDataTarget2, interface
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: 6b2700b2f12e312f06640a06e5ec82fbc58f2ca9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860464"
---
# <a name="iclrdatatarget2-interface"></a>ICLRDataTarget2, interface
Sous-classe de [ICLRDataTarget](iclrdatatarget-interface.md) qui est utilisée par la couche des services d’accès aux données pour manipuler les régions de la mémoire virtuelle dans le processus cible.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[AllocVirtual, méthode](iclrdatatarget2-allocvirtual-method.md)|Alloue de la mémoire dans l’espace d’adressage du processus cible.|  
|[FreeVirtual, méthode](iclrdatatarget2-freevirtual-method.md)|Libère de la mémoire qui a été précédemment allouée dans l’espace d’adressage du processus cible.|  
  
## <a name="remarks"></a>Notes   
 Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour le processus cible particulier. Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire. La cible ne prend peut-être pas en charge la modification de ses régions de mémoire.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](iclrdatatarget-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
