---
title: CorTypeAttr, énumération
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
ms.openlocfilehash: b1586184c91619994ba0dfc9d5dcc277c10f99cf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436449"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr, énumération
Contient des valeurs qui indiquent les métadonnées de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`tdVisibilityMask`|Used for type visibility information.|  
|`tdNotPublic`|Specifies that the type is not in public scope.|  
|`tdPublic`|Specifies that the type is in public scope.|  
|`tdNestedPublic`|Specifies that the type is nested with public visibility.|  
|`tdNestedPrivate`|Specifies that the type is nested with private visibility.|  
|`tdNestedFamily`|Specifies that the type is nested with family visibility.|  
|`tdNestedAssembly`|Specifies that the type is nested with assembly visibility.|  
|`tdNestedFamANDAssem`|Specifies that the type is nested with family and assembly visibility.|  
|`tdNestedFamORAssem`|Specifies that the type is nested with family or assembly visibility.|  
|`tdLayoutMask`|Gets layout information for the type.|  
|`tdAutoLayout`|Specifies that the fields of this type are laid out automatically.|  
|`tdSequentialLayout`|Specifies that the fields of this type are laid out sequentially.|  
|`tdExplicitLayout`|Specifies that field layout is supplied explicitly.|  
|`tdClassSemanticsMask`|Gets semantic information about the type.|  
|`tdClass`|Spécifie que le type est une classe.|  
|`tdInterface`|Spécifie que le type est une interface.|  
|`tdAbstract`|Spécifie que le type est abstrait.|  
|`tdSealed`|Specifies that the type cannot be extended.|  
|`tdSpecialName`|Specifies that the class name is special. Its name describes how.|  
|`tdImport`|Specifies that the type is imported.|  
|`tdSerializable`|Specifies that the type is serializable.|  
|`tdWindowsRuntime`|Specifies that this type is a Windows Runtime type.|  
|`tdStringFormatMask`|Gets information about how strings are encoded and formatted.|  
|`tdAnsiClass`|Specifies that this type interprets an LPTSTR as ANSI.|  
|`tdUnicodeClass`|Specifies that this type interprets an LPTSTR as Unicode.|  
|`tdAutoClass`|Specifies that this type interprets an LPTSTR automatically.|  
|`tdCustomFormatClass`|Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.|  
|`tdCustomFormatMask`|Use this mask to get non-standard encoding information for native interop. The meaning of the values of these two bits is unspecified.|  
|`tdBeforeFieldInit`|Specifies that the type must be initialized before the first attempt to access a static field.|  
|`tdForwarder`|Specifies that the type is exported, and a type forwarder.|  
|`tdReservedMask`|This flag and the flags below are used internally by the common language runtime.|  
|`tdRTSpecialName`|Specifies that the common language runtime should check the name encoding.|  
|`tdHasSecurity`|Specifies that the type has security associated with it.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorHdr.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
