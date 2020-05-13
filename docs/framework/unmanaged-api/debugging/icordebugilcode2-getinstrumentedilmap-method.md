---
title: ICorDebugILCode2::GetInstrumentedILMap, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: c6fdb7040620bb7a5b6aea6e0dc41e08d6f346d0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210356"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>ICorDebugILCode2::GetInstrumentedILMap, méthode
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Retourne un mappage des décalages du langage intermédiaire instrumenté par le profileur avec les décalages du langage intermédiaire de la méthode d'origine pour cette instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 cMap  
 [en entrée] La capacité de stockage du tableau `map`. Pour plus d'informations, consultez la section Remarques.  
  
 pcMap  
 [en sortie] Le nombre de valeurs COR_IL_MAP écrites dans le tableau du mappage.  
  
 map  
 [en sortie] Un tableau de valeurs COR_IL_MAP qui fournissent des informations sur les mappages du langage intermédiaire instrumenté par le profileur avec le langage intermédiaire de la méthode d'origine.  
  
## <a name="remarks"></a>Remarks  
 Si le profileur définit le mappage en appelant la méthode [ICorProfilerInfo :: SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , le débogueur peut appeler cette méthode pour récupérer le mappage et pour utiliser le mappage en interne lors du calcul des offsets de langage intermédiaire pour les traces de la pile et les durées de vie des variables.  
  
 Si `cMap` a la valeur 0 et que `pcMap` est non**null**, `pcMap` a pour valeur le nombre de valeurs de COR_IL_MAP disponibles. Si `cMap` est différent de zéro, il représente la capacité de stockage du tableau `map`. Lorsque la méthode est retournée, `map` contient un maximum d' `cMap` éléments et `pcMap` est défini sur le nombre de valeurs COR_IL_MAP effectivement écrites dans le `map` tableau.  
  
 Si le langage intermédiaire n'a pas été instrumenté ou si le mappage n'a pas été fourni par le profileur, cette méthode retourne `S_OK` et définit `pcMap` à 0.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo::SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [ICorDebugILCode2, interface](icordebugilcode2-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
