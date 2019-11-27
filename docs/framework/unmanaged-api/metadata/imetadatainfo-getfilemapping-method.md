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
ms.openlocfilehash: 0cd2071d4410615a08e774ba30e0e8fe8d1fa7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436174"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping, méthode
Obtient la région de la mémoire du fichier mappé et le type de mappage.  
  
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
 à Pointeur vers le début du fichier mappé.  
  
 `pcbData`  
 à Taille de la région mappée. Si `pdwMappingType` est `fmFlat`, il s’agit de la taille du fichier.  
  
 `pdwMappingType`  
 à Valeur [CorFileMapping,](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) qui indique le type de mappage. L’implémentation actuelle du common language runtime (CLR) retourne toujours `fmFlat`. Les autres valeurs sont réservées pour un usage ultérieur. Toutefois, vous devez toujours vérifier la valeur renvoyée, car d’autres valeurs peuvent être activées dans les versions ultérieures ou les versions de service.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|Toutes les sorties sont remplies.|  
|`E_INVALIDARG`|La valeur NULL a été transmise en tant que valeur d’argument.|  
|`COR_E_NOTSUPPORTED`|L’implémentation du CLR ne peut pas fournir d’informations sur la région de la mémoire. Ceci peut se produire pour les raisons suivantes :<br /><br /> -La portée des métadonnées a été ouverte avec l’indicateur `ofWrite` ou `ofCopyMemory`.<br />-La portée des métadonnées a été ouverte sans l’indicateur `ofReadOnly`.<br />-La méthode [IMetaDataDispenser :: OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) a été utilisée pour ouvrir uniquement la partie métadonnées du fichier.<br />-Le fichier n’est pas un fichier exécutable portable (PE). **Remarque :**  Ces conditions dépendent de l’implémentation du CLR et sont susceptibles d’être assouplies dans les futures versions du CLR.|  
  
## <a name="remarks"></a>Notes  
 La mémoire vers laquelle `ppvData` pointe est valide uniquement tant que la portée des métadonnées sous-jacentes est ouverte.  
  
 Pour que cette méthode fonctionne, lorsque vous mappez les métadonnées d’un fichier sur disque en mémoire en appelant la méthode [IMetaDataDispenser :: OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) , vous devez spécifier l’indicateur `ofReadOnly` et vous ne devez pas spécifier l’indicateur `ofWrite` ou `ofCopyMemory`.  
  
 Le choix du type de mappage de fichier pour chaque étendue est spécifique à une implémentation donnée du CLR. Il ne peut pas être défini par l’utilisateur. L’implémentation actuelle du CLR retourne toujours `fmFlat` dans `pdwMappingType`, mais cela peut changer dans les futures versions du CLR ou dans les futures versions de service d’une version donnée. Vous devez toujours vérifier la valeur retournée dans `pdwMappingType`, car les différents types auront des dispositions et des décalages différents.  
  
 La transmission de NULL pour l’un des trois paramètres n’est pas prise en charge. La méthode retourne `E_INVALIDARG`, et aucune des sorties n’est remplie. Si vous ignorez le type de mappage ou la taille de la région, vous risquez de provoquer un arrêt anormal du programme.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataInfo, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping, énumération](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
