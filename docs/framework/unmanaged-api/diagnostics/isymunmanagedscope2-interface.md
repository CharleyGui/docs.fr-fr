---
title: ISymUnmanagedScope2, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: 886ba693183a6b99eb03635e95a9661d105de40e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610858"
---
# <a name="isymunmanagedscope2-interface"></a>ISymUnmanagedScope2, interface
Représente une portée lexicale dans une méthode. Cette interface étend l’interface [ISymUnmanagedScope](isymunmanagedscope-interface.md) avec des méthodes qui obtiennent des informations sur les constantes définies dans l’étendue.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetConstantCount, méthode](isymunmanagedscope2-getconstantcount-method.md)|Obtient le nombre des constantes définies dans cette portée.|  
|[GetConstants, méthode](isymunmanagedscope2-getconstants-method.md)|Obtient les constantes locales définies dans cette portée.|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope, interface](isymunmanagedscope-interface.md)
