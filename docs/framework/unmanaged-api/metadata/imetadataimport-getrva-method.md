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
ms.openlocfilehash: b4e7209c357f21a3f0de5770b483b673d5a5570b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729211"
---
# <a name="imetadataimportgetrva-method"></a>IMetaDataImport::GetRVA, méthode

Obtient l’adresse virtuelle relative (RVA) et les indicateurs d’implémentation de la méthode ou du champ représenté par le jeton spécifié.  
  
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
 dans Un jeton de métadonnées MethodDef ou FieldDef qui représente l’objet de code pour lequel retourner l’adresse RVA. Si le jeton est un FieldDef, le champ doit être une variable globale.  
  
 `pulCodeRVA`  
 à Pointeur vers l’adresse virtuelle relative de l’objet de code représenté par le jeton.  
  
 `pdwImplFlags`  
 à Pointeur vers les indicateurs d’implémentation de la méthode. Cette valeur est un masque de masque de l’énumération [CorMethodImpl,](cormethodimpl-enumeration.md) . La valeur de `pdwImplFlags` est valide uniquement si `tk` est un jeton MethodDef.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
