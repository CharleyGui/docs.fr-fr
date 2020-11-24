---
title: ISymUnmanagedWriter2, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: 6feb48b7c78dda64ba372e470b83ffb14f21f2f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683327"
---
# <a name="isymunmanagedwriter2-interface"></a>ISymUnmanagedWriter2, interface

Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables. Cette interface étend l’interface [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DefineConstant2, méthode](isymunmanagedwriter2-defineconstant2-method.md)|Définit un nom pour une valeur de constante.|  
|[DefineGlobalVariable2, méthode](isymunmanagedwriter2-defineglobalvariable2-method.md)|Définit une variable globale unique.|  
|[DefineLocalVariable2, méthode](isymunmanagedwriter2-definelocalvariable2-method.md)|Définit une variable unique dans la portée lexicale actuelle.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
- [ISymUnmanagedWriter3, interface](isymunmanagedwriter3-interface.md)
