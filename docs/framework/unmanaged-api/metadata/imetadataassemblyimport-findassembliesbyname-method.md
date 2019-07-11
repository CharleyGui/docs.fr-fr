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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 315d9aa6f7db51342e71ba3f8fcdc091f7707743
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777983"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a>IMetaDataAssemblyImport::FindAssembliesByName, méthode
Obtient un tableau d’assemblys avec la valeur `szAssemblyName` paramètre, à l’aide de règles standard employées par le common language runtime (CLR) pour la résolution des références.  
  
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
 [in] Le répertoire racine dans lequel rechercher l’assembly donné. Si cette valeur est définie sur `null`, `FindAssembliesByName` recherchera uniquement dans le global assembly cache l’assembly.  
  
 `szPrivateBin`  
 [in] Liste des sous-répertoires séparés par des points-virgules (par exemple, « bin ; bin2 »), sous le répertoire racine, dans laquelle rechercher l’assembly. Ces répertoires sont détectés en plus de celles spécifiées dans la valeur par défaut, les règles de détection.  
  
 `szAssemblyName`  
 [in] Le nom de l’assembly à rechercher. Le format de cette chaîne est défini dans la page de référence de classe pour <xref:System.Reflection.AssemblyName>.  
  
 `ppIUnk`  
 [in] Tableau de type [IUnknown](/cpp/atl/iunknown) dans lequel placer la `IMetadataAssemblyImport` pointeurs d’interface.  
  
 `cMax`  
 [out] Le nombre maximal de pointeurs d’interface qui peut être placé dans `ppIUnk`.  
  
 `pcAssemblies`  
 [out] Le nombre de pointeurs d’interface retourné. Autrement dit, le nombre de pointeurs d’interface placés dans `ppIUnk`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`FindAssembliesByName` retourné avec succès.|  
|`S_FALSE`|Il n’existe aucun assembly.|  
  
## <a name="remarks"></a>Notes  
 Étant donné un nom d’assembly, le `FindAssembliesByName` méthode recherche l’assembly en suivant les règles standards pour résoudre les références d’assembly. (Pour plus d’informations, consultez [méthode de localisation des assemblys par le Runtime](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permet à l’appelant de configurer différents aspects du contexte de programme de résolution d’assembly, tels qu’application chemin de recherche de base et privées.  
  
 Le `FindAssembliesByName` (méthode), le CLR doit être initialisée dans le processus pour appeler la logique de résolution d’assembly. Par conséquent, vous devez appeler [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (en passant COINITEE_DEFAULT) avant d’appeler `FindAssembliesByName`, puis suivez avec un appel à [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).  
  
 `FindAssembliesByName` Retourne un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointeur vers le fichier contenant le manifeste d’assembly pour le nom de l’assembly qui est passé. Si le nom de l’assembly donné n’est pas entièrement spécifié (par exemple, si elle n’inclut pas de version), plusieurs assemblys peuvent être retournés.  
  
 `FindAssembliesByName` est couramment utilisé par un compilateur qui tente de trouver un assembly référencé au moment de la compilation.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Méthode de localisation des assemblys par le runtime](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
