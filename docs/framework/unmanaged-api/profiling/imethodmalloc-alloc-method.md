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
ms.openlocfilehash: 58809f12e4dd4419b754caafc3f8b883b8bc5089
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721164"
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

## <a name="remarks"></a>Remarques

 La mémoire allouée commence à une adresse supérieure à l’adresse de base du module associé à cet allocateur. En d’autres termes, chaque allocateur est créé pour un module particulier et tente d’allouer de la mémoire à un décalage positif par rapport à son adresse de base. Si `Alloc` ne parvient pas à allouer le nombre d’octets demandé à une adresse supérieure à l’adresse de base du module, il retourne E_OUTOFMEMORY, quelle que soit la quantité réelle d’espace mémoire disponible.

 La `Alloc` méthode doit être utilisée conjointement avec la méthode [ICorProfilerInfo :: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) .

## <a name="requirements"></a>Configuration requise

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

 **En-tête :** CorProf.idl, CorProf.h

 **Bibliothèque :** CorGuids.lib

 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [IMethodMalloc, interface](imethodmalloc-interface.md)
