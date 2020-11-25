---
title: ImportTypes2, méthode
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
ms.openlocfilehash: 2ec7708edd86b9f2656d0eee434992c3b73200ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705044"
---
# <a name="importtypes2-method"></a>ImportTypes2, méthode

Initialise l’importation de types. Appelez cette méthode pour commencer l’importation de types à partir de chaque étendue importée via la [méthode ImportFile](importfile-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `AssemblyID`  
 ID de l’assembly dans lequel effectuer l’importation.  
  
 `FileToken`  
 ID du fichier à partir duquel effectuer l’importation.  
  
 `dwScope`  
 Étendue de base zéro à partir de laquelle effectuer l’importation.  
  
 `phEnum`  
 Reçoit un handle d’énumérateur pour les types dans l’étendue donnée.  
  
 `ppImportScope`  
 Reçoit éventuellement l’interface d' [interface IMetaDataImport2](../metadata/imetadataimport2-interface.md) .  
  
 `pdwCountOfTypes`  
 Reçoit éventuellement le nombre de types dans l’étendue spécifiée.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink2, interface](ialink2-interface.md)
- [IALink, interface](ialink-interface.md)
- [API ALink](index.md)
