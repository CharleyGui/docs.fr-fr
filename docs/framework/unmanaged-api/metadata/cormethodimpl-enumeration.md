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
ms.openlocfilehash: a76a7a2d4ad68e367e38e175377aff40ce399346
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450209"
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
|`miCodeTypeMask`|Flags that describe code type.|  
|`miIL`|Specifies that the method implementation is Microsoft intermediate language (MSIL).|  
|`miNative`|Spécifie que l’implémentation de la méthode est native.|  
|`miOPTIL`|Specifies that the method implementation is OPTIL.|  
|`miRuntime`|Specifies that the method implementation is provided by the common language runtime.|  
|`miManagedMask`|Flags that indicate whether the code is managed or unmanaged.|  
|`miUnmanaged`|Specifies that the method implementation is unmanaged.|  
|`miManaged`|Specifies that the method implementation is managed.|  
|`miForwardRef`|Specifies that the method is defined. This flag is used primarily in merge scenarios.|  
|`miPreserveSig`|Specifies that the method signature cannot be mangled for an HRESULT conversion.|  
|`miInternalCall`|Reserved for internal use by the common language runtime.|  
|`miSynchronized`|Specifies that the method is single-threaded through its body.|  
|`miNoInlining`|Spécifie que la méthode ne peut pas être inline.|  
|`miAggressiveInlining`|Specifies that the method should be inlined if possible.|  
|`miNoOptimization`|Specifies that the method should not be optimized.|  
|`miMaxMethodImplVal`|The maximum valid value for a `CorMethodImpl`.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorHdr.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
