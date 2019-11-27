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
ms.openlocfilehash: ff6932b6040a19e0ccda2f8d2140fa131cdd9224
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450077"
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
 [in, out] Pointeur vers l’énumérateur. Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.  
  
 `mb`  
 dans Jeton MethodDef qui limite la portée de l’énumération.  
  
 `rEventProp`  
 à Tableau utilisé pour stocker les événements ou les propriétés.  
  
 `cMax`  
 [in] Taille maximale du tableau `rEventProp`.  
  
 `pcEventProp`  
 à Nombre d’événements ou de propriétés retournés dans `rEventProp`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` retourné avec succès.|  
|`S_FALSE`|Il n’y a aucun événement ou propriété à énumérer. Dans ce cas, `pcEventProp` est égal à zéro.|  
  
## <a name="remarks"></a>Notes  
 De nombreux types de common language runtime définissent les événements de`Changed` de *propriété* et `On`méthodes de`Changed` de *propriété* associées à leurs propriétés. Par exemple, le type de <xref:System.Windows.Forms.Control?displayProperty=nameWithType> définit une propriété <xref:System.Windows.Forms.Control.Font%2A>, un événement <xref:System.Windows.Forms.Control.FontChanged> et une méthode <xref:System.Windows.Forms.Control.OnFontChanged%2A>. La méthode d’accesseur Set de la propriété <xref:System.Windows.Forms.Control.Font%2A> appelle <xref:System.Windows.Forms.Control.OnFontChanged%2A> méthode, qui à son tour déclenche l’événement <xref:System.Windows.Forms.Control.FontChanged>. Vous appelez `EnumMethodSemantics` à l’aide du MethodDef pour <xref:System.Windows.Forms.Control.OnFontChanged%2A> pour obtenir des références à la propriété <xref:System.Windows.Forms.Control.Font%2A> et à l’événement <xref:System.Windows.Forms.Control.FontChanged>.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
