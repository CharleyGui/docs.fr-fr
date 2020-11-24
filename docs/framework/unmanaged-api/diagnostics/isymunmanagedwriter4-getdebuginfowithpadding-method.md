---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding, méthode
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 4ac2cccfb17d82d8c62ad7db89161aa794825ae5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678275"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>ISymUnmanagedWriter4::GetDebugInfoWithPadding, méthode

Fonctionne de la même façon que la [méthode GetDebugInfo](isymunmanagedwriter-getdebuginfo-method.md) , sauf que la chaîne du chemin d’accès est complétée par des zéros après le caractère null de fin pour que les données de la chaîne soient de taille fixe `MAX_PATH` . Le remplissage n’est fourni que si la longueur de la chaîne du chemin d’accès est inférieure à `MAX_PATH` .  
  
 Cela facilite l’écriture d’outils qui différencient les fichiers PE.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne `HRESULT`.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter4, interface](isymunmanagedwriter4-interface.md)
