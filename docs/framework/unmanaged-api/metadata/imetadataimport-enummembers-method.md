---
title: IMetaDataImport::EnumMembers, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: acb772a64c8f13405f2836bb5f4f308986dce414
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447659"
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers, méthode
Énumère les jetons MemberRef représentant les membres du type spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `phEnum`  
 [in, out] Pointeur vers l’énumérateur.  
  
 `cl`  
 dans Jeton TypeDef représentant le type dont les membres doivent être énumérés.  
  
 `rMembers`  
 à Tableau utilisé pour contenir les jetons MemberDef.  
  
 `cMax`  
 [in] Taille maximale du tableau `rMembers`.  
  
 `pcTokens`  
 à Nombre réel de jetons MemberDef retournés dans `rMembers`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers` retourné avec succès.|  
|`S_FALSE`|Il n’y a aucun jeton MemberDef à énumérer. Dans ce cas, `pcTokens` est égal à zéro.|  
  
## <a name="remarks"></a>Notes  
 Lors de l’énumération des collections de membres pour une classe, `EnumMembers` retourne uniquement les membres (champs et méthodes, mais **pas** les propriétés ou les événements) définis directement sur la classe. Elle ne retourne pas les membres que la classe hérite, même si la classe fournit une implémentation pour ces membres hérités. Pour énumérer les membres hérités, l’appelant doit parcourir explicitement la chaîne d’héritage. Notez que les règles de la chaîne d’héritage peuvent varier selon le langage ou le compilateur qui a émis les métadonnées d’origine.
 
 Les propriétés et les événements ne sont pas énumérés par `EnumMembers`. Pour les énumérer, utilisez [EnumProperties,](imetadataimport-enumproperties-method.md) ou [EnumEvents,](imetadataimport-enumevents-method.md).
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
