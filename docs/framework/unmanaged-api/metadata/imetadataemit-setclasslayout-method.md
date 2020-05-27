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
ms.openlocfilehash: a18583ce807ffa672811f3a0cd1e744233f6eb30
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008827"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout, méthode
Termine la disposition des champs pour une classe qui a été définie par un appel antérieur à la [méthode DefineTypeDef](imetadataemit-definetypedef-method.md).  
  
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
 dans `mdTypeDef`Jeton qui spécifie la classe à mettre en sortie.  
  
 `dwPackSize`  
 dans Taille de compression : 1, 2, 4, 8 ou 16 octets. La taille de compression est le nombre d’octets entre les champs adjacents.  
  
 `rFieldOffsets`  
 dans Tableau de structures [COR_FIELD_OFFSET](cor-field-offset-structure.md) , chacune spécifiant un champ de la classe et l’offset du champ dans la classe. Terminez le tableau avec `mdTokenNil` .  
  
 `ulClassSize`  
 dans Taille, en octets, de la classe.  
  
## <a name="remarks"></a>Remarques  
 La classe est initialement définie en appelant la méthode [IMetaDataEmit ::D efinetypedef](imetadataemit-definetypedef-method.md) et en spécifiant l’une des trois dispositions pour les champs de la classe : automatique, séquentielle ou explicite. Normalement, vous utilisez la disposition automatique et laissez le runtime choisir la meilleure façon de disposer les champs.  
  
 Toutefois, vous souhaiterez peut-être disposer des champs présentés en fonction de la structure utilisée par le code non managé. Dans ce cas, choisissez une disposition séquentielle ou explicite et appelez `SetClassLayout` pour terminer la disposition des champs :  
  
- Disposition séquentielle : spécifiez la taille de compression. Un champ est aligné en fonction de sa taille naturelle ou de sa taille de compression, selon la valeur la plus petite du décalage du champ. Définissez `rFieldOffsets` et `ulClassSize` sur zéro.  
  
- Disposition explicite : spécifiez le décalage de chaque champ ou spécifiez la taille de la classe et la taille de la compression.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
