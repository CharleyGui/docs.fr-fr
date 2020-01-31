---
title: ICorDebugArrayValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: 0944f3379c18cba56ab65fe40a5b94a64d8a8991
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778200"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue, interface

Sous-classe de ICorDebugHeapValue qui représente un tableau unidimensionnel ou multidimensionnel.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetBaseIndicies, méthode](icordebugarrayvalue-getbaseindicies-method.md)|Obtient l’index de base de chaque dimension du tableau.|  
|[GetCount, méthode](icordebugarrayvalue-getcount-method.md)|Obtient le nombre total d’éléments dans le tableau.|  
|[GetDimensions, méthode](icordebugarrayvalue-getdimensions-method.md)|Obtient les dimensions du tableau.|  
|[GetElement, méthode](icordebugarrayvalue-getelement-method.md)|Obtient une valeur représentant l’élément donné dans le tableau.|  
|[GetElementAtPosition, méthode](icordebugarrayvalue-getelementatposition-method.md)|Obtient l’élément à la position donnée, en traitant le tableau comme un tableau unidimensionnel de base zéro.|  
|[GetElementType, méthode](icordebugarrayvalue-getelementtype-method.md)|Obtient le type simple des éléments dans le tableau.|  
|[GetRank, méthode](icordebugarrayvalue-getrank-method.md)|Obtient le nombre de dimensions dans le tableau.|  
|[HasBaseIndicies, méthode](icordebugarrayvalue-hasbaseindicies-method.md)|Détermine si le tableau a des index de base.|  
  
## <a name="remarks"></a>Notes  
 `ICorDebugArrayValue` prend en charge les tableaux unidimensionnels et multidimensionnels.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
