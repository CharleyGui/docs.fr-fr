---
title: ICLRMetadataLocator::GetMetadata, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
ms.openlocfilehash: f0ba2342e9704ba06dd1d3612f699298c734a5eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723517"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata, méthode

Appelée par les services d’accès aux données common language runtime (CLR) pour récupérer les métadonnées d’une image.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `imagePath`  
 dans Chaîne qui spécifie le chemin d’accès du fichier image.  
  
 `imageTimestamp`  
 dans Horodatage du fichier image.  
  
 `imageSize`  
 dans Taille du fichier image.  
  
 `mvid`  
 dans Identificateur global unique de l’image.  
  
 `mdRva`  
 dans Adresse virtuelle relative (RVA) des métadonnées. L’adresse est relative à l’adresse de base de l’image.  
  
 `flags`  
 [in] Réservé pour une future utilisation.  
  
 `bufferSize`  
 dans Taille de la mémoire tampon dans laquelle placer les métadonnées.  
  
 `buffer`  
 à Mémoire tampon dans laquelle placer les métadonnées.  
  
 `dataSize`  
 à Taille des métadonnées retournées.  
  
## <a name="remarks"></a>Remarques  

 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** ClrData. idl, ClrData. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMetadataLocator, interface](iclrmetadatalocator-interface.md)
