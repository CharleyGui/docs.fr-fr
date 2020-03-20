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
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177270"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps, méthode
Obtient des informations sur les métadonnées pour l’événement représentées par le jeton d’événement spécifié, y compris le type de déclaration, les méthodes d’ajout et de suppression pour les délégués, et tous les drapeaux et autres données associées.  
  
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
 [dans] Le jeton des métadonnées de l’événement représentant l’événement pour obtenir des métadonnées pour.  
  
 `pClass`  
 [out] Un pointeur pour le jeton TypeDef représentant la classe qui déclare l’événement.  
  
 `szEvent`  
 [out] Le nom de l’événement référencé par `ev`.  
  
 `pchEvent`  
 [dans] La longueur demandée `szEvent`en caractères larges de .  
  
 `pdwEventFlags`  
 [out] La longueur retournée dans `szEvent`de larges caractères de .  
  
 `ptkEventType`  
 [out] Un pointeur vers un jeton de métadonnées <xref:System.Delegate> TypeRef ou TypeDef représentant le type de l’événement.  
  
 `pmdAddOn`  
 [out] Un pointeur sur le jeton des métadonnées représentant la méthode qui ajoute des gestionnaires pour l’événement.  
  
 `pmdRemoveOn`  
 [out] Un pointeur sur le jeton des métadonnées représentant la méthode qui supprime les gestionnaires pour l’événement.  
  
 `pmdFire`  
 [out] Un pointeur sur le jeton des métadonnées représentant la méthode qui soulève l’événement.  
  
 `rmdOtherMethod`  
 [out] Un éventail de pointeurs symboliques à d’autres méthodes associées à l’événement.  
  
 `cMax`  
 [in] Taille maximale du tableau `rmdOtherMethod`.  
  
 `pcOtherMethod`  
 [out] Le nombre de jetons `rmdOtherMethod`retournés dans .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
