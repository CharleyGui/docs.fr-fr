---
title: CorNativeType, énumération
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
ms.openlocfilehash: 09a351db65c7ed310d3eb68c71a5207ed6040dd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177970"
---
# <a name="cornativetype-enumeration"></a>CorNativeType, énumération
Contient des valeurs qui décrivent les types non managés natifs.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|Obsolète.|  
|`NATIVE_TYPE_VOID`|Obsolète.|  
|`NATIVE_TYPE_BOOLEAN`|Une valeur Boolean 4-byte, où TRUE est non-zéro et FALSE est zéro.|  
|`NATIVE_TYPE_I1`|Une valeur 8 bits signée.|  
|`NATIVE_TYPE_U1`|Une valeur integer 8 bits non signée.|  
|`NATIVE_TYPE_I2`|Une valeur 16 bits signée.|  
|`NATIVE_TYPE_U2`|Une valeur integer 16 bits non signée.|  
|`NATIVE_TYPE_I4`|Valeur d’entier 32 bits signé.|  
|`NATIVE_TYPE_U4`|Valeur d'entier 32 bits non signé.|  
|`NATIVE_TYPE_I8`|Une valeur 64 bits signée.|  
|`NATIVE_TYPE_U8`|Une valeur integer 64 bits non signée.|  
|`NATIVE_TYPE_R4`|Une valeur numérique à 4 points flottants.|  
|`NATIVE_TYPE_R8`|Une valeur numérique flottante de 8 points.|  
|`NATIVE_TYPE_SYSCHAR`|Obsolète.|  
|`NATIVE_TYPE_VARIANT`|Obsolète.|  
|`NATIVE_TYPE_CURRENCY`|Un type COM numérique qui <xref:System.Decimal> correspond au type géré.|  
|`NATIVE_TYPE_PTR`|Obsolète.|  
|`NATIVE_TYPE_DECIMAL`|Obsolète.|  
|`NATIVE_TYPE_DATE`|Obsolète.|  
|`NATIVE_TYPE_BSTR`|COM Interop.|  
|`NATIVE_TYPE_LPSTR`|Une valeur de chaîne LPSTR.|  
|`NATIVE_TYPE_LPWSTR`|Une valeur de chaîne LPWSTR.|  
|`NATIVE_TYPE_LPTSTR`|Une valeur de chaîne LPTSTR.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Une valeur de chaîne fixe et définie par le système.|  
|`NATIVE_TYPE_OBJECTREF`|Obsolète.|  
|`NATIVE_TYPE_IUNKNOWN`|COM Interop.|  
|`NATIVE_TYPE_IDISPATCH`|COM Interop.|  
|`NATIVE_TYPE_STRUCT`|Une valeur de structure indigène.|  
|`NATIVE_TYPE_INTF`|COM Interop.|  
|`NATIVE_TYPE_SAFEARRAY`|COM Interop.|  
|`NATIVE_TYPE_FIXEDARRAY`|Une valeur de tableau à longueur fixe.|  
|`NATIVE_TYPE_INT`|Une valeur d’intégrer signée 16 bits.|  
|`NATIVE_TYPE_UINT`|Une valeur indigène de 16 bits non signée integer.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Obsolète.<br /><br /> Utilisez NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|COM Interop.|  
|`NATIVE_TYPE_ANSIBSTR`|COM Interop.|  
|`NATIVE_TYPE_TBSTR`|COM Interop.<br /><br /> Sélectionnez BSTR ou ANSIBSTR en fonction de la plate-forme.|  
|`NATIVE_TYPE_VARIANTBOOL`|Une valeur Boolean 2-byte, où TRUE est -1 et FALSE est zéro.|  
|`NATIVE_TYPE_FUNC`|Pointeur de fonction.|  
|`NATIVE_TYPE_ASANY`|Une référence à n’importe quel type natif.|  
|`NATIVE_TYPE_ARRAY`|Une référence à un tableau avec des membres d’un type non spécifié.|  
|`NATIVE_TYPE_LPSTRUCT`|Un pointeur d’intégrerie 32 bits à une structure.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Un type natif de marshaler personnalisé.<br /><br /> Il doit être suivi d’une série du format suivant : « Nom de type autochtone/0Custom marshaler type nom/0Le cookie/0optional cookie/0 » ou « Nom de type marécage/0Optional cookie/0 »|  
|`NATIVE_TYPE_ERROR`|COM Interop.<br /><br /> Avec ELEMENT_TYPE_I4 ce type de cartes à VT_HRESULT.|  
|`NATIVE_TYPE_IINSPECTABLE`|Un `IInspectable` type natif.|  
|`NATIVE_TYPE_HSTRING`|Un `HString`natif .|  
|`NATIVE_TYPE_MAX`|Valeur non valide.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** CorHdr.h  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
