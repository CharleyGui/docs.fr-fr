---
title: IMetaDataConverter::GetTypeLibFromMetaData, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: eed8661f8885ca16492ab336a599b5290057843a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714599"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a>IMetaDataConverter::GetTypeLibFromMetaData, méthode

Obtient un pointeur vers une `ITypeLib` instance de qui représente la bibliothèque de types qui a la bibliothèque et les noms de modules spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `strModule`  
 dans Nom du module de la bibliothèque de types.  
  
 `strTlbName`  
 dans Nom de la bibliothèque de types.  
  
 `ppITL`  
 à Pointeur vers un emplacement qui reçoit l’adresse de l' `ITypeLib` instance qui représente la bibliothèque de types.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataConverter, interface](imetadataconverter-interface.md)
