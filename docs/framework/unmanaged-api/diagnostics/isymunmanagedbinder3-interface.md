---
title: ISymUnmanagedBinder3, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: 5a26de2a8f5439b7c81560927c991d449e57b76c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441589"
---
# <a name="isymunmanagedbinder3-interface"></a>ISymUnmanagedBinder3, interface
Étend l’interface de classeur de symboles. Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente l' `ISymUnmanagedBinder` interface.  
  
> [!IMPORTANT]
> L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetReaderFromCallback, méthode](isymunmanagedbinder3-getreaderfromcallback-method.md)|Permet à l’utilisateur d’implémenter ou de fournir via le rappel d’un `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` pour obtenir les informations du répertoire de débogage à partir de la mémoire|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder, interface](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder2, interface](isymunmanagedbinder2-interface.md)
