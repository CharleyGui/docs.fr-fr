---
title: COR_PRF_CODEGEN_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: 3252e3b33da743c0e146e25f798c0e669aeb74ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718603"
---
# <a name="cor_prf_codegen_flags-enumeration"></a>COR_PRF_CODEGEN_FLAGS, énumération

Définit les indicateurs de génération de code qui peuvent être définis avec la méthode [ICorProfilerFunctionControl :: setcodegenflags,](icorprofilerfunctioncontrol-setcodegenflags-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|Aucune fonction n’est insérée dans le corps de cette fonction. Toutefois, la fonction elle-même peut être inline dans ses appelants.|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|Toutes les optimisations sont désactivées pour le corps de cette fonction. Toutefois, la fonction elle-même peut toujours être inline dans ses appelants.|  
  
## <a name="remarks"></a>Remarques  

 L' `COR_PRF_CODEGEN_FLAGS` énumération est utilisée par la méthode [ICorProfilerFunctionControl :: setcodegenflags,](icorprofilerfunctioncontrol-setcodegenflags-method.md) pour permettre au profileur de contrôler la génération de code pour la fonction recompilée juste-à-temps.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de profilage](profiling-enumerations.md)
