---
title: IMetaDataImport::GetCustomAttributeProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
ms.openlocfilehash: 320cfae93f8aae94f9315e8e20ed6cf7f9cced7c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491314"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps, méthode
Obtient la valeur de l'attribut personnalisé, en fonction de son jeton de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cv`  
 [in] Jeton de métadonnées représentant l'attribut personnalisé à récupérer.  
  
 `ptkObj`  
 [out, optional] Jeton de métadonnées représentant l'objet que l'attribut personnalisé modifie. Cette valeur peut correspondre à tout type de jeton de métadonnées, à l'exception de `mdCustomAttribute`.  
  
 `ptkType`  
 [out, optional] Jeton de métadonnées `mdMethodDef` ou `mdMemberRef` représentant le <xref:System.Type> de l'attribut personnalisé retourné.  
  
 `ppBlob`  
 [out, optional] Pointeur vers un tableau de données correspondant à la valeur de l'attribut personnalisé.  
  
 `pcbSize`  
 [out, optional] Taille en octets des données retournées dans *`ppBlob`.  
  
## <a name="remarks"></a>Remarques  
 Un attribut personnalisé est stocké sous forme d'un tableau de données, le format qui est compris par le moteur de métadonnées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
