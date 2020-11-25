---
title: ISymUnmanagedScope, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
ms.openlocfilehash: 9256342ad3a91e6770d6fd19d9d2f94fab267d3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725883"
---
# <a name="isymunmanagedscope-interface"></a>ISymUnmanagedScope, interface

Représente une portée lexicale dans une méthode.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetChildren, méthode](isymunmanagedscope-getchildren-method.md)|Obtient les enfants de cette portée.|  
|[GetEndOffset, méthode](isymunmanagedscope-getendoffset-method.md)|Obtient l’offset de fin pour cette portée.|  
|[GetLocalCount, méthode](isymunmanagedscope-getlocalcount-method.md)|Obtient le nombre de variables locales définies dans cette portée.|  
|[GetLocals, méthode](isymunmanagedscope-getlocals-method.md)|Obtient les variables locales définies dans cette portée.|  
|[GetMethod, méthode](isymunmanagedscope-getmethod-method.md)|Obtient la méthode qui contient cette portée.|  
|[GetNamespaces, méthode](isymunmanagedscope-getnamespaces-method.md)|Obtient les espaces de noms utilisés dans cette portée.|  
|[GetParent, méthode](isymunmanagedscope-getparent-method.md)|Obtient la portée parente de cette portée.|  
|[GetStartOffset, méthode](isymunmanagedscope-getstartoffset-method.md)|Obtient le décalage de début pour cette portée.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope2, interface](isymunmanagedscope2-interface.md)
