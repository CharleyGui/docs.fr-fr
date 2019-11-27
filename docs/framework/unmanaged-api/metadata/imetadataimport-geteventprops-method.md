---
title: IMetaDataImport::GetEventProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 18fe0c834506d0ac4cd15fd7af4c4f15904b0f81
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437577"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps, méthode
Obtient des informations de métadonnées pour l’événement représenté par le jeton d’événement spécifié, y compris le type déclarant, les méthodes d’ajout et de suppression pour les délégués et tous les indicateurs et autres données associées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ev`  
 dans Jeton de métadonnées d’événement représentant l’événement pour lequel obtenir les métadonnées.  
  
 `pClass`  
 à Pointeur vers le jeton TypeDef représentant la classe qui déclare l’événement.  
  
 `szEvent`  
 à Nom de l’événement référencé par `ev`.  
  
 `pchEvent`  
 dans Longueur demandée en caractères larges de `szEvent`.  
  
 `pdwEventFlags`  
 à Longueur retournée en caractères larges de `szEvent`.  
  
 `ptkEventType`  
 à Pointeur vers un jeton de métadonnées TypeRef ou TypeDef représentant le type de <xref:System.Delegate> de l’événement.  
  
 `pmdAddOn`  
 à Pointeur vers le jeton de métadonnées représentant la méthode qui ajoute des gestionnaires pour l’événement.  
  
 `pmdRemoveOn`  
 à Pointeur vers le jeton de métadonnées représentant la méthode qui supprime les gestionnaires de l’événement.  
  
 `pmdFire`  
 à Pointeur vers le jeton de métadonnées représentant la méthode qui déclenche l’événement.  
  
 `rmdOtherMethod`  
 à Tableau de pointeurs de jeton vers d’autres méthodes associées à l’événement.  
  
 `cMax`  
 [in] Taille maximale du tableau `rmdOtherMethod`.  
  
 `pcOtherMethod`  
 à Nombre de jetons retournés dans `rmdOtherMethod`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
