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
ms.openlocfilehash: 95bbb0cc2f223cfa96e1314ed28f46016c81a2fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687695"
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
|`NATIVE_TYPE_BOOLEAN`|Valeur booléenne sur 4 octets, où TRUE est différent de zéro et FALSe est égal à zéro.|  
|`NATIVE_TYPE_I1`|Valeur entière 8 bits signée.|  
|`NATIVE_TYPE_U1`|Valeur entière 8 bits non signée.|  
|`NATIVE_TYPE_I2`|Valeur entière 16 bits signée.|  
|`NATIVE_TYPE_U2`|Valeur entière 16 bits non signée.|  
|`NATIVE_TYPE_I4`|Valeur d’entier 32 bits signé.|  
|`NATIVE_TYPE_U4`|Valeur d'entier 32 bits non signé.|  
|`NATIVE_TYPE_I8`|Valeur entière 64 bits signée.|  
|`NATIVE_TYPE_U8`|Valeur entière 64 bits non signée.|  
|`NATIVE_TYPE_R4`|Valeur numérique à virgule flottante sur 4 octets.|  
|`NATIVE_TYPE_R8`|Valeur numérique à virgule flottante sur 8 octets.|  
|`NATIVE_TYPE_SYSCHAR`|Obsolète.|  
|`NATIVE_TYPE_VARIANT`|Obsolète.|  
|`NATIVE_TYPE_CURRENCY`|Type COM numérique qui correspond au <xref:System.Decimal> type managé.|  
|`NATIVE_TYPE_PTR`|Obsolète.|  
|`NATIVE_TYPE_DECIMAL`|Obsolète.|  
|`NATIVE_TYPE_DATE`|Obsolète.|  
|`NATIVE_TYPE_BSTR`|COM Interop.|  
|`NATIVE_TYPE_LPSTR`|Valeur de chaîne LPSTR.|  
|`NATIVE_TYPE_LPWSTR`|Valeur de chaîne LPWSTR.|  
|`NATIVE_TYPE_LPTSTR`|Valeur de chaîne LPTSTR.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Valeur de chaîne fixe définie par le système.|  
|`NATIVE_TYPE_OBJECTREF`|Obsolète.|  
|`NATIVE_TYPE_IUNKNOWN`|COM Interop.|  
|`NATIVE_TYPE_IDISPATCH`|COM Interop.|  
|`NATIVE_TYPE_STRUCT`|Valeur de structure native.|  
|`NATIVE_TYPE_INTF`|COM Interop.|  
|`NATIVE_TYPE_SAFEARRAY`|COM Interop.|  
|`NATIVE_TYPE_FIXEDARRAY`|Valeur de tableau de longueur fixe.|  
|`NATIVE_TYPE_INT`|Valeur d’entier 16 bits signé natif.|  
|`NATIVE_TYPE_UINT`|Valeur de l’entier non signé 16 bits natif.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Obsolète.<br /><br /> Utilisez NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|COM Interop.|  
|`NATIVE_TYPE_ANSIBSTR`|COM Interop.|  
|`NATIVE_TYPE_TBSTR`|COM Interop.<br /><br /> Sélectionnez BSTR ou ANSIBSTR en fonction de la plateforme.|  
|`NATIVE_TYPE_VARIANTBOOL`|Valeur booléenne sur 2 octets, où TRUE est-1 et FALSe est égal à zéro.|  
|`NATIVE_TYPE_FUNC`|Pointeur de fonction.|  
|`NATIVE_TYPE_ASANY`|Référence à n’importe quel type natif.|  
|`NATIVE_TYPE_ARRAY`|Référence à un tableau avec des membres d’un type non spécifié.|  
|`NATIVE_TYPE_LPSTRUCT`|Pointeur d’entier 32 bits vers une structure.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Type natif de marshaleur personnalisé.<br /><br /> Il doit être suivi d’une chaîne au format suivant : « nom de type natif/nom de type de marshaleur 0Custom/0Optional cookie/0 » ou « {native type GUID}/0Custom nom de type de marshaleur/0Optional cookie/0 »|  
|`NATIVE_TYPE_ERROR`|COM Interop.<br /><br /> Avec ELEMENT_TYPE_I4 ce type est mappé à VT_HRESULT.|  
|`NATIVE_TYPE_IINSPECTABLE`|Type natif `IInspectable` .|  
|`NATIVE_TYPE_HSTRING`|Un natif `HString` .|  
|`NATIVE_TYPE_MAX`|Valeur non valide.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Énumérations de métadonnées](metadata-enumerations.md)
