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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f005ee9d3d9d4b8977cd6a1838fe46015e604df5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777472"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a>IMetaDataEmit::DefineTypeRefByName, méthode
Obtient les métadonnées jeton pour un type qui est défini dans la portée spécifiée, qui est en dehors de la portée actuelle.  
  
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
 [in] Le jeton en spécifiant la résolution de portée. Les types de jetons suivants sont valides :  
  
- `mdModuleRef`, si le type est défini dans le même assembly dans lequel l’appelant est défini.  
  
- `mdAssemblyRef`, si le type est défini dans un assembly autre que celui dans lequel l’appelant est défini.  
  
- `mdTypeRef`, si le type est un type imbriqué.  
  
- `mdModule`, si le type est défini dans le même module que celui dans lequel l’appelant est défini.  
  
- Valeur null, si le type est défini dans le monde entier.  
  
 `szName`  
 [in] Le nom du type cible au format Unicode.  
  
 `ptr`  
 [out] Un pointeur vers le `mdTypeRef` jeton qui est assigné au type.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
