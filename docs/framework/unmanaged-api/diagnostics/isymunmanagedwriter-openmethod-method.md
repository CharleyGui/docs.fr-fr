---
title: ISymUnmanagedWriter::OpenMethod, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: deb3a28ffb73754b4c03496a6a72325418f1a4fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722906"
---
# <a name="isymunmanagedwriteropenmethod-method"></a>ISymUnmanagedWriter::OpenMethod, méthode

Ouvre une méthode dans laquelle les informations de symboles sont émises. La méthode donnée devient la méthode actuelle pour les appels pour définir des points de séquence, des paramètres et des étendues lexicales. Il existe une portée lexicale implicite autour de la totalité de la méthode. La réouverture d’une méthode précédemment fermée efface tous les symboles définis précédemment pour cette méthode. Il ne peut y avoir qu’une seule méthode ouverte à la fois.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a>Paramètres  

 `method`  
 dans Jeton de métadonnées de la méthode à ouvrir.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)
- [CloseMethod, méthode](isymunmanagedwriter-closemethod-method.md)
- [OpenMethod2, méthode](isymunmanagedwriter3-openmethod2-method.md)
