---
title: ICorDebugDataTarget::GetPlatform, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: 3654c94975d16e35d5c3d8e762730d17509a2c6d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788876"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform, méthode
Fournit des informations sur la plateforme, y compris l’architecture du processeur et le système d’exploitation, sur lesquelles le processus cible est en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>Parameters  
 `pTargetPlatform`  
 à Pointeur vers une énumération [CorDebugPlatformEnum](cordebugplatform-enumeration.md) qui décrit la plateforme cible.  
  
## <a name="remarks"></a>Notes  
 La `CorDebugPlatformEnum` valeur de retour de l’énumération est utilisée par l’interface [ICorDebug](icordebug-interface.md) pour déterminer les détails du processus cible, comme sa taille de pointeur, sa disposition d’espace d’adressage, son ensemble de registres, son format d’instruction, sa disposition de contexte et ses conventions d’appel.  
  
 La valeur `pTargetPlatform` peut faire référence à une plateforme qui est émulée pour la cible au lieu de spécifier le matériel réel en cours d’utilisation. Par exemple, un processus qui s’exécute dans l’environnement WOW (Windows on Windows) sur une édition 64 bits du système d’exploitation Windows doit utiliser la valeur `CORDB_PLATFORM_WINDOWS_X86` de l’énumération [CorDebugPlatformEnum](cordebugplatform-enumeration.md) .  
  
 Cette méthode doit être correctement exécutée. En cas d’échec, la plateforme cible est inutilisable. La méthode peut échouer pour les raisons suivantes :  
  
- La plateforme émulée pour la cible est inutilisable.  
  
- Le matériel réel sur la plateforme cible est inutilisable.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugDataTarget, interface](icordebugdatatarget-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
