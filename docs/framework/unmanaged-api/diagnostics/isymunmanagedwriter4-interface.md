---
title: ISymUnmanagedWriter4, interface
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: 21d6520aae1367368973da1692f6bca3aeb2c129
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493654"
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
|[GetDebugInfoWithPadding, méthode](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|Fonctionne de la même façon que la [méthode GetDebugInfo](isymunmanagedwriter-getdebuginfo-method.md) , sauf que la chaîne du chemin d’accès est complétée par des zéros après le caractère null de fin pour que les données de la chaîne soient de taille fixe `MAX_PATH` . Le remplissage n’est fourni que si la longueur de la chaîne du chemin d’accès est inférieure à `MAX_PATH` .<br /><br /> Cela facilite l’écriture d’outils qui différencient les fichiers PE.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter3, interface](isymunmanagedwriter3-interface.md)
