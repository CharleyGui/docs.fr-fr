---
title: ISymENCUnmanagedMethod, interface
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: acb8d48ed6314756e2c1a10fff314a303799fb24
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707280"
---
# <a name="isymencunmanagedmethod-interface"></a>ISymENCUnmanagedMethod, interface

Fournit des informations pour la fonctionnalité modifier et continuer.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDocumentsForMethod, méthode](isymencunmanagedmethod-getdocumentsformethod-method.md)|Obtient les documents dans lesquels cette méthode contient des lignes.|  
|[GetDocumentsForMethodCount, méthode](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|Obtient le nombre de documents dans lesquels cette méthode contient des lignes.|  
|[GetFileNameFromOffset, méthode](isymencunmanagedmethod-getfilenamefromoffset-method.md)|Obtient le nom de fichier pour la ligne associée à un offset.|  
|[GetLineFromOffset, méthode](isymencunmanagedmethod-getlinefromoffset-method.md)|Obtient les informations de ligne associées à un offset.|  
|[GetSourceExtentInDocument, méthode](isymencunmanagedmethod-getsourceextentindocument-method.md)|Obtient la ligne de début la plus petite et la ligne de fin la plus grande pour la méthode dans un document spécifique.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
