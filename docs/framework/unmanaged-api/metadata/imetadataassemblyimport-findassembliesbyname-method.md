---
title: IMetaDataAssemblyImport::FindAssembliesByName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177802"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName, méthode
Obtient un éventail d’assemblages avec le paramètre spécifié, `szAssemblyName` en utilisant les règles standard employées par l’heure de circulation de langue commune (CLR) pour résoudre des références.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,
    [in]  LPCWSTR     szPrivateBin,
    [in]  LPCWSTR     szAssemblyName,
    [out] IUnknown    *ppIUnk[],
    [in]  ULONG       cMax,
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szAppBase`  
 [dans] Le répertoire racine dans lequel rechercher l’assemblage donné. Si cette valeur `null`est `FindAssembliesByName` définie à , ne regardera que dans le cache d’assemblage global pour l’assemblage.  
  
 `szPrivateBin`  
 [dans] Une liste de sous-directions semi-colons (par exemple, "bin;bin2"), sous le répertoire des racines, dans laquelle rechercher l’assemblage. Ces répertoires sont sondés en plus de ceux spécifiés dans les règles de sondage par défaut.  
  
 `szAssemblyName`  
 [dans] Le nom de l’assemblée à trouver. Le format de cette chaîne est défini <xref:System.Reflection.AssemblyName>dans la page de référence de la classe pour .  
  
 `ppIUnk`  
 [dans] Un tableau de type [IUnknown](/cpp/atl/iunknown) `IMetadataAssemblyImport` dans lequel mettre les pointeurs d’interface.  
  
 `cMax`  
 [out] Le nombre maximum de pointeurs d’interface qui peuvent être placés en `ppIUnk`.  
  
 `pcAssemblies`  
 [out] Le nombre de pointeurs d’interface retourné. C’est-à-dire, le nombre `ppIUnk`de pointeurs d’interface effectivement placés dans .  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`retourné avec succès.|  
|`S_FALSE`|Il n’y a pas d’assemblées.|  
  
## <a name="remarks"></a>Notes   
 Compte tenu d’un nom d’assemblage, la `FindAssembliesByName` méthode trouve l’assemblage en suivant les règles standard pour résoudre les références d’assemblage. (Pour plus d’informations, voir [Comment les assemblages De localisation de durée de course](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permet à l’appelant de configurer divers aspects du contexte du résolveur d’assemblage, tels que la base d’application et le chemin de recherche privé.  
  
 La `FindAssembliesByName` méthode exige que le CLR soit paradé dans le processus afin d’invoquer la logique de résolution de l’assemblage. Par conséquent, vous devez appeler [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passant `FindAssembliesByName`COINITEE_DEFAULT) avant d’appeler , puis suivre avec un appel à [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName`renvoie un pointeur [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) au fichier contenant le manifeste d’assemblage pour le nom d’assemblage qui est transmis. Si le nom d’assemblage donné n’est pas entièrement spécifié (par exemple, s’il n’inclut pas de version), plusieurs assemblages peuvent être retournés.  
  
 `FindAssembliesByName`est couramment utilisé par un compilateur qui tente de trouver un assemblage référencé au moment de la compilation.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Méthode de localisation des assemblys par le runtime](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
