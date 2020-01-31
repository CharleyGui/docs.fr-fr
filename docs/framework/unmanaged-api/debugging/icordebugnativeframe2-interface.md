---
title: ICorDebugNativeFrame2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
ms.openlocfilehash: 22a3f39bc1f9b4e6cad1db4fd0a6480b7c04e8fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792755"
---
# <a name="icordebugnativeframe2-interface"></a>ICorDebugNativeFrame2, interface
Fournit des méthodes qui testent les relations entre frames enfant et parent.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[IsChild, méthode](icordebugnativeframe2-ischild-method.md)|Détermine si le frame actuel est un Frame enfant.|  
|[IsMatchingParentFrame, méthode](icordebugnativeframe2-ismatchingparentframe-method.md)|Détermine si le frame spécifié est le parent du frame actuel.|  
|[GetStackParameterSize, méthode](icordebugnativeframe2-getstackparametersize-method.md)|Retourne la taille cumulée des paramètres sur la pile sur les systèmes d’exploitation x86.|  
  
## <a name="remarks"></a>Notes  
 Cette interface étend logiquement l’interface « ICorDebugNativeFrame ».  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
