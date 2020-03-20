---
title: IMetaDataDispenserEx::SetOption, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.SetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type:
- apiref
ms.openlocfilehash: f8e85a670d04e5825653864484b7ccd9ce747949
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175900"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption, méthode
Définit l’option spécifiée à une valeur donnée pour la portée actuelle des métadonnées. L’option contrôle la façon dont les appels à la portée actuelle des métadonnées sont traités.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `optionId`  
 [dans] Un pointeur à un GUID qui spécifie l’option à définir.  
  
 `pValue`  
 [dans] La valeur à utiliser pour définir l’option. Le type de cette valeur doit être une variante du type d’option spécifiée.  
  
## <a name="remarks"></a>Notes   
 Le tableau suivant répertorie `optionId` les GUID disponibles que le `pValue` paramètre peut indiquer et les valeurs valides correspondantes pour le paramètre.  
  
|GUID|Description|`pValue`Paramètre|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Contrôle les éléments vérifiés pour les doublons. Chaque fois que vous appelez une méthode [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) qui crée un nouvel élément, vous pouvez demander la méthode pour vérifier si l’élément existe déjà dans la portée actuelle. Par exemple, vous pouvez vérifier `mdMethodDef` l’existence d’articles; dans ce cas, lorsque vous appelez [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), il vérifiera que la méthode n’existe pas déjà dans la portée actuelle. Cette vérification utilise la clé qui identifie de façon unique une méthode donnée : type parent, nom et signature.|Doit être une variante de type UI4, et doit contenir une combinaison des valeurs des [CorCheckDuplicatesPour](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) l’énumération.|  
|MetaDataRefToDefCheck (en)|Les contrôles qui ont fait référence aux éléments sont convertis en définitions. Par défaut, le moteur de métadonnées optimisera le code en convertissant un élément référencé à sa définition si l’élément référencé est effectivement défini dans la portée actuelle.|Doit être une variante de type UI4, et doit contenir une combinaison des valeurs de l’énumération [CorRefToDefCheck.](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md)|  
|MétaDataNotificationForTokenMovement|Les contrôles qui se produisent lors d’une fusion des métadonnées génèrent des rappels. Utilisez la méthode [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) pour établir votre interface [IMapToken.](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)|Doit être une variante de type UI4, et doit contenir une combinaison des valeurs de l’énumération [CorNotificationForTokenMovement.](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md)|  
|MetaDataSetENC|Contrôle le comportement de l’édition et de la poursuite (ENC). Un seul mode de comportement peut être défini à la fois.|Doit être une variante de type UI4, et doit contenir une valeur de l’énumération [CorSetENC.](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) La valeur n’est pas un peumask.|  
|MetaDataErrorIfEmitOutOfOrder MetaDataErrorIfEmitOutOfOrder MetaDataErrorIfEmitOutOfOrder MetaD|Les contrôles qui émettent des erreurs hors commande génèrent des rappels. L’émission de métadonnées hors de l’ordre n’est pas fatale; cependant, si vous émettez des métadonnées dans un ordre qui est favorisé par le moteur de métadonnées, les métadonnées sont plus compactes et peuvent donc être recherchées plus efficacement. Utilisez `IMetaDataEmit::SetHandler` la méthode pour établir votre interface [IMetaDataError.](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)|Doit être une variante de type UI4, et doit contenir une combinaison des valeurs de l’énumération [CorErrorIfEmitOutOfOrder.](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md)|  
|MetaDataImportOption|Contrôle les types d’éléments supprimés lors d’un ENC sont récupérés par un enumérateur.|Doit être une variante de type UI4, et doit contenir une combinaison des valeurs de l’énumération [CorImportOptions Enumeration.](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md)|  
|MetaDataThreadSafetyOptions|Contrôle si le moteur des métadonnées obtient des serrures de lecteur/auteur, assurant ainsi la sécurité du thread. Par défaut, le moteur suppose que l’accès est à un seul threaded par l’appelant, de sorte qu’aucun verrou n’est obtenu. Les clients sont responsables du maintien d’une synchronisation appropriée des fils lors de l’utilisation des métadonnées API.|Doit être une variante de type UI4, et doit contenir une valeur de l’énumération [CorThreadSafetyOptions.](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) La valeur n’est pas un peumask.|  
|MétaDataGenerateTCEAdapters|Contrôle si l’importateur de bibliothèque type devrait générer les adaptateurs d’événements étroitement couplés (TCE) pour les conteneurs de points de connexion COM.|Doit être une variante de type BOOL. Si `pValue` elle `true`est configuré, l’importateur de bibliothèque de type génère les adaptateurs TCE.|  
|MetaDataTypeLibImportNamespace|Spécifie un espace de nom non par défaut pour la bibliothèque type qui est importé.|Doit être soit une valeur nulle ou une variante de type BSTR. S’il `pValue` s’agit d’une valeur nulle, l’espace nom actuel est configuré pour annuler; autrement, l’espace de nom actuel est réglé à la chaîne qui se tient dans le type BSTR de la variante.|  
|MetaDataLinkerOptions MetaDataLinkerOptions MetaDataLinkerOptions MetaD|Contrôle si le lien doit générer un assemblage ou un fichier module cadre .NET.|Doit être une variante de type UI4, et doit contenir une combinaison des valeurs de l’énumération [CorLinkerOptions.](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md)|  
|MetaDataRuntimeVersion|Spécifie la version de l’heure de jeu de langage commun contre laquelle cette image a été construite. La version est stockée sous forme de chaîne, comme "v1.0.3705".|Doit être une valeur nulle, une valeur VT_EMPTY, ou une variante de type BSTR. Si `pValue` elle est nulle, la version de l’heure d’exécution est définie pour annuler. Si `pValue` elle est VT_EMPTY, la version est définie à une valeur par défaut, qui est tirée de la version de Mscorwks.dll dans laquelle le code des métadonnées est en cours d’exécution. Dans le cas contraire, la version runtime est réglée sur la chaîne qui se tient dans le type BSTR de la variante.|  
|MetaDataMergerOptions|Spécifie les options de fusion des métadonnées.|Doit être une variante de type UI4, et doit `MergeFlags` contenir une combinaison des valeurs de l’énumération, qui est décrite dans le fichier CorHdr.h.|  
|MetaDataPreserveLocalRefs MetaDataPreserveLocalRefs|Désactiver l’optimisation des références locales en définitions.|Doit contenir une combinaison des valeurs de l’énumération [CorLocalRefPreservation.](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md)|  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenserEx, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
