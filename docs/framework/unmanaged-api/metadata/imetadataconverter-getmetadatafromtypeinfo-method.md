---
title: IMetaDataConverter::GetMetaDataFromTypeInfo, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetMetaDataFromTypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetMetaDataFromTypeInfo
helpviewer_keywords:
- GetMetaDataFromTypeInfo method [.NET Framework metadata]
- IMetaDataConverter::GetMetaDataFromTypeInfo method [.NET Framework metadata]
ms.assetid: d44484bb-23a3-49c3-9e46-69d0d9ab4f0f
topic_type:
- apiref
ms.openlocfilehash: 1f45310bc65bc8614033182a81db451b79bcf97f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714716"
---
# <a name="imetadataconvertergetmetadatafromtypeinfo-method"></a>IMetaDataConverter::GetMetaDataFromTypeInfo, méthode

Obtient un pointeur vers une instance [IMetaDataImport](imetadataimport-interface.md) qui représente la signature des métadonnées de la bibliothèque de types référencée par l' `ITypeInfo` instance spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMetaDataFromTypeInfo (  
    [in]  ITypeInfo         *pITI,  
    [out] IMetaDataImport   **ppMDI  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pITI`  
 dans Pointeur vers un `ITypeInfo` objet qui fait référence à la bibliothèque de types.  
  
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
