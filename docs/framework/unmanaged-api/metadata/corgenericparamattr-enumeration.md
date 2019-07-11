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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 981829500e499be05a8de7c1ffb4683429a903e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781848"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr, énumération
Contient des valeurs qui décrivent le <xref:System.Type> paramètres pour les types génériques, comme utilisés lors d’appels à [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
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
|`gpVarianceMask`|Variance de paramètre s’applique uniquement aux paramètres génériques pour les interfaces et délégués.|  
|`gpNonVariant`|Indique l’absence de variance.|  
|`gpCovariant`|Indique la covariance.|  
|`gpContravariant`|Indique la contravariance.|  
|`gpSpecialConstraintMask`|Les contraintes spéciales peuvent s’appliquer à tout <xref:System.Type> paramètre.|  
|`gpNoSpecialConstraint`|Indique qu’aucune contrainte s’applique à la <xref:System.Type> paramètre.|  
|`gpReferenceTypeConstraint`|Indique que le <xref:System.Type> paramètre doit être un type référence.|  
|`gpNotNullableValueTypeConstraint`|Indique que le <xref:System.Type> paramètre doit être un type valeur qui ne peut pas être une valeur null.|  
|`gpDefaultConstructorConstraint`|Indique que le <xref:System.Type> paramètre doit avoir un constructeur public par défaut qui n’accepte aucun paramètre.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
