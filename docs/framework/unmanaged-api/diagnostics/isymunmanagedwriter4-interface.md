---
title: ISymUnmanagedWriter4, interface
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: c2b57897e4f0e8b23337302f344065d79677e0c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725805"
---
# <a name="isymunmanagedwriter4-interface"></a>ISymUnmanagedWriter4, interface

Interface Isymunmanagedwriter4,.  
  
## <a name="syntax"></a>Syntax  
  
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
