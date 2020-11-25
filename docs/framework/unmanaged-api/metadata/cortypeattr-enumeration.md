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
ms.openlocfilehash: 50ce4e5e6125eae493bb62032d5c6bd8887c1afb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699090"
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
|`tdVisibilityMask`|Utilisé pour les informations de visibilité du type.|  
|`tdNotPublic`|Spécifie que le type n’est pas dans la portée publique.|  
|`tdPublic`|Spécifie que le type est dans une portée publique.|  
|`tdNestedPublic`|Spécifie que le type est imbriqué avec une visibilité publique.|  
|`tdNestedPrivate`|Spécifie que le type est imbriqué avec une visibilité privée.|  
|`tdNestedFamily`|Spécifie que le type est imbriqué avec la visibilité de la famille.|  
|`tdNestedAssembly`|Spécifie que le type est imbriqué avec la visibilité de l’assembly.|  
|`tdNestedFamANDAssem`|Spécifie que le type est imbriqué avec la visibilité de la famille et de l’assembly.|  
|`tdNestedFamORAssem`|Spécifie que le type est imbriqué avec une visibilité Family ou assembly.|  
|`tdLayoutMask`|Obtient des informations de disposition pour le type.|  
|`tdAutoLayout`|Spécifie que les champs de ce type sont disposés automatiquement.|  
|`tdSequentialLayout`|Spécifie que les champs de ce type sont disposés de manière séquentielle.|  
|`tdExplicitLayout`|Spécifie que la disposition des champs est fournie explicitement.|  
|`tdClassSemanticsMask`|Obtient des informations sémantiques sur le type.|  
|`tdClass`|Spécifie que le type est une classe.|  
|`tdInterface`|Spécifie que le type est une interface.|  
|`tdAbstract`|Spécifie que le type est abstrait.|  
|`tdSealed`|Spécifie que le type ne peut pas être étendu.|  
|`tdSpecialName`|Spécifie que le nom de la classe est spécial. Son nom décrit comment.|  
|`tdImport`|Spécifie que le type est importé.|  
|`tdSerializable`|Spécifie que le type est sérialisable.|  
|`tdWindowsRuntime`|Spécifie que ce type est un type de Windows Runtime.|  
|`tdStringFormatMask`|Obtient des informations sur la façon dont les chaînes sont encodées et mises en forme.|  
|`tdAnsiClass`|Spécifie que ce type interprète un LPTSTR comme ANSI.|  
|`tdUnicodeClass`|Spécifie que ce type interprète un LPTSTR comme Unicode.|  
|`tdAutoClass`|Spécifie que ce type interprète un LPTSTR automatiquement.|  
|`tdCustomFormatClass`|Spécifie que le type a un encodage non standard, comme spécifié par `CustomFormatMask` .|  
|`tdCustomFormatMask`|Utilisez ce masque pour obtenir des informations d’encodage non standard pour une interopérabilité native. La signification des valeurs de ces deux bits n’est pas spécifiée.|  
|`tdBeforeFieldInit`|Spécifie que le type doit être initialisé avant la première tentative d’accès à un champ statique.|  
|`tdForwarder`|Spécifie que le type est exporté et un redirecteur de type.|  
|`tdReservedMask`|Cet indicateur et les indicateurs ci-dessous sont utilisés en interne par le common language runtime.|  
|`tdRTSpecialName`|Spécifie que le common language runtime doit vérifier l’encodage du nom.|  
|`tdHasSecurity`|Spécifie que la sécurité est associée au type.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
