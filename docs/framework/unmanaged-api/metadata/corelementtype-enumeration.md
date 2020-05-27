---
title: CorElementType, énumération
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
ms.openlocfilehash: 25fb3278e576ebe4a538379918e868b2e5f87911
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007869"
---
# <a name="corelementtype-enumeration"></a>CorElementType, énumération

Spécifie un common language runtime <xref:System.Type> , un modificateur de type ou des informations sur un type dans une signature de type de métadonnées.

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a>Membres

|Membre|Description|
|------------|-----------------|
|`ELEMENT_TYPE_END`|Utilisé en interne.|
|`ELEMENT_TYPE_VOID`|Type void.|
|`ELEMENT_TYPE_BOOLEAN`|Type booléen|
|`ELEMENT_TYPE_CHAR`|Type de caractère.|
|`ELEMENT_TYPE_I1`|Entier signé sur 1 octet.|
|`ELEMENT_TYPE_U1`|Entier non signé sur 1 octet.|
|`ELEMENT_TYPE_I2`|Entier signé sur 2 octets.|
|`ELEMENT_TYPE_U2`|Entier non signé sur 2 octets.|
|`ELEMENT_TYPE_I4`|Entier signé de 4 octets.|
|`ELEMENT_TYPE_U4`|Entier non signé sur 4 octets.|
|`ELEMENT_TYPE_I8`|Entier signé de 8 octets.|
|`ELEMENT_TYPE_U8`|Entier non signé sur 8 octets.|
|`ELEMENT_TYPE_R4`|Virgule flottante sur 4 octets.|
|`ELEMENT_TYPE_R8`|Virgule flottante sur 8 octets.|
|`ELEMENT_TYPE_STRING`|Type System. String.|
|`ELEMENT_TYPE_PTR`|Modificateur de type pointeur.|
|`ELEMENT_TYPE_BYREF`|Modificateur de type référence.|
|`ELEMENT_TYPE_VALUETYPE`|Modificateur de type valeur.|
|`ELEMENT_TYPE_CLASS`|Modificateur de type de classe.|
|`ELEMENT_TYPE_VAR`|Modificateur de type de variable de classe.|
|`ELEMENT_TYPE_ARRAY`|Modificateur de type tableau multidimensionnel.|
|`ELEMENT_TYPE_GENERICINST`|Modificateur de type pour les types génériques.|
|`ELEMENT_TYPE_TYPEDBYREF`|Référence typée.|
|`ELEMENT_TYPE_I`|Taille d’un entier natif.|
|`ELEMENT_TYPE_U`|Taille d’un entier natif non signé.|
|`ELEMENT_TYPE_FNPTR`|Pointeur vers une fonction.|
|`ELEMENT_TYPE_OBJECT`|Type System. Object.|
|`ELEMENT_TYPE_SZARRAY`|Modificateur de type tableau à liaison inférieure zéro unidimensionnel.|
|`ELEMENT_TYPE_MVAR`|Modificateur de type de variable de méthode.|
|`ELEMENT_TYPE_CMOD_REQD`|Modificateur requis pour le langage C.|
|`ELEMENT_TYPE_CMOD_OPT`|Modificateur facultatif du langage C.|
|`ELEMENT_TYPE_INTERNAL`|Utilisé en interne.|
|`ELEMENT_TYPE_MAX`|Type non valide.|
|`ELEMENT_TYPE_MODIFIER`|Utilisé en interne.|
|`ELEMENT_TYPE_SENTINEL`|Modificateur de type qui est une sentinelle pour une liste d’un nombre variable de paramètres.|
|`ELEMENT_TYPE_PINNED`|Utilisé en interne.|

## <a name="remarks"></a>Remarques

Les modificateurs de type forment la base pour représenter des types plus complexes. Une `CorElementType` valeur de modificateur de type est appliquée à la valeur qui le suit immédiatement dans la signature de type. La valeur qui suit la `CorElementType` valeur du modificateur de type peut être une `CorElementType` valeur de type simple, un jeton de métadonnées ou une autre valeur, comme indiqué dans le tableau suivant.

> [!NOTE]
> Tous les nombres (*nombre*, nombre d' *arguments*, *jeton de métadonnées*, *rang*, *nombre*et *limite*) sont stockés sous forme d’entiers compressés. Pour plus d’informations, consultez [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) sur le site Web ECMA.

|Modificateur de type|Format|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR\<a `CorElementType` value>|
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF\<a `CorElementType` value>|
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE\<an `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS\<an `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR\<number>|
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN>\<boundN>|
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ...\<argN>|
|`ELEMENT_TYPE_FNPTR`|ELEMENT_TYPE_FNPTR\<complete signature for the function, including calling convention>|
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY\<a `CorElementType` value>|
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR\<number>|
|`ELEMENT_TYPE_CMOD_REQD`|ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT\<a `mdTypeRef` or `mdTypeDef` metadata token>|

## <a name="requirements"></a>Spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorHdr. h

**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
