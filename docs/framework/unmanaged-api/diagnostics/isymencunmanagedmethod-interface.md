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
ms.openlocfilehash: 54c8c7f5c3ba6b4afd4ff352a8afb947a92e2d61
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441875"
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
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
