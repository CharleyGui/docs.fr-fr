---
title: IMetaDataImport::EnumMethodSemantics, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175458"
---
# <a name="imetadataimportenummethodsemantics-method"></a>IMetaDataImport::EnumMethodSemantics, méthode
Énumère les propriétés et les événements de modification de propriétés auxquels la méthode spécifiée est associée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `phEnum`  
 [dans, dehors] Un pointeur à l’enumérateur. Cela doit être NULL pour le premier appel de cette méthode.  
  
 `mb`  
 [dans] Un jeton MethodDef qui limite la portée de l’énumération.  
  
 `rEventProp`  
 [out] Le tableau utilisé pour stocker les événements ou les propriétés.  
  
 `cMax`  
 [in] Taille maximale du tableau `rEventProp`.  
  
 `pcEventProp`  
 [out] Le nombre d’événements `rEventProp`ou de propriétés retournés dans .  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics`retourné avec succès.|  
|`S_FALSE`|Il n’y a pas d’événements ou de propriétés à énumérer. Dans ce `pcEventProp` cas, c’est zéro.|  
  
## <a name="remarks"></a>Notes   
 De nombreux types courants d’exécution de langue définissent les événements *de propriété* `Changed` `On`et les méthodes de *propriété* `Changed` liées à leurs propriétés. Par exemple, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> le type <xref:System.Windows.Forms.Control.Font%2A> définit <xref:System.Windows.Forms.Control.FontChanged> une propriété, <xref:System.Windows.Forms.Control.OnFontChanged%2A> un événement et une méthode. La méthode d’accesseur défini de la <xref:System.Windows.Forms.Control.Font%2A> méthode des appels <xref:System.Windows.Forms.Control.OnFontChanged%2A> de propriété, qui à son tour soulève l’événement. <xref:System.Windows.Forms.Control.FontChanged> Vous appelez `EnumMethodSemantics` en utilisant le <xref:System.Windows.Forms.Control.OnFontChanged%2A> MethodDef <xref:System.Windows.Forms.Control.Font%2A> pour obtenir <xref:System.Windows.Forms.Control.FontChanged> des références à la propriété et l’événement.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
