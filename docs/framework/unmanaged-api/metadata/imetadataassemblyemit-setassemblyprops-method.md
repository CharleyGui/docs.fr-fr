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
ms.openlocfilehash: 7c6adcbcfe64f63048078b4ccba6727a58531033
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008103"
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
 dans Jeton de métadonnées qui spécifie la `Assembly` structure de métadonnées à modifier.  
  
 `pbPublicKey`  
 dans Pointeur vers la clé publique de l’éditeur de l’assembly.  
  
 `cbPublicKey`  
 dans Taille en octets de `pbPublicKey` .  
  
 `ulHashAlgId`  
 dans Identificateur de l’algorithme de hachage utilisé pour hacher les fichiers d’assembly.  
  
 `szName`  
 dans Nom de texte explicite de l’assembly.  
  
 `pMetaData`  
 dans Pointeur vers ASSEMBLYMETADATA qui contient les informations de version, de plateforme et de paramètres régionaux de l’assembly.  
  
 `dwAssemblyFlags`  
 dans Combinaison d’opérations de bits de valeurs [AssemblyFlags](assemblyflags-enumeration.md) qui spécifient différents attributs de l’assembly.  
  
## <a name="remarks"></a>Remarques  
 Pour créer une `Assembly` structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit ::D efineassembly](imetadataassemblyemit-defineassembly-method.md) .  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](imetadataassemblyemit-interface.md)
