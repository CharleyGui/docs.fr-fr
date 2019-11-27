---
title: ExportType, méthode
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
ms.openlocfilehash: 84c41e467c57afd2562e7aa8dd72ce4796249667
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438572"
---
# <a name="exporttype-method"></a>ExportType, méthode
Spécifie qu’un type peut être exportable.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly à partir duquel effectuer l’exportation.  
  
 `FileToken`  
 Jeton de fichier ou ID d’assembly du fichier qui définit le type exportable.  
  
 `TypeToken`  
 Jeton de type à rendre exportable.  
  
 `pszTypename`  
 Nom de type qualifié complet à rendre exportable.  
  
 `dwFlags`  
 `ComType` indicateurs tels que `tdPublic` ou `tdNested`. Ce paramètre peut être passé à la [méthode DefineExportedType,](../metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Reçoit le jeton pour le type exporté.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
