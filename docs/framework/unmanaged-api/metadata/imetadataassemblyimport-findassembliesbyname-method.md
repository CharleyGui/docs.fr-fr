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
ms.openlocfilehash: d2693a94f02214df6d7265b26e3d70d91adcf8a7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503833"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName, méthode
Obtient un tableau d’assemblys avec le `szAssemblyName` paramètre spécifié, à l’aide des règles standard utilisées par le Common Language Runtime (CLR) pour la résolution des références.  
  
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
 dans Répertoire racine dans lequel Rechercher l’assembly donné. Si cette valeur est définie sur `null` , `FindAssembliesByName` se présente uniquement dans le global assembly cache de l’assembly.  
  
 `szPrivateBin`  
 dans Liste des sous-répertoires délimités par des points-virgules (par exemple, « bin ; BIN2 »), sous le répertoire racine dans lequel Rechercher l’assembly. Ces répertoires sont détectés en plus de ceux spécifiés dans les règles de détection par défaut.  
  
 `szAssemblyName`  
 dans Nom de l’assembly à rechercher. Le format de cette chaîne est défini dans la page de référence de la classe pour <xref:System.Reflection.AssemblyName> .  
  
 `ppIUnk`  
 dans Tableau de type [IUnknown](/cpp/atl/iunknown) dans lequel placer les `IMetadataAssemblyImport` pointeurs d’interface.  
  
 `cMax`  
 à Nombre maximal de pointeurs d’interface qui peuvent être placés dans `ppIUnk` .  
  
 `pcAssemblies`  
 à Nombre de pointeurs d’interface retournés. Autrement dit, le nombre de pointeurs d’interface réellement placés dans `ppIUnk` .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName`retourné avec succès.|  
|`S_FALSE`|Il n’y a aucun assembly.|  
  
## <a name="remarks"></a>Remarques  
 Étant donné un nom d’assembly, la `FindAssembliesByName` méthode recherche l’assembly en suivant les règles standard pour la résolution des références d’assembly. (Pour plus d’informations, consultez [Comment le runtime localise les assemblys](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName`permet à l’appelant de configurer différents aspects du contexte du programme de résolution d’assembly, tels que la base de l’application et le chemin de recherche privé.  
  
 La `FindAssembliesByName` méthode requiert l’initialisation du CLR dans le processus afin d’appeler la logique de résolution d’assembly. Par conséquent, vous devez appeler [CoInitializeEE,](../hosting/coinitializeee-function.md) (en passant COINITEE_DEFAULT) avant d’appeler `FindAssembliesByName` , puis suivre un appel à [CoUninitializeCor,](../hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName`retourne un pointeur [IMetaDataImport](imetadataimport-interface.md) vers le fichier contenant le manifeste d’assembly pour le nom de l’assembly qui est passé. Si le nom de l’assembly donné n’est pas complètement spécifié (par exemple, s’il n’inclut pas de version), plusieurs assemblys peuvent être retournés.  
  
 `FindAssembliesByName`est couramment utilisé par un compilateur qui tente de trouver un assembly référencé au moment de la compilation.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Méthode de localisation des assemblys par le runtime](../../deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport, interface](imetadataassemblyimport-interface.md)
