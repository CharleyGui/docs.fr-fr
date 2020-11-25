---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan, méthode
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: e4b09e6d89b3ba8ba3bf7e149d31a14a74b945b5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723933"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a>ISymUnmanagedWriter5::MapTokenToSourceSpan, méthode

Mappe le jeton de métadonnées donné à l’étendue de ligne source donnée dans le fichier source spécifié.  
  
 Doit être appelé entre les appels à la [méthode openmaptokenstosourcespans,](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) et à la [méthode closemaptokenstosourcespans,](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne `HRESULT`.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedWriter5, interface](isymunmanagedwriter5-interface.md)
