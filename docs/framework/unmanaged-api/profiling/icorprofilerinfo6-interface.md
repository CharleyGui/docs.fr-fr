---
title: ICorProfilerInfo6, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: 80ac17a96e5c1c8c32cfc336da6c2be30eaf80fd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868367"
---
# <a name="icorprofilerinfo6-interface"></a>ICorProfilerInfo6, interface
[Pris en charge dans le .NET Framework 4,6 et versions ultérieures]  
  
 Sous-classe de [ICorProfilerInfo5](icorprofilerinfo5-interface.md) qui fournit un énumérateur pour toutes les méthodes définies dans un module Ngen donné et incluse dans une méthode donnée.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, méthode](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|Retourne un énumérateur pour toutes les méthodes qui appartiennent à un module NGen donné et qui sont inline dans le corps d’une méthode donnée.|  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de profilage](profiling-interfaces.md)
