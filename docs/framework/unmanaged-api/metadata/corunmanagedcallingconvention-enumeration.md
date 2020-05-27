---
title: CorUnmanagedCallingConvention, énumération
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
ms.openlocfilehash: b4c521489f38360d45c2cf8ff3780e057299f0b4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008948"
---
# <a name="corunmanagedcallingconvention-enumeration"></a>CorUnmanagedCallingConvention, énumération
Spécifie les conventions d’appel pour le code non managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|Convention d’appel du langage C.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|Convention d’appel standard.|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|Convention d’appel « This ».|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|Convention d’appel « Fast ».|  
|`IMAGE_CEE_CS_CALLCONV_C`|Non utilisé.|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|Non utilisé.|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|Non utilisé.|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|Non utilisé.|  
  
## <a name="remarks"></a>Remarques  
 Le CLR ne prend pas en charge la Convention d’appel « Fast » dans le .NET Framework version 1,0.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
