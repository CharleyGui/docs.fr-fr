---
title: IMetaDataAssemblyEmit::DefineAssemblyRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
ms.openlocfilehash: 612463bca18c23fac0b086adde2d208a0fbc5ae5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008168"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a>IMetaDataAssemblyEmit::DefineAssemblyRef, méthode
Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pbPublicKeyOrToken`  
 dans Clé publique de l’éditeur de l’assembly référencé. La fonction d’assistance [StrongNameTokenFromAssembly (](../strong-naming/strongnametokenfromassembly-function.md) peut être utilisée pour obtenir le hachage de la clé publique à passer comme ce paramètre.  
  
 `cbPublicKeyOrToken`  
 dans Taille en octets de `pbPublicKeyOrToken` .  
  
 `szName`  
 dans Nom de texte explicite de l’assembly. Cette valeur ne doit pas dépasser 1024 caractères.  
  
 `pMetaData`  
 dans Instance ASSEMBLYMETADATA qui contient les informations de version, de plateforme et de paramètres régionaux de l’assembly référencé.  
  
 `pbHashValue`  
 dans Données de hachage associées à l’assembly référencé. facultatif.  
  
 `cbHashValue`  
 dans Taille en octets de `pbHashValue` .  
  
 `dwAssemblyRefFlags`  
 dans Combinaison d’opérations de bits de valeurs [CorAssemblyFlags,](corassemblyflags-enumeration.md) qui influencent le comportement du moteur d’exécution.  
  
 `pmdar`  
 à Pointeur vers le jeton de `AssemblyRef` métadonnées retourné.  
  
## <a name="remarks"></a>Remarques  
 Une `AssemblyRef` structure de métadonnées doit être définie pour chaque assembly référencé par cet assembly.  
  
 Au moment de l’exécution, les détails d’un assembly référencé sont passés au programme de résolution d’assembly et indiquent qu’ils représentent les informations « comme étant générées ». Le programme de résolution d’assembly applique ensuite la stratégie.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](imetadataassemblyemit-interface.md)
