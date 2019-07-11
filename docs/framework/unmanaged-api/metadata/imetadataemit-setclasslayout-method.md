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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c455b5196ceafef924de59e9134b89ed62455520
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737227"
---
# <a name="imetadataemitsetclasslayout-method"></a>IMetaDataEmit::SetClassLayout, méthode
Exécute la disposition des champs pour une classe qui a été défini par un appel antérieur à [DefineTypeDef, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).  
  
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
 [in] Un `mdTypeDef` jeton qui spécifie la classe à être disposé.  
  
 `dwPackSize`  
 [in] La taille de compression : 1, 2, 4, 8 ou 16 octets. La taille de compression est le nombre d’octets entre des champs adjacents.  
  
 `rFieldOffsets`  
 [in] Un tableau de [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, dont chacun spécifie un champ de la classe et le champ de l’offset dans la classe. Terminez le tableau avec `mdTokenNil`.  
  
 `ulClassSize`  
 [in] La taille, en octets, de la classe.  
  
## <a name="remarks"></a>Notes  
 La classe est définie initialement en appelant le [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) (méthode) et en spécifiant une des trois dispositions pour les champs de la classe : automatique, séquentielle ni explicite. Normalement, vous utiliser la disposition automatique et laisser l’exécution de choisir la meilleure façon de disposer les champs.  
  
 Toutefois, vous souhaiterez peut-être les champs disposés selon la disposition de code non managé. Dans ce cas, choisissez une disposition séquentielle ou explicite et appelez `SetClassLayout` pour terminer la disposition des champs :  
  
- Disposition séquentielle : Spécifiez la taille de compression. Un champ est aligné en fonction de sa taille naturelle ou la taille de compression, selon que le résultat dans le décalage plus petits du champ. Définissez `rFieldOffsets` et `ulClassSize` à zéro.  
  
- Disposition explicite : Spécifier le décalage de chaque champ ou spécifier la taille de la classe et la taille de compression.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
