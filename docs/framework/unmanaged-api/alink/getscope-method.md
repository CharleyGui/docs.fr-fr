---
title: GetScope, méthode
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
ms.openlocfilehash: 078168ae8860f18ff6f811dcc972e3eb3c857e1d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447202"
---
# <a name="getscope-method"></a>GetScope, méthode
Obtient une étendue d’importation.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID unique de l’assembly dans lequel effectuer l’importation.  
  
 `FileToken`  
 ID unique du fichier à partir duquel effectuer l’importation.  
  
 `dwScope`  
 Étendue de base zéro à importer.  
  
 `ppImportScope`  
 Reçoit l’interface d' [interface IMetaDataImport](../metadata/imetadataimport-interface.md) pour l’étendue.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
