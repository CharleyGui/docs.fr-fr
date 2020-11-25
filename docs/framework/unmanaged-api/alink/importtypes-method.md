---
title: ImportTypes, méthode
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 762f78900add70238971978ceecda089d0c725ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705109"
---
# <a name="importtypes-method"></a>ImportTypes, méthode

Lance l’importation de types à partir de chaque étendue importée via la [méthode ImportFile](importfile-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `AssemblyID`  
 ID de l’assembly dans lequel effectuer l’importation.  
  
 `FileToken`  
 ID du fichier à partir duquel effectuer l’importation.  
  
 `dwScope`  
 Étendue de base zéro à importer.  
  
 `phEnum`  
 Reçoit un handle d’énumérateur pour les types de cette portée.  
  
 `ppImportScope`  
 Reçoit éventuellement l’interface d' [interface IMetaDataImport](../metadata/imetadataimport-interface.md) .  
  
 `pdwCountOfTypes`  
 Reçoit éventuellement le nombre de types dans l’étendue indiquée.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
