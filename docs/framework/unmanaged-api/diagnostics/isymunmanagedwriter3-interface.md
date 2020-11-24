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
ms.openlocfilehash: dfc2e39a6a39e7386bd7358d422d5c6978ec42ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683288"
---
# <a name="isymunmanagedwriter3-interface"></a>ISymUnmanagedWriter3, interface

Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables. Cette interface étend l’interface [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Commit, méthode](isymunmanagedwriter3-commit-method.md)|Valide les modifications écrites jusqu’à présent dans le flux.|  
|[OpenMethod2, méthode](isymunmanagedwriter3-openmethod2-method.md)|Ouvre une méthode et fournit son décalage de section réel dans l’image.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter2, interface](isymunmanagedwriter2-interface.md)
