---
title: ISymUnmanagedWriter4, interface
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: eaf2e8e60d9812ab6a31fb3b9050cbaae0f1a9d7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609467"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4, interface
Interface Isymunmanagedwriter4,.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a>Méthodes  
 Cette interface contient les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDebugInfoWithPadding, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Fonctionne de la même façon que la [méthode GetDebugInfo](isymunmanagedwriter-getdebuginfo-method.md) , sauf que la chaîne du chemin d’accès est complétée par des zéros après le caractère null de fin pour que les données de la chaîne soient de taille fixe `MAX_PATH` . Le remplissage n’est fourni que si la longueur de la chaîne du chemin d’accès est inférieure à `MAX_PATH` .<br /><br /> Cela facilite l’écriture d’outils qui différencient les fichiers PE.|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3, interface](isymunmanagedwriter3-interface.md)
