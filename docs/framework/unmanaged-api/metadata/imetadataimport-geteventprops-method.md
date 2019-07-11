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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c87f2212c761dc31a75addabca6970c5497aa2a0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782429"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps, méthode
Obtient les informations de métadonnées pour l’événement représenté par le jeton d’événement spécifié, y compris le type déclarant, l’ajouter et supprimer des méthodes pour les délégués et les indicateurs et autres données associées.  
  
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
 [in] Le jeton de métadonnées d’événement représentant l’événement pour lequel obtenir les métadonnées.  
  
 `pClass`  
 [out] Pointeur vers le jeton TypeDef représentant la classe qui déclare l’événement.  
  
 `szEvent`  
 [out] Le nom de l’événement référencé par `ev`.  
  
 `pchEvent`  
 [in] La longueur demandée en caractères larges de `szEvent`.  
  
 `pdwEventFlags`  
 [out] La longueur retournée en caractères larges de `szEvent`.  
  
 `ptkEventType`  
 [out] Un pointeur vers un TypeRef ou TypeDef métadonnées jeton représentant le <xref:System.Delegate> type de l’événement.  
  
 `pmdAddOn`  
 [out] Pointeur vers le jeton de métadonnées qui représente la méthode qui ajoute des gestionnaires pour l’événement.  
  
 `pmdRemoveOn`  
 [out] Pointeur vers le jeton de métadonnées qui représente la méthode qui supprime les gestionnaires pour l’événement.  
  
 `pmdFire`  
 [out] Pointeur vers le jeton de métadonnées représentant la méthode qui déclenche l’événement.  
  
 `rmdOtherMethod`  
 [out] Un tableau de pointeurs de jetons pour d’autres méthodes associées à l’événement.  
  
 `cMax`  
 [in] Taille maximale du tableau `rmdOtherMethod`.  
  
 `pcOtherMethod`  
 [out] Le nombre de jetons retournés dans `rmdOtherMethod`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
