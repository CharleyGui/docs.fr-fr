---
title: IMethodMalloc::Alloc, méthode
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: af881d23ff77f05dadbbc745b973979e35ebe9f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447571"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc, méthode

Tente d’allouer une quantité de mémoire spécifiée pour un nouveau corps de fonction MSIL (Microsoft Intermediate Language).

## <a name="syntax"></a>Syntaxe

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>Paramètres

`cb`\
dans Nombre d’octets à allouer pour le corps de la méthode.

## <a name="remarks"></a>Notes

 La mémoire allouée commence à une adresse supérieure à l’adresse de base du module associé à cet allocateur. En d’autres termes, chaque allocateur est créé pour un module particulier et tente d’allouer de la mémoire à un décalage positif par rapport à son adresse de base. Si `Alloc` ne parvient pas à allouer le nombre d’octets demandé à une adresse supérieure à l’adresse de base du module, il retourne E_OUTOFMEMORY, quelle que soit la quantité réelle d’espace mémoire disponible.

 La méthode `Alloc` doit être utilisée conjointement avec la méthode [ICorProfilerInfo :: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) .

## <a name="requirements"></a>Configuration requise
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

 **En-tête :** CorProf.idl, CorProf.h

 **Bibliothèque :** CorGuids.lib

 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [IMethodMalloc, interface](imethodmalloc-interface.md)
