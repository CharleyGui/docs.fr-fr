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
ms.openlocfilehash: d229b530062d759ab270612fa70b1799acbcadbe
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448071"
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
  
## <a name="remarks"></a>Notes  
 Un module peut être chargé par le biais d’une table d’adresses d’importation (IAT), via un appel à `LoadLibrary`ou par le biais d’une référence de métadonnées. Par conséquent, le chargeur common language runtime (CLR) a plusieurs chemins de code pour déterminer l’assembly dans lequel un module vit. Par conséquent, il est possible qu’après l’appel de [ICorProfilerCallback :: ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) , le module ne connaisse pas l’assembly dans lequel il se trouve et l’obtention de l’ID d’assembly parent n’est pas possible. La méthode `ModuleAttachedToAssembly` est appelée quand le module est attaché à son assembly parent et que son ID d’assembly parent peut être obtenu.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
