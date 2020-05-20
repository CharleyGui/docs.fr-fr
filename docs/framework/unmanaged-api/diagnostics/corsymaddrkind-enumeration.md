---
title: CorSymAddrKind, énumération
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: 5991b0abaedabe2337cd754c7bd19f96c5e9b685
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420615"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind, énumération
Indique le type d’adresse mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|Indique une variable locale MSIL (Microsoft Intermediate Language) ou un index de paramètre.|  
|`ADDR_NATIVE_RVA`|Indique une adresse virtuelle relative dans un module.|  
|`ADDR_NATIVE_REGISTER`|Indique un registre de l’UC.|  
|`ADDR_NATIVE_REGREL`|Indique que la première adresse est un registre et que la deuxième adresse est un décalage.|  
|`ADDR_NATIVE_OFFSET`|Indique un offset à partir d’une adresse de base.|  
|`ADDR_NATIVE_REGREG`|Indique que la première adresse est la partie basse d’un registre et que la deuxième adresse est la partie haute.|  
|`ADDR_NATIVE_REGSTK`|Indique que la première adresse est la partie basse d’un registre, la deuxième est la partie haute et la troisième est un décalage.|  
|`ADDR_NATIVE_STKREG`|Indique que la première adresse est un registre, la deuxième est un décalage et la troisième la partie haute du Registre.|  
|`ADDR_BITFIELD`|Indique que la première adresse est le début d’un champ et la deuxième adresse la longueur du champ.|  
|`ADDR_NATIVE_ISECTOFFSET`|Indique que la première adresse est la section et que la deuxième adresse est un décalage.|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations du magasin de symboles de diagnostics](diagnostics-symbol-store-enumerations.md)
