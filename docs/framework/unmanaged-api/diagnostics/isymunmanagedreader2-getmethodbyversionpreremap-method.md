---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
ms.openlocfilehash: b12ecfdaf7c90589ce2e96b39f7437444cb91b09
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615421"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a>ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode
Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version modifier & continuer. Les numéros de version commencent à 1 et sont incrémentés chaque fois que la méthode est modifiée à la suite d’une opération modifier & continuer.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  
 `token`  
 dans Jeton de métadonnées de la méthode.  
  
 `version`  
 dans Version de la méthode.  
  
 `pRetVal`  
 à Pointeur vers l’interface [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) retournée.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl. CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedReader2, interface](isymunmanagedreader2-interface.md)
