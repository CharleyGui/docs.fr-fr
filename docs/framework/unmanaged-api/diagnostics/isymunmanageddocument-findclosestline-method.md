---
title: ISymUnmanagedDocument::FindClosestLine, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
ms.openlocfilehash: 9e6134d39096c4ab157aa545646d83339f92a0b8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441030"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a>ISymUnmanagedDocument::FindClosestLine, méthode
Retourne la ligne la plus proche qui est un point de séquence, en fonction d’une ligne dans ce document qui peut être ou non un point de séquence.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a>Paramètres  
 `line`  
 dans Ligne dans ce document.  
  
 `pRetVal`  
 à Pointeur vers une variable qui reçoit la ligne.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode est réussie ; Sinon, un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedDocument, interface](isymunmanageddocument-interface.md)
