---
title: ILCodeKind, énumération
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: 0586b9e184a0958b978837601db002e035881cbc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421031"
---
# <a name="ilcodekind-enumeration"></a>ILCodeKind, énumération
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Fournit des valeurs qui spécifient si le débogueur peut accéder aux variables locales ou au code ajoutés dans l'instrumentation ReJIT du profileur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a>Membres  
  
|Nom de membre|Description|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|Le débogueur n'a pas accès aux informations de l'instrumentation ReJIT.|  
|`ILCODE_REJIT_IL`|Le débogueur a accès aux informations de l'instrumentation ReJIT.|  
  
## <a name="remarks"></a>Notes  
 Un membre de l' `ILCodeKind` énumération peut être passé aux méthodes [Enumeratelocalvariablesex,](icordebugilframe4-enumeratelocalvariablesex-method.md) et [getlocalvariableex,](icordebugilframe4-getlocalvariableex-method.md) pour déterminer si le débogueur peut accéder aux variables ajoutées dans l’instrumentation ReJIT du profileur, et à la méthode [getcodeex,](icordebugilframe4-getcodeex-method.md) pour déterminer si le débogueur peut accéder au langage intermédiaire instrumenté.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
- [ICorDebugILFrame4, interface](icordebugilframe4-interface.md)
- [ReJIT : Guide pratique](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
