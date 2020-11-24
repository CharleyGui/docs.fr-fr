---
title: ICorProfilerInfo::BeginInprocDebugging, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: 3f56c3faa10eb05896936a37b0094797b0b6e2b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669170"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging, méthode

Initialise la prise en charge du débogage en cours de processus. Cette méthode est obsolète dans la version 2,0 de .NET Framework.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a>Paramètres  

 `fThisThreadOnly`  
 dans Affectez à cette valeur la valeur pour `true` initialiser la prise en charge du débogage pour le thread actuel uniquement ; affectez-lui la valeur `false` pour initialiser la prise en charge du débogage pour tous les threads.  
  
 `pdwProfilerContext`  
 à Pointeur vers une valeur retournée qui identifie la session de débogage.  
  
## <a name="remarks"></a>Remarques  

 Les services de débogage du CLR ont pris en charge le débogage de processus limité dans le .NET Framework versions 1,0 et 1,1. Le débogage en cours de processus permettait à un profileur d’utiliser les parties d’inspection de l’API de débogage. Toutefois, en raison des commentaires des clients, le débogage en cours de processus a été supprimé de la .NET Framework dans la version 2,0 et remplacé par un ensemble de fonctionnalités qui est plus en ligne avec l’API de profilage.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Version de .NET Framework :** 1,0  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
