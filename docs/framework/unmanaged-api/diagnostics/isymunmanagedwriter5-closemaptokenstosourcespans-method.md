---
title: ISymUnmanagedWriter5::CloseMapTokensToSourceSpans, méthode
ms.date: 03/30/2017
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
ms.openlocfilehash: b57174f9f76b174927b8f1997beac3dd1482583a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725909"
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a>ISymUnmanagedWriter5::CloseMapTokensToSourceSpans, méthode

Fermez la section de données personnalisées spéciale pour les informations de mappage de l’étendue Token-to-source. Une fois fermé, aucune autre information de mappage ne peut être ajoutée.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a>Valeur de retour  

 Retourne `HRESULT`.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter5, interface](isymunmanagedwriter5-interface.md)
