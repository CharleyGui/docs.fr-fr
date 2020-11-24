---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: 5298dd0f53693d96b748f6c839660838fdfad4ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689548"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>ISymUnmanagedReader::GetMethodsFromDocumentPosition, méthode

Retourne un tableau de méthodes, chacune contenant le point d’arrêt à la position donnée dans un document.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a>Paramètres  

 `document`  
 dans Document spécifié.  
  
 `line`  
 dans Ligne du document spécifié.  
  
 `column`  
 dans Colonne du document spécifié.  
  
 `cMethod`  
 [in] Taille du tableau `pRetVal`.  
  
 `pcMethod`  
 à Pointeur vers une variable qui reçoit le nombre d’éléments retournés dans le `pRetVal` tableau.  
  
 `pRetVal`  
 à Tableau de pointeurs, chacun pointant vers un objet [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) qui représente une méthode contenant le point d’arrêt.  
  
## <a name="return-value"></a>Valeur renvoyée  

 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedReader, interface](isymunmanagedreader-interface.md)
