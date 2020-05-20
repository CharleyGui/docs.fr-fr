---
title: ISymUnmanagedBinder2, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
ms.openlocfilehash: 8a4fbb40ec2426d000628fbd6d5f0241d3152c18
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441667"
---
# <a name="isymunmanagedbinder2-interface"></a>ISymUnmanagedBinder2, interface
Représente un Binder de symboles pour du code non managé et étend l’interface [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) .  
  
> [!IMPORTANT]
> L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetReaderForFile2, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|À partir d’une interface de métadonnées et d’un nom de fichier, retourne l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) appropriée qui lira les symboles de débogage associés au module. Fournit une recherche plus complète que la méthode [ISymUnmanagedBinder :: GetReaderForFile,](isymunmanagedbinder-getreaderforfile-method.md) .|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedBinder, interface](isymunmanagedbinder-interface.md)
- [ISymUnmanagedBinder3, interface](isymunmanagedbinder3-interface.md)
