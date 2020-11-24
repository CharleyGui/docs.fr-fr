---
title: ISymUnmanagedWriter5::OpenMapTokensToSourceSpans, méthode
ms.date: 03/30/2017
ms.assetid: 93ad2517-b0dc-464c-8688-a58a30eda18d
ms.openlocfilehash: 95976e2f331252c88eab717e184abc284842e3b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683262"
---
# <a name="isymunmanagedwriter5openmaptokenstosourcespans-method"></a>ISymUnmanagedWriter5::OpenMapTokensToSourceSpans, méthode

Ouvrez une section de données personnalisées spéciale pour émettre des informations de mappage de jeton-à-source dans. L’ouverture de cette section quand une méthode est déjà ouverte, ou vice versa, est une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT OpenMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a>Valeur de retour  

 Retourne `HRESULT`.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter5, interface](isymunmanagedwriter5-interface.md)
