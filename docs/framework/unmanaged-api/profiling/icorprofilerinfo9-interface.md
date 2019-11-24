---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 74031fd822550f8a0752d02ce0c2d89b2f5ae546
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444953"
---
# <a name="icorprofilerinfo9-interface"></a>Interface ICorProfilerInfo9

A subclass of [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.  

## <a name="methods"></a>Méthodes  

| Méthode|Description|  
| ------------|-----------------|  
|[GetNativeCodeStartAddresses Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist. |
|[GetILToNativeMapping3 Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| Given the native code start address, returns the native to IL mapping information for this jitted version of the code. |
|[GetCodeInfo4 Method](icorprofilerinfo9-getcodeinfo4-method.md)| Given the native code start address, returns the blocks of virtual memory that store this code. |

## <a name="requirements"></a>spécifications  
**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**En-tête :** CorProf.idl, CorProf.h  
**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
