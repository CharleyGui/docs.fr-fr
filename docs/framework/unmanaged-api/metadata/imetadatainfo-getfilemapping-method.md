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
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175263"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping, méthode
Obtient la région de mémoire du fichier cartographié, et le type de cartographie.  
  
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
 [out] Un pointeur pour le début du fichier cartographié.  
  
 `pcbData`  
 [out] La taille de la région cartographiée. Si `pdwMappingType` `fmFlat`c’est, c’est la taille du fichier.  
  
 `pdwMappingType`  
 [out] Une valeur [De CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) qui indique le type de cartographie. La mise en œuvre actuelle de l’heure de course de langue commune (CLR) revient `fmFlat`toujours . Les autres valeurs sont réservées pour un usage ultérieur. Toutefois, vous devez toujours vérifier la valeur retournée, car d’autres valeurs peuvent être activées dans les versions futures ou les versions de service.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|Toutes les sorties sont remplies.|  
|`E_INVALIDARG`|NULL a été adopté comme une valeur d’argument.|  
|`COR_E_NOTSUPPORTED`|La mise en œuvre du CLR ne peut pas fournir d’informations sur la région de la mémoire. Ceci peut se produire pour les raisons suivantes :<br /><br /> - Le champ d’application `ofWrite` des `ofCopyMemory` métadonnées a été ouvert avec le ou le drapeau.<br />- La portée des métadonnées a été ouverte sans le `ofReadOnly` drapeau.<br />- La méthode [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) méthode a été utilisé pour ouvrir seulement la partie métadonnées du fichier.<br />- Le fichier n’est pas un fichier portable exécutable (PE). **Note:**  Ces conditions dépendent de la mise en œuvre du CLR et risquent d’être affaiblies dans les versions futures du CLR.|  
  
## <a name="remarks"></a>Notes   
 La mémoire `ppvData` qui pointe vers est valable seulement tant que la portée sous-jacente des métadonnées est ouverte.  
  
 Pour que cette méthode fonctionne, lorsque vous cartographiez les métadonnées d’un fichier sur disque en mémoire en appelant la `ofReadOnly` méthode [IMetaDataDispenser ::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) méthode, vous devez spécifier le drapeau et vous ne devez pas spécifier le ou `ofWrite` `ofCopyMemory` le drapeau.  
  
 Le choix du type de cartographie des fichiers pour chaque portée est spécifique à une mise en œuvre donnée du CLR. Il ne peut pas être défini par l’utilisateur. La mise en œuvre `fmFlat` `pdwMappingType`actuelle du CLR revient toujours, mais cela peut changer dans les versions futures du CLR ou dans les versions de service futures d’une version donnée. Vous devez toujours vérifier `pdwMappingType`la valeur retournée, parce que différents types auront des mises en page et des compensations différentes.  
  
 Le passage de NULL pour l’un ou l’autre des trois paramètres n’est pas pris en charge. La méthode `E_INVALIDARG`revient, et aucune des sorties n’est remplie. Ignorer le type de cartographie ou la taille de la région peut entraîner une interruption anormale du programme.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataInfo, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [CorFileMapping, énumération](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
