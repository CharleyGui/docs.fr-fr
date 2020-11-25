---
title: IMetaDataConverter::GetMetaDataFromTypeLib, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeLib
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib
helpviewer_keywords:
- IMetaDataConverter::GetMetaDataFromTypeLib method [.NET Framework metadata]
- GetMetaDataFromTypeLib method [.NET Framework metadata]
ms.assetid: 97dc3a56-adfa-431f-889e-06a35ac84d51
topic_type:
- apiref
ms.openlocfilehash: ed0902824bdbb4d057bf5a7920db4b1d18eb7347
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714664"
---
# <a name="imetadataconvertergetmetadatafromtypelib-method"></a>IMetaDataConverter::GetMetaDataFromTypeLib, méthode

Obtient un pointeur d’interface vers une instance [IMetaDataImport](imetadataimport-interface.md) qui représente la signature des métadonnées de la bibliothèque de types représentée par l' `ITypeLib` instance spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMetaDataFromTypeLib (  
    [in]  ITypeLib        *pITL,
    [out] IMetaDataImport **ppMDI  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pITL`  
 dans Pointeur vers un `ITypeLib` objet qui représente la bibliothèque de types.  
  
 `ppMDI`  
 à Pointeur vers un emplacement qui reçoit l’adresse de l' `IMetaDataImport` instance qui représente la signature de métadonnées.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataImport, interface](imetadataimport-interface.md)
