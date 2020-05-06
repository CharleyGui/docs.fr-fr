---
title: CorDebugNGenPolicy, énumération
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: 036d3f12b38c19259fefaba674d0f9025a58d688
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795753"
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy, énumération
Fournit une valeur qui détermine si un débogueur charge les images natives (NGen) depuis le cache d'images natives.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Membres  
  
|Nom de membre|Description|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|Dans une application Windows 8. x Store, l’utilisation d’images du cache d’images natives locales est désactivée. Dans une application de bureau, ce paramètre n’a aucun effet.|  
  
## <a name="remarks"></a>Notes   
 L' `CorDebugNGENPolicy` énumération est utilisée par la méthode [ICorDebugProcess5 :: enablengenpolicy,](icordebugprocess5-enablengenpolicy-method.md) . La désactivation de l’utilisation d’images à partir du cache d’images natives local offre une expérience de débogage cohérente en garantissant que le débogueur charge des images déboguées et compilées juste-à-temps au lieu d’images natives optimisées.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
