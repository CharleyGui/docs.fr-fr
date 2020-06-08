---
title: ISymUnmanagedWriter5, interface
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: d9204457b71b670e1c96ed228ad11116bdf41fe6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493576"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5, interface
Interface ISymUnmanagedWriter5.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>Méthodes  
 Cette interface contient les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans, méthode](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Fermez la section de données personnalisées spéciale pour les informations de mappage de l’étendue Token-to-source. Une fois fermé, aucune autre information de mappage ne peut être ajoutée.|  
|[MapTokenToSourceSpan, méthode](isymunmanagedwriter5-maptokentosourcespan-method.md)|Mappe le jeton de métadonnées donné à l’étendue de ligne source donnée dans le fichier source spécifié.<br /><br /> Doit être appelé entre les appels à la [méthode openmaptokenstosourcespans,](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) et à la [méthode closemaptokenstosourcespans,](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).|  
|[OpenMapTokensToSourceSpans, méthode](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Ouvrez une section de données personnalisées spéciale pour émettre des informations de mappage de jeton-à-source dans. L’ouverture de cette section quand une méthode est déjà ouverte, ou vice versa, est une erreur.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4, interface](isymunmanagedwriter4-interface.md)
