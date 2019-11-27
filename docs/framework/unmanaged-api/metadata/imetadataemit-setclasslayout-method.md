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
ms.openlocfilehash: 5214298c6ad9594548ab45ed583cb5b14ce1f30d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441768"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout, méthode
Termine la disposition des champs pour une classe qui a été définie par un appel antérieur à la [méthode DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
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
 dans Jeton `mdTypeDef` qui spécifie la classe à mettre en sortie.  
  
 `dwPackSize`  
 dans Taille de compression : 1, 2, 4, 8 ou 16 octets. La taille de compression est le nombre d’octets entre les champs adjacents.  
  
 `rFieldOffsets`  
 dans Tableau de structures [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) , chacune spécifiant un champ de la classe et l’offset du champ dans la classe. Mettez fin au tableau avec `mdTokenNil`.  
  
 `ulClassSize`  
 dans Taille, en octets, de la classe.  
  
## <a name="remarks"></a>Notes  
 La classe est initialement définie en appelant la méthode [IMetaDataEmit ::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) et en spécifiant l’une des trois dispositions pour les champs de la classe : automatique, séquentielle ou explicite. Normalement, vous utilisez la disposition automatique et laissez le runtime choisir la meilleure façon de disposer les champs.  
  
 Toutefois, vous souhaiterez peut-être disposer des champs présentés en fonction de la structure utilisée par le code non managé. Dans ce cas, choisissez une disposition séquentielle ou explicite et appelez `SetClassLayout` pour terminer la disposition des champs :  
  
- Disposition séquentielle : spécifiez la taille de compression. Un champ est aligné en fonction de sa taille naturelle ou de sa taille de compression, selon la valeur la plus petite du décalage du champ. Définissez `rFieldOffsets` et `ulClassSize` sur zéro.  
  
- Disposition explicite : spécifiez le décalage de chaque champ ou spécifiez la taille de la classe et la taille de la compression.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
