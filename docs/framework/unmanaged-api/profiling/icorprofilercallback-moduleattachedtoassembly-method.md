---
title: ICorProfilerCallback::ModuleAttachedToAssembly, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
ms.openlocfilehash: bcf5c5c9044a30fc8259dbc54bad8f3141f0f926
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733111"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly, méthode

Notifie le profileur qu’un module est attaché à son assembly parent.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a>Paramètres  

 `moduleId`  
 dans ID du module qui est attaché.  
  
 `AssemblyId`  
 dans ID de l’assembly parent auquel le module est attaché.  
  
## <a name="remarks"></a>Remarques  

 Un module peut être chargé par le biais d’une table d’adresses d’importation (IAT), d’un appel à `LoadLibrary` ou par le biais d’une référence de métadonnées. Par conséquent, le chargeur common language runtime (CLR) a plusieurs chemins de code pour déterminer l’assembly dans lequel un module vit. Par conséquent, il est possible qu’après l’appel de [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) , le module ne connaisse pas l’assembly dans lequel il se trouve et l’obtention de l’ID d’assembly parent n’est pas possible. La `ModuleAttachedToAssembly` méthode est appelée quand le module est attaché à son assembly parent et que son ID d’assembly parent peut être obtenu.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
