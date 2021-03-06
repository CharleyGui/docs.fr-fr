---
title: ICLRDataTarget3, interface
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
ms.openlocfilehash: 7297bfa5297878dde6867a99029ac88754a05290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723582"
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3, interface

Sous-classe de [ICLRDataTarget2](iclrdatatarget2-interface.md) qui fournit l’accès aux informations sur les exceptions.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetExceptionRecord, méthode](iclrdatatarget3-getexceptionrecord-method.md)|Appelé par les services d'accès aux données du Common Langage Runtime (CLR) pour récupérer l'enregistrement d'exception associé au processus cible.|  
|[GetExceptionContextRecord, méthode](iclrdatatarget3-getexceptioncontextrecord-method.md)|Appelé par les services d'accès aux données CLR pour récupérer l'enregistrement de contexte associé au processus cible.|  
|[GetExceptionThreadID, méthode](iclrdatatarget3-getexceptionthreadid-method.md)|Appelée par les services d'accès aux données de CLR (Common Language Runtime) pour obtenir l'ID du thread qui a levé l'exception.|  
  
## <a name="remarks"></a>Remarques  

 Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour le processus cible particulier. Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire. La cible ne prend peut-être pas en charge la modification de ses régions de mémoire.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget, interface](iclrdatatarget-interface.md)
- [ICLRDataTarget2, interface](iclrdatatarget2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
