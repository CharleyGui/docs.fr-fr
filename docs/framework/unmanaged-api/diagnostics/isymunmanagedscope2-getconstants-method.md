---
title: ISymUnmanagedScope2::GetConstants, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: f558d209d13fae93bd3a6f5e0e653afb91371a6a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615330"
---
# <a name="isymunmanagedscope2getconstants-method"></a>ISymUnmanagedScope2::GetConstants, méthode
Obtient les constantes locales définies dans cette portée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cConstants`  
 dans Longueur de la mémoire tampon vers laquelle `pcConstants` pointe le paramètre.  
  
 `pcConstants`  
 à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir les constantes.  
  
 `constants`  
 à Mémoire tampon qui stocke les constantes.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedScope2, interface](isymunmanagedscope2-interface.md)
