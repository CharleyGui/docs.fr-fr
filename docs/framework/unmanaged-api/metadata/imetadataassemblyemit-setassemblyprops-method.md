---
title: IMetaDataAssemblyEmit::SetAssemblyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: f79320d5b7d2ad4ad44a79fae063ce6718490a70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431950"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps, méthode
Modifie la structure de métadonnées `Assembly` spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pma`  
 dans Jeton de métadonnées qui spécifie la structure de métadonnées `Assembly` à modifier.  
  
 `pbPublicKey`  
 dans Pointeur vers la clé publique de l’éditeur de l’assembly.  
  
 `cbPublicKey`  
 dans Taille en octets de `pbPublicKey`.  
  
 `ulHashAlgId`  
 dans Identificateur de l’algorithme de hachage utilisé pour hacher les fichiers d’assembly.  
  
 `szName`  
 dans Nom de texte explicite de l’assembly.  
  
 `pMetaData`  
 dans Pointeur vers ASSEMBLYMETADATA qui contient les informations de version, de plateforme et de paramètres régionaux de l’assembly.  
  
 `dwAssemblyFlags`  
 dans Combinaison d’opérations de bits de valeurs [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) qui spécifient différents attributs de l’assembly.  
  
## <a name="remarks"></a>Notes  
 Pour créer une structure de métadonnées `Assembly`, utilisez la méthode [IMetaDataAssemblyEmit ::D efineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
