---
title: ISymUnmanagedWriter3, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: 006045ce101884119f676e4f6324815eb21a10a4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614654"
---
# <a name="isymunmanagedwriter3-interface"></a>ISymUnmanagedWriter3, interface
Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables. Cette interface étend l’interface [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Commit, méthode](isymunmanagedwriter3-commit-method.md)|Valide les modifications écrites jusqu’à présent dans le flux.|  
|[OpenMethod2, méthode](isymunmanagedwriter3-openmethod2-method.md)|Ouvre une méthode et fournit son décalage de section réel dans l’image.|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter2, interface](isymunmanagedwriter2-interface.md)
