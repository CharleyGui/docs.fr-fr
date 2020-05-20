---
title: ISymUnmanagedDocument::GetCheckSum, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 543bd208e5492460435663c32f276472a763f613
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441095"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a>ISymUnmanagedDocument::GetCheckSum, méthode
Obtient la somme de contrôle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cData`  
 dans Longueur de la mémoire tampon fournie par le `data` paramètre.  
  
 `pcData`  
 à Taille et longueur de la somme de contrôle, en octets.  
  
 `data`  
 à Mémoire tampon qui reçoit la somme de contrôle.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedDocument, interface](isymunmanageddocument-interface.md)
