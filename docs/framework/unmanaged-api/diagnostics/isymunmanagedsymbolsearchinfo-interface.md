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
ms.openlocfilehash: 308c501e17446719067d2dc0580d698c1770bf53
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610663"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a>ISymUnmanagedSymbolSearchInfo, interface
Fournit des méthodes qui obtiennent des informations sur le chemin de recherche. Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetHRESULT, méthode](isymunmanagedsymbolsearchinfo-gethresult-method.md)|Obtient le HRESULT.|  
|[GetSearchPath, méthode](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|Obtient le chemin de recherche.|  
|[GetSearchPathLength, méthode](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|Obtient la longueur du chemin d’accès de recherche.|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
