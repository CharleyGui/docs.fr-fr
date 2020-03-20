---
title: IMetaDataEmit::SetClassLayout, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177572"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout, méthode
Termine la disposition des champs pour une classe qui a été définie par un appel préalable à [DefineTypeDef Méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 [dans] Un `mdTypeDef` jeton qui spécifie la classe à mettre en place.  
  
 `dwPackSize`  
 [dans] La taille d’emballage: 1, 2, 4, 8 ou 16 octets. La taille d’emballage est le nombre d’octets entre les champs adjacents.  
  
 `rFieldOffsets`  
 [dans] Un éventail de structures [COR_FIELD_OFFSET,](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) chacune spécifie un champ de la classe et le décalage du champ au sein de la classe. Terminez le `mdTokenNil`tableau avec .  
  
 `ulClassSize`  
 [dans] La taille, dans les octets, de la classe.  
  
## <a name="remarks"></a>Notes   
 La classe est initialement définie en appelant la méthode [IMetaDataEmit::DefineTypeDef,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) et en spécifiant l’une des trois mises en page pour les champs de la classe: automatique, séquentielle, ou explicite. Normalement, vous utiliseriez la disposition automatique et laisser le temps d’exécution choisir la meilleure façon d’exposer les champs.  
  
 Cependant, vous voudrez peut-être que les champs sont énoncés selon l’arrangement que le code non menté utilise. Dans ce cas, choisissez une mise en `SetClassLayout` page séquentielle ou explicite et appelez pour compléter la disposition des champs :  
  
- Mise en page séquentielle : Spécifier la taille de l’emballage. Un champ est aligné en fonction de sa taille naturelle ou de la taille de l’emballage, selon le plus petit décalage du champ. Définir `rFieldOffsets` `ulClassSize` et à zéro.  
  
- Mise en page explicite : soit spécifiez le décalage de chaque champ, soit spécifiez la taille de la classe et la taille de l’emballage.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
