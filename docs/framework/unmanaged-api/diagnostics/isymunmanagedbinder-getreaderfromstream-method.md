---
title: ISymUnmanagedBinder::GetReaderFromStream, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
ms.openlocfilehash: 351bb2a1eb03684a0498fba35270e1bda44a93c0
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441745"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a>ISymUnmanagedBinder::GetReaderFromStream, méthode
À partir d’une interface de métadonnées et d’un flux de données qui contient le magasin de symboles, retourne la structure [ISymUnmanagedReader](isymunmanagedreader-interface.md) appropriée qui lira les symboles de débogage du magasin de symboles donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  
 `importer`  
 dans Pointeur vers l’interface d’importation de métadonnées.  
  
 `pstream`  
 dans Pointeur vers le flux de contenu qui contient le magasin de symboles.  
  
 `pRetVal`  
 à Pointeur qui a pour valeur l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retournée.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedBinder, interface](isymunmanagedbinder-interface.md)
