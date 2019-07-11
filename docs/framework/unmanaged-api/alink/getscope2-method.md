---
title: GetScope2, méthode
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c0abc63610f3f1ed6e8a556c44ee15edc1ea20b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741844"
---
# <a name="getscope2-method"></a>GetScope2, méthode
Obtient une portée d’importation.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly cible.  
  
 `FileToken`  
 ID du fichier à partir duquel importer.  
  
 `dwScope`  
 Portée de base zéro à importer.  
  
 `ppImportScope`  
 Reçoit le pointeur vers [IMetaDataImport2, Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface pour la portée indiquée.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Nécessite alink.h.  
  
## <a name="see-also"></a>Voir aussi

- [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
