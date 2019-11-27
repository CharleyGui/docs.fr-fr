---
title: IMetaDataEmit::DefineTypeRefByName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: 3dfdd473b01bfe83def52f957c52e0f4d11375ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434383"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName, méthode
Obtient un jeton de métadonnées pour un type qui est défini dans la portée spécifiée, qui est en dehors de la portée actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `tkResolutionScope`  
 dans Jeton spécifiant l’étendue de la résolution. Les types de jetons suivants sont valides :  
  
- `mdModuleRef`, si le type est défini dans le même assembly que celui dans lequel l’appelant est défini.  
  
- `mdAssemblyRef`, si le type est défini dans un assembly autre que celui dans lequel l’appelant est défini.  
  
- `mdTypeRef`, si le type est un type imbriqué.  
  
- `mdModule`, si le type est défini dans le même module dans lequel l’appelant est défini.  
  
- NULL, si le type est défini globalement.  
  
 `szName`  
 dans Nom du type de cible au format Unicode.  
  
 `ptr`  
 à Pointeur vers le jeton de `mdTypeRef` assigné au type.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
