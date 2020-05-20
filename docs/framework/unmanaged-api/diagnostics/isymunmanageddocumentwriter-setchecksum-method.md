---
title: ISymUnmanagedDocumentWriter::SetCheckSum, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
ms.openlocfilehash: 06a331e24622e0a155d974ca869818a6532baa1f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615538"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a>ISymUnmanagedDocumentWriter::SetCheckSum, méthode
Définit les informations de la somme de contrôle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `algorithmId`  
 dans GUID qui représente l’identificateur d’algorithme.  
  
 `checkSumSize`  
 dans `ULONG32`Qui indique la taille, en octets, de la `checkSum` mémoire tampon.  
  
 `checkSum`  
 dans Mémoire tampon qui stocke les informations de somme de contrôle.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedDocumentWriter, interface](isymunmanageddocumentwriter-interface.md)
