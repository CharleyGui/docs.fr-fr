---
title: CorGenericParamAttr, énumération
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: ea50430c3ae6cef9b47880bcb8ad969f62ce9c39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704912"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr, énumération

Contient des valeurs qui décrivent les <xref:System.Type> paramètres des types génériques, tels qu’ils sont utilisés dans les appels à [IMetaDataEmit2 ::D efinegenericparam](imetadataemit2-definegenericparam-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`gpVarianceMask`|La variance de paramètre s’applique uniquement aux paramètres génériques pour les interfaces et les délégués.|  
|`gpNonVariant`|Indique l’absence de variance.|  
|`gpCovariant`|Indique la covariance.|  
|`gpContravariant`|Indique la contravariance.|  
|`gpSpecialConstraintMask`|Des contraintes spéciales peuvent s’appliquer à n’importe quel <xref:System.Type> paramètre.|  
|`gpNoSpecialConstraint`|Indique qu’aucune contrainte ne s’applique au <xref:System.Type> paramètre.|  
|`gpReferenceTypeConstraint`|Indique que le <xref:System.Type> paramètre doit être un type référence.|  
|`gpNotNullableValueTypeConstraint`|Indique que le <xref:System.Type> paramètre doit être un type valeur qui ne peut pas être une valeur null.|  
|`gpDefaultConstructorConstraint`|Indique que le <xref:System.Type> paramètre doit avoir un constructeur public par défaut qui ne prend pas de paramètres.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](metadata-enumerations.md)
