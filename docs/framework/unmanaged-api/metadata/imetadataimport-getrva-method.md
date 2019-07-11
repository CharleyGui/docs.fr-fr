---
title: IMetaDataImport::GetRVA, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d305aa59c1b9e9e1225b30f12e36fc689d584db1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778888"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA, méthode
Obtient l’adresse virtuelle relative (RVA) et les indicateurs d’implémentation de la méthode ou le champ représenté par le jeton spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,   
   [out] ULONG       *pulCodeRVA,   
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `tk`  
 [in] Un jeton de métadonnées MethodDef ou FieldDef qui représente l’objet de code pour retourner l’adresse RVA. Si le jeton est FieldDef, le champ doit être une variable globale.  
  
 `pulCodeRVA`  
 [out] Pointeur vers l’adresse virtuelle relative de l’objet de code représenté par le jeton.  
  
 `pdwImplFlags`  
 [out] Pointeur vers les indicateurs d’implémentation pour la méthode. Cette valeur est un masque de bits à partir de la [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) énumération. La valeur de `pdwImplFlags` est valide uniquement si `tk` est un jeton MethodDef.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
