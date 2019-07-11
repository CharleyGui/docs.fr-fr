---
title: IMetaDataTables2::GetMetaDataStreamInfo, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f559a269b48ceabfbe9c3a0cf3665458a2cf012
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769281"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a>IMetaDataTables2::GetMetaDataStreamInfo, méthode
Obtient le nom, la taille et le contenu du flux de métadonnées à l’index spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ix`  
 [in] L’index du flux de métadonnées demandées.  
  
 `ppchName`  
 [out] Un pointeur vers le nom du flux.  
  
 `ppv`  
 [out] Un pointeur vers le flux de métadonnées.  
  
 `pcb`  
 [out] La taille, en octets, de `ppv`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataTables2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
- [IMetaDataTables, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
