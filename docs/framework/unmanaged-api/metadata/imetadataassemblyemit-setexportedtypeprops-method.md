---
title: IMetaDataAssemblyEmit::SetExportedTypeProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: 076d027945dc27942e4b0989e14e86d829f76679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713483"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a>IMetaDataAssemblyEmit::SetExportedTypeProps, méthode

Modifie la structure de métadonnées `ExportedType` spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ct`  
 dans Jeton de métadonnées qui spécifie la `ExportedType` structure de métadonnées à modifier.  
  
 `tkImplementation`  
 dans Jeton, de type `File` , `AssemblyRef` ou `ExportedType` , qui spécifie la façon dont ce type est implémenté.  
  
 `tkTypeDef`  
 dans `TypeDef` Jeton référencé dans le fichier de code.  
  
 `dwExportedTypeFlags`  
 dans Combinaison d’opérations de bits de valeurs qui spécifient des attributs du type.  
  
## <a name="remarks"></a>Remarques  

 Pour créer une `ExportedType` structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit ::D efineexportedtype](imetadataassemblyemit-defineexportedtype-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](imetadataassemblyemit-interface.md)
