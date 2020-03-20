---
title: IMetaDataImport::EnumMemberRefs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: b8a65b0748fec0e474d8b3b5dc03473fbd716108
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177331"
---
# <a name="imetadataimportenummemberrefs-method"></a>IMetaDataImport::EnumMemberRefs, méthode
Énumère les jetons MemberRef représentant les membres du type spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `phEnum`  
 [dans, dehors] Un pointeur à l’enumérateur.  
  
 `tkParent`  
 [dans] Un jeton TypeDef, TypeRef, MethodDef ou ModuleRef pour le type dont les membres doivent être énumérés.  
  
 `rMemberRefs`  
 [out] Le tableau utilisé pour stocker les jetons MemberRef.  
  
 `cMax`  
 [in] Taille maximale du tableau `rMemberRefs`.  
  
 `pcTokens`  
 [out] Le nombre réel de jetons MemberRef retournés dans `rMemberRefs`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMemberRefs`retourné avec succès.|  
|`S_FALSE`|Il n’y a pas de jetons MemberRef à énumérer. Dans ce `pcTokens` cas, est à zéro.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
