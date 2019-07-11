---
title: IMetaDataImport::GetTypeDefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77f72fb7eb7b0542dc9a3179811a78b189d6b3b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778842"
---
# <a name="imetadataimportgettypedefprops-method"></a>IMetaDataImport::GetTypeDefProps, méthode
Retourne des informations de métadonnées pour le <xref:System.Type> représenté par le jeton TypeDef spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 [in] Le jeton TypeDef qui représente le type à retourner les métadonnées.  
  
 `szTypeDef`  
 [out] Une mémoire tampon contenant le nom de type.  
  
 `cchTypeDef`  
 [in] La taille en caractères larges de `szTypeDef`.  
  
 `pchTypeDef`  
 [out] Le nombre de caractères étendus retournés dans `szTypeDef`.  
  
 `pdwTypeDefFlags`  
 [out] Pointeur vers tous les indicateurs qui modifient la définition de type. Cette valeur est un masque de bits à partir de la [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) énumération.  
  
 `ptkExtends`  
 [out] Un jeton de métadonnées TypeDef ou TypeRef qui représente le type de base du type demandé.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
