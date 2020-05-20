---
title: ISymUnmanagedBinder3::GetReaderFromCallback, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
ms.openlocfilehash: 4a23e9aa259f430c0d0579657952fc6aba4c307c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441654"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a>ISymUnmanagedBinder3::GetReaderFromCallback, méthode
Permet à l’utilisateur d’implémenter ou de fournir via le rappel d’un `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` pour obtenir les informations du répertoire de débogage à partir de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  
 `importer`  
 dans Pointeur vers l’interface d’importation de métadonnées.  
  
 `fileName`  
 dans Pointeur vers le nom de fichier.  
  
 `searchPath`  
 dans Pointeur vers le chemin de recherche.  
  
 `searchPolicy`  
 dans Valeur de l’énumération [CorSymSearchPolicyAttributes,](corsymsearchpolicyattributes-enumeration.md) qui spécifie la stratégie à utiliser lors de la recherche d’un lecteur de symboles.  
  
 `callback`  
 dans Pointeur vers la fonction de rappel.  
  
 `pRetVal`  
 à Pointeur qui a pour valeur l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retournée.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedBinder3, interface](isymunmanagedbinder3-interface.md)
