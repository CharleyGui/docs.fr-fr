---
title: ISymUnmanagedSymbolSearchInfo, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: 95ad3cbea4269173f22e662d15772ff97f7ee900
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705447"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a>ISymUnmanagedSymbolSearchInfo, interface

Fournit des méthodes qui obtiennent des informations sur le chemin de recherche. Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetHRESULT, méthode](isymunmanagedsymbolsearchinfo-gethresult-method.md)|Obtient le HRESULT.|  
|[GetSearchPath, méthode](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|Obtient le chemin de recherche.|  
|[GetSearchPathLength, méthode](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|Obtient la longueur du chemin d’accès de recherche.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
