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
ms.openlocfilehash: 3b47d1559300a462ccda42bc88da43f66c1043ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491301"
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
 à Nom de l’événement référencé par `ev` .  
  
 `pchEvent`  
 dans Longueur demandée en caractères larges de `szEvent` .  
  
 `pdwEventFlags`  
 à Longueur retournée en caractères larges de `szEvent` .  
  
 `ptkEventType`  
 à Pointeur vers un jeton de métadonnées TypeRef ou TypeDef représentant le <xref:System.Delegate> type de l’événement.  
  
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
 à Nombre de jetons retournés dans `rmdOtherMethod` .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
