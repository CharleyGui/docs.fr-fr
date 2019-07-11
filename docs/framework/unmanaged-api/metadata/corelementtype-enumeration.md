---
title: CorElementType, énumération1
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d47e250a35640d15bd494d99442271a070a1dd0a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781901"
---
# <a name="corelementtype-enumeration1"></a>CorElementType, énumération1

Spécifie un common language runtime <xref:System.Type>, un modificateur de type, ou des informations sur un type dans une signature de type de métadonnées.

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
|`ELEMENT_TYPE_VOID`|Un type void.|
|`ELEMENT_TYPE_BOOLEAN`|Un type booléen|
|`ELEMENT_TYPE_CHAR`|Type de caractère.|
|`ELEMENT_TYPE_I1`|Entier signé sur 1 octet.|
|`ELEMENT_TYPE_U1`|Entier non signé sur 1 octet.|
|`ELEMENT_TYPE_I2`|Un entier signé de 2 octets.|
|`ELEMENT_TYPE_U2`|Entier non signé sur 2 octets.|
|`ELEMENT_TYPE_I4`|Un entier signé de 4 octets.|
|`ELEMENT_TYPE_U4`|Entier non signé sur 4 octets.|
|`ELEMENT_TYPE_I8`|Un entier signé de 8 octets.|
|`ELEMENT_TYPE_U8`|Entier non signé sur 8 octets.|
|`ELEMENT_TYPE_R4`|Virgule flottante sur 4 octets.|
|`ELEMENT_TYPE_R8`|Une virgule flottante de 8 octets.|
|`ELEMENT_TYPE_STRING`|Un type System.String.|
|`ELEMENT_TYPE_PTR`|Un modificateur de type pointeur.|
|`ELEMENT_TYPE_BYREF`|Un modificateur de type référence.|
|`ELEMENT_TYPE_VALUETYPE`|Un modificateur de type valeur.|
|`ELEMENT_TYPE_CLASS`|Un modificateur de type classe.|
|`ELEMENT_TYPE_VAR`|Un modificateur de type de variable de classe.|
|`ELEMENT_TYPE_ARRAY`|Un modificateur de type tableau multidimensionnel.|
|`ELEMENT_TYPE_GENERICINST`|Un modificateur de type pour les types génériques.|
|`ELEMENT_TYPE_TYPEDBYREF`|Référence typée.|
|`ELEMENT_TYPE_I`|Taille d’un entier natif.|
|`ELEMENT_TYPE_U`|Taille d’un entier natif non signé.|
|`ELEMENT_TYPE_FNPTR`|Pointeur vers une fonction.|
|`ELEMENT_TYPE_OBJECT`|Un type System.Object.|
|`ELEMENT_TYPE_SZARRAY`|Une seule dimension, zéro modificateur de type tableau de limite inférieure.|
|`ELEMENT_TYPE_MVAR`|Un modificateur de type de variable de méthode.|
|`ELEMENT_TYPE_CMOD_REQD`|Modificateur de langage C requis.|
|`ELEMENT_TYPE_CMOD_OPT`|Un modificateur facultatif de langage C.|
|`ELEMENT_TYPE_INTERNAL`|Utilisé en interne.|
|`ELEMENT_TYPE_MAX`|Type non valide.|
|`ELEMENT_TYPE_MODIFIER`|Utilisé en interne.|
|`ELEMENT_TYPE_SENTINEL`|Un modificateur de type qui est un objet sentinel pour obtenir la liste d’un nombre variable de paramètres.|
|`ELEMENT_TYPE_PINNED`|Utilisé en interne.|

## <a name="remarks"></a>Notes

Les modificateurs de type constituent la base pour représenter des types plus complexes. Un `CorElementType` valeur de modificateur de type est appliqué à la valeur qui suit immédiatement dans la signature de type. La valeur qui suit le `CorElementType` valeur de modificateur de type peut être un `CorElementType` valeur de type simple, un jeton de métadonnées ou une autre valeur, tel que spécifié dans le tableau suivant.

> [!NOTE]
> Tous les nombres (*nombre*, *nombre d’arguments*, *jeton de métadonnées*, *rang*, *nombre*et *lié*) sont stockées sous la forme d’entiers compressés. Consultez [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) sur le site Web ECMA pour plus d’informations.

|Modificateur de type|Format|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR \<un `CorElementType` valeur >|
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF \<un `CorElementType` valeur >|
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE \<un `mdTypeDef` jeton de métadonnées >|
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS \<un `mdTypeDef` jeton de métadonnées >|
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR \<numéro >|
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY \<un `CorElementType` valeur > \<rang > \<count1 > \<bound1 >... \<countN > \<boundN >|
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST \<un `mdTypeDef` jeton de métadonnées > \<nombre d’arguments > \<arg1 >... \<argN >|
|`ELEMENT_TYPE_FNPTR`|ELEMENT_TYPE_FNPTR \<signature complète pour la fonction, y compris la convention d’appel >|
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY \<un `CorElementType` valeur >|
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR \<numéro >|
|`ELEMENT_TYPE_CMOD_REQD`|ELEMENT_TYPE_\<un `mdTypeRef` ou `mdTypeDef` jeton de métadonnées >|
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT \<un `mdTypeRef` ou `mdTypeDef` jeton de métadonnées >|

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorHdr.h

**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
