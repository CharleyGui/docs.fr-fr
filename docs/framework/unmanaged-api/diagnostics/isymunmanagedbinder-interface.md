---
title: ISymUnmanagedBinder, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
ms.openlocfilehash: f4f925282d65cd9cbc8eb1c8825f358602de68ed
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441693"
---
# <a name="isymunmanagedbinder-interface"></a>ISymUnmanagedBinder, interface
Représente un Binder de symboles pour du code non managé.  
  
> [!IMPORTANT]
> L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetReaderForFile, méthode](isymunmanagedbinder-getreaderforfile-method.md)|Pour une interface de métadonnées et un nom de fichier donnés, retourne la structure [ISymUnmanagedReader](isymunmanagedreader-interface.md) correcte qui lira les symboles de débogage associés au module.|  
|[GetReaderFromStream, méthode](isymunmanagedbinder-getreaderfromstream-method.md)|À partir d’une interface de métadonnées et d’un flux de données qui contient le magasin de symboles, retourne la structure [ISymUnmanagedReader](isymunmanagedreader-interface.md) appropriée qui lira les symboles de débogage du magasin de symboles donné.|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder2, interface](isymunmanagedbinder2-interface.md)
- [ISymUnmanagedBinder3, interface](isymunmanagedbinder3-interface.md)
