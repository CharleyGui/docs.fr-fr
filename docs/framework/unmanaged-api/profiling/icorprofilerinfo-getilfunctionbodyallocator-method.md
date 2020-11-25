---
title: ICorProfilerInfo::GetILFunctionBodyAllocator, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
ms.openlocfilehash: b18de87cf89985e0f7ec11edf58b43d67720251c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718018"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator, méthode

Obtient une interface qui fournit une méthode pour allouer de la mémoire à utiliser pour échanger le corps d’une méthode dans le code MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a>Paramètres  

 `moduleId`  
 dans ID du module dans lequel la méthode réside.  
  
 `ppMalloc`  
 à Pointeur vers une interface [IMethodMalloc](imethodmalloc-interface.md) qui fournit une méthode pour allouer la mémoire.  
  
## <a name="remarks"></a>Remarques  

 Un corps de méthode dans le code MSIL doit se trouver sous la forme d’une adresse virtuelle relative (RVA) relative au module chargé, ce qui signifie qu’il suit le module dans un délai de 4 Go. Pour faciliter le remplacement du corps d’une méthode par un outil, la `GetILFunctionBodyAllocator` méthode garantit que la mémoire est allouée dans cette plage.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
