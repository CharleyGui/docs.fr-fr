---
title: IMetaDataEmit::DefineMethod, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177674"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod, méthode
Crée une définition pour une méthode ou une fonction globale avec la signature spécifiée, et renvoie un jeton à cette définition de méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineMethod (
    [in]  mdTypeDef         td,
    [in]  LPCWSTR           szName,
    [in]  DWORD             dwMethodFlags,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [in]  ULONG             ulCodeRVA,
    [in]  DWORD             dwImplFlags,
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 [dans] Le `mdTypedef` jeton de la classe mère ou de l’interface parente de la méthode. Définissez-vous, `td` `mdTokenNil`si vous définissez une fonction globale.  
  
 `szName`  
 [dans] Le nom du membre dans Unicode.  
  
 `dwMethodFlags`  
 [dans] Une valeur du recensement [de CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) qui spécifie les attributs de la méthode ou de la fonction globale.  
  
 `pvSigBlob`  
 [dans] La signature de la méthode. La signature est persistée comme fourni. Si vous avez besoin de spécifier des informations supplémentaires pour tous les paramètres, utilisez la méthode [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) méthode.  
  
 `cbSigBlob`  
 [dans] Le compte d’octets dans `pvSigBlob`.  
  
 `ulCodeRVA`  
 [dans] L’adresse du code.  
  
 `dwImplFlags`  
 [dans] Une valeur de l’énumération [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) qui spécifie les caractéristiques de mise en œuvre de la méthode.  
  
 `pmd`  
 [out] Le jeton du membre.  
  
## <a name="remarks"></a>Notes   
 L’API métadonnées garantit de maintenir des méthodes dans le même ordre que l’appelant les `td` émet pour une classe ou une interface fermée, qui est spécifiée dans le paramètre.  
  
 Des informations supplémentaires `DefineMethod` concernant l’utilisation et des paramètres particuliers sont données ci-dessous.  
  
## <a name="slots-in-the-v-table"></a>Machines à sous dans la table en V  
 Le temps d’exécution utilise des définitions de méthode pour configurer des emplacements v-table. Dans le cas où une ou plusieurs fentes doivent être ignorées, par exemple pour préserver la parité avec une disposition d’interface COM, une méthode factice est définie pour prendre la fente ou les fentes dans la table en v; définir `dwMethodFlags` la `mdRTSpecialName` valeur de l’énumération [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) et spécifier le nom comme:  
  
 \<_VtblGap>\<\_*SéquenceAumeurs**DeSlots*>
  
 où *SequenceNumber* est le numéro de séquence de la méthode et *CountOfSlots* est le nombre de fentes à sauter dans la table en v. Si *CountOfSlots* est omis, 1 est supposé. Ces méthodes factices ne sont pas callables à partir de code géré ou non géré et toute tentative de les appeler, à partir de code géré ou non géré, génère une exception. Leur seul but est de prendre de l’espace dans la table en v que le temps d’exécution génère pour l’intégration COM.  
  
## <a name="duplicate-methods"></a>Méthodes dupliqué  
 Vous ne devez pas définir les méthodes en double. Autrement dit, vous `DefineMethod` ne devriez pas appeler `td`avec `wzName`un `pvSig` ensemble de valeurs en double dans le , , et les paramètres. (Ces trois paramètres ensemble définissent uniquement la méthode.). Cependant, vous pouvez utiliser un triple en double à condition que, pour l’une des définitions de la méthode, vous définissez le `mdPrivateScope` bit dans le `dwMethodFlags` paramètre. (Le `mdPrivateScope` bit signifie que le compilateur n’émettra pas de référence à cette définition de méthode.)  
  
## <a name="method-implementation-information"></a>Informations sur la mise en œuvre de la méthode  
 L’information sur la mise en œuvre de la méthode n’est souvent pas connue au moment où la méthode est déclarée. Par conséquent, vous n’avez pas `ulCodeRVA` `dwImplFlags` besoin de `DefineMethod`passer des valeurs dans le et les paramètres lors de l’appel . Les valeurs peuvent être fournies plus tard par [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), le cas échéant.  
  
 Dans certaines situations, telles que l’invocation de la plate-forme (PInvoke) `ulCodeRVA` ou les scénarios d’interop COM, le corps de méthode ne sera pas fourni, et doit être réglé à zéro. Dans ces situations, la méthode ne doit pas être étiquetée comme abstraite, car le temps d’exécution localisera la mise en œuvre.  
  
## <a name="defining-a-method-for-pinvoke"></a>Définir une méthode pour PInvoke  
 Pour que chaque fonction non gérée soit appelée par PInvoke, vous devez définir une méthode gérée qui représente la fonction cible non gérée. Pour définir la méthode `DefineMethod` gérée, utilisez avec certains des paramètres définis à certaines valeurs, selon la façon dont PInvoke est utilisé :  
  
- Vrai PInvoke - implique l’invocation d’une méthode externe non gestion qui réside dans un DLL non gestion.  
  
- PInvoke local - implique l’invocation d’une méthode indigène non gérée qui est intégré dans le module géré actuel.  
  
 Les paramètres sont donnés dans le tableau suivant.  
  
|Paramètre|Valeurs pour le vrai PInvoke|Valeurs pour PInvoke local|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Ensemble `mdStatic`; clair `mdSynchronized` `mdAbstract`et .|  
|`pvSigBlob`|Une signature valide de méthode de course de langue commune (CLR) avec des paramètres qui sont des types gérés valides.|Une signature de méthode CLR valide avec des paramètres qui sont valides types gérés.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Définissez `miCil` et `miManaged`.|Définissez `miNative` et `miUnmanaged`.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
