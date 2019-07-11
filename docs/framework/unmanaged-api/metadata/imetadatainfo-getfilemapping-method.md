---
title: IMetaDataInfo::GetFileMapping, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 22af95ef4bd1fca0a8253faa6ce0e1c7a862054d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782662"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping, méthode
Obtient la zone de mémoire du fichier mappé et le type de mappage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ppvData`  
 [out] Pointeur vers le début du fichier mappé.  
  
 `pcbData`  
 [out] La taille de la région mappée. Si `pdwMappingType` est `fmFlat`, c’est la taille du fichier.  
  
 `pdwMappingType`  
 [out] Un [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) valeur qui indique le type de mappage. L’implémentation actuelle du common language runtime (CLR) retourne toujours `fmFlat`. Autres valeurs sont réservées pour une utilisation ultérieure. Toutefois, vous devez toujours vérifier la valeur retournée, étant donné que les autres valeurs peuvent être activées dans les versions ou versions de service.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|Toutes les sorties sont remplies.|  
|`E_INVALIDARG`|NULL a été transmise en tant que valeur d’argument.|  
|`COR_E_NOTSUPPORTED`|L’implémentation CLR ne peut pas fournir d’informations sur la région de mémoire. Cela peut se produire pour les raisons suivantes :<br /><br /> -La portée des métadonnées a été ouverte avec le `ofWrite` ou `ofCopyMemory` indicateur.<br />-La portée des métadonnées a été ouverte sans le `ofReadOnly` indicateur.<br />-Le [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) méthode a été utilisée pour ouvrir uniquement la partie métadonnées du fichier.<br />-Le fichier n’est pas un fichier exécutable portable (PE). **Remarque :**  Ces conditions dépendent de l’implémentation CLR et sont susceptibles d’être affaiblies dans les futures versions du CLR.|  
  
## <a name="remarks"></a>Notes  
 La mémoire qui `ppvData` pointe est valide tant que la portée des métadonnées sous-jacentes est ouverte.  
  
 Afin que cette méthode fonctionne, lorsque vous mappez les métadonnées d’un fichier sur disque dans la mémoire en appelant le [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) (méthode), vous devez spécifier le `ofReadOnly` indicateur et vous ne devez pas spécifier le `ofWrite` ou `ofCopyMemory` indicateur.  
  
 Le choix du type de mappage de fichier pour chaque étendue est spécifique à une implémentation donnée du CLR. Elle ne peut pas être définie par l’utilisateur. L’implémentation actuelle du CLR retourne toujours `fmFlat` dans `pdwMappingType`, mais cela peut changer dans les futures versions du CLR ou dans les versions de service d’une version donnée. Vous devez toujours vérifier la valeur retournée `pdwMappingType`, car différents types ont différentes dispositions et les décalages.  
  
 Passage de NULL pour une des trois paramètres n’est pas pris en charge. La méthode retourne `E_INVALIDARG`, et aucune des sorties sont remplis. Ignorer le type de mappage ou la taille de la région peut entraîner l’arrêt du programme anormale.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataInfo, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping, énumération](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
