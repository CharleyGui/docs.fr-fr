---
title: ICLRDataTarget, interface
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: 0d3e6a95d8fd71a67b97923dac53c1f615dfe666
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703419"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget, interface

Fournit des méthodes pour l’interaction avec un élément cible du common language runtime (CLR).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetCurrentThreadID, méthode](iclrdatatarget-getcurrentthreadid-method.md)|Obtient l’identificateur de système d’exploitation pour le thread actuel.|  
|[GetImageBase, méthode](iclrdatatarget-getimagebase-method.md)|Obtient l’adresse mémoire de base pour l’image spécifiée.|  
|[GetMachineType, méthode](iclrdatatarget-getmachinetype-method.md)|Obtient un identificateur pour le type de jeu d’instructions que le processus cible utilise.|  
|[GetPointerSize, méthode](iclrdatatarget-getpointersize-method.md)|Obtient la taille, en octets, d’un pointeur vers la cible actuelle.|  
|[GetThreadContext, méthode](iclrdatatarget-getthreadcontext-method.md)|Obtient un pointeur vers le contexte du thread avec l’identificateur spécifié.|  
|[GetTLSValue, méthode](iclrdatatarget-gettlsvalue-method.md)|Obtient une valeur dans le stockage local des threads (TLS) à l’index spécifié pour le thread spécifié.|  
|[ReadVirtual, méthode](iclrdatatarget-readvirtual-method.md)|Lit les données à partir de l’adresse mémoire virtuelle spécifiée dans la mémoire tampon spécifiée.|  
|[Méthode de requête](iclrdatatarget-request-method.md)|Appelée par les services d’accès aux données common language runtime (CLR) pour demander une opération, comme défini par l’implémentation.|  
|[SetThreadContext, méthode](iclrdatatarget-setthreadcontext-method.md)|Définit le contexte actuel du thread spécifié dans le processus cible.|  
|[SetTLSValue, méthode](iclrdatatarget-settlsvalue-method.md)|Définit une valeur dans le stockage local des threads (TLS) du thread spécifié dans le processus cible.|  
|[WriteVirtual, méthode](iclrdatatarget-writevirtual-method.md)|Écrit des données à partir de la mémoire tampon spécifiée dans l’adresse mémoire virtuelle spécifiée.|  
  
## <a name="remarks"></a>Remarques  

 Le client API (autrement dit, le débogueur) doit implémenter cette interface en fonction de l’élément cible particulier. Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRDataTarget2, interface](iclrdatatarget2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
