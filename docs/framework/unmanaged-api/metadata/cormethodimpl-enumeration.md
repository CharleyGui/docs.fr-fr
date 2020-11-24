---
title: CorMethodImpl, énumération
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
ms.openlocfilehash: 40e82997e58292a10f5e960cc9d9785d9ea8946a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676970"
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl, énumération

Contient des valeurs qui décrivent les fonctionnalités d’implémentation d’une méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`miCodeTypeMask`|Indicateurs qui décrivent le type de code.|  
|`miIL`|Spécifie que l’implémentation de la méthode est en langage MSIL (Microsoft Intermediate Language).|  
|`miNative`|Spécifie que l’implémentation de la méthode est native.|  
|`miOPTIL`|Spécifie que l’implémentation de la méthode est OPTI.|  
|`miRuntime`|Spécifie que l’implémentation de la méthode est fournie par le common language runtime.|  
|`miManagedMask`|Indicateurs qui indiquent si le code est managé ou non managé.|  
|`miUnmanaged`|Spécifie que l’implémentation de la méthode n’est pas gérée.|  
|`miManaged`|Spécifie que l’implémentation de la méthode est managée.|  
|`miForwardRef`|Spécifie que la méthode est définie. Cet indicateur est principalement utilisé dans les scénarios de fusion.|  
|`miPreserveSig`|Spécifie que la signature de la méthode ne peut pas être tronquée pour une conversion HRESULT.|  
|`miInternalCall`|Réservé à un usage interne par la common language runtime.|  
|`miSynchronized`|Spécifie que la méthode est à thread unique par le biais de son corps.|  
|`miNoInlining`|Spécifie que la méthode ne peut pas être inline.|  
|`miAggressiveInlining`|Spécifie que la méthode doit être inline si possible.|  
|`miNoOptimization`|Spécifie que la méthode ne doit pas être optimisée.|  
|`miMaxMethodImplVal`|Valeur maximale valide pour `CorMethodImpl` .|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
