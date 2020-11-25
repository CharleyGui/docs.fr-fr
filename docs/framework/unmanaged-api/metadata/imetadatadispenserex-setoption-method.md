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
ms.openlocfilehash: 4216658eb562c5c57b75c3c257cd8e53a7a34221
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700585"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption, méthode

Définit l’option spécifiée sur une valeur donnée pour la portée de métadonnées actuelle. L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `optionId`  
 dans Pointeur vers un GUID qui spécifie l’option à définir.  
  
 `pValue`  
 dans Valeur à utiliser pour définir l’option. Le type de cette valeur doit être une variante du type de l’option spécifiée.  
  
## <a name="remarks"></a>Remarques  

 Le tableau suivant répertorie les GUID disponibles sur lesquels le `optionId` paramètre peut pointer et les valeurs valides correspondantes pour le `pValue` paramètre.  
  
|GUID|Description|`pValue` Parameter|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Contrôle les éléments dont les doublons sont vérifiés. Chaque fois que vous appelez une méthode [IMetaDataEmit](imetadataemit-interface.md) qui crée un nouvel élément, vous pouvez demander à la méthode de vérifier si l’élément existe déjà dans la portée actuelle. Par exemple, vous pouvez vérifier l’existence d' `mdMethodDef` éléments. dans ce cas, quand vous appelez [IMetaDataEmit ::D efinemethod](imetadataemit-definemethod-method.md), il vérifie que la méthode n’existe pas déjà dans l’étendue actuelle. Cette vérification utilise la clé qui identifie de façon unique une méthode donnée : le type de parent, le nom et la signature.|Doit être une variante de type UI4 et doit contenir une combinaison des valeurs de l’énumération [corcheckduplicatesfor,](corcheckduplicatesfor-enumeration.md) .|  
|MetaDataRefToDefCheck|Contrôle les éléments référencés qui sont convertis en définitions. Par défaut, le moteur de métadonnées optimise le code en convertissant un élément référencé en sa définition si l’élément référencé est réellement défini dans l’étendue actuelle.|Doit être une variante de type UI4 et doit contenir une combinaison des valeurs de l’énumération [CorRefToDefCheck,](correftodefcheck-enumeration.md) .|  
|MetaDataNotificationForTokenMovement|Contrôle les remappages de jetons qui se produisent pendant une fusion de métadonnées générer des rappels. Utilisez la méthode [IMetaDataEmit :: SetHandler](imetadataemit-sethandler-method.md) pour établir votre interface [IMapToken](imaptoken-interface.md) .|Doit être une variante de type UI4 et doit contenir une combinaison des valeurs de l’énumération [CorNotificationForTokenMovement,](cornotificationfortokenmovement-enumeration.md) .|  
|MetaDataSetENC|Contrôle le comportement de Edit-and-continue (ENC). Un seul mode de comportement peut être défini à la fois.|Doit être une variante de type UI4 et doit contenir une valeur de l’énumération [CorSetENC,](corsetenc-enumeration.md) . La valeur n’est pas un masque de masque.|  
|MetaDataErrorIfEmitOutOfOrder|Les contrôles qui génèrent des erreurs émises en désordre génèrent des rappels. L’émission de métadonnées dans le désordre n’est pas irrécupérable ; Toutefois, si vous émettez des métadonnées dans un ordre qui est favorisé par le moteur de métadonnées, les métadonnées sont plus compactes et peuvent donc être recherchées plus efficacement. Utilisez la `IMetaDataEmit::SetHandler` méthode pour établir votre interface [IMetaDataError](imetadataerror-interface.md) .|Doit être une variante de type UI4 et doit contenir une combinaison des valeurs de l’énumération [CorErrorIfEmitOutOfOrder,](corerrorifemitoutoforder-enumeration.md) .|  
|MetaDataImportOption|Contrôle les genres d’éléments qui ont été supprimés pendant l’extraction de ENC par un énumérateur.|Doit être une variante de type UI4 et doit contenir une combinaison des valeurs de l’énumération [corimportoptions,](corimportoptions-enumeration.md) .|  
|MetaDataThreadSafetyOptions|Contrôle si le moteur de métadonnées obtient des verrous de lecture/écriture, garantissant ainsi la sécurité des threads. Par défaut, le moteur suppose que l’accès est monothread par l’appelant, de sorte qu’aucun verrou n’est obtenu. Les clients sont chargés de maintenir la synchronisation de threads appropriée lors de l’utilisation de l’API de métadonnées.|Doit être une variante de type UI4 et doit contenir une valeur de l’énumération [CorThreadSafetyOptions,](corthreadsafetyoptions-enumeration.md) . La valeur n’est pas un masque de masque.|  
|MetaDataGenerateTCEAdapters|Contrôle si l’importateur de bibliothèques de types doit générer les adaptateurs d’événements (TCE) étroitement couplés pour les conteneurs de points de connexion COM.|Doit être une variante de type BOOL. Si `pValue` a la valeur `true` , l’importateur de bibliothèques de types génère les adaptateurs TCE.|  
|MetaDataTypeLibImportNamespace|Spécifie un espace de noms non défini par défaut pour la bibliothèque de types importée.|Il doit s’agir d’une valeur null ou d’un variant de type BSTR. Si `pValue` est une valeur null, l’espace de noms actuel a la valeur null ; dans le cas contraire, l’espace de noms actuel est défini sur la chaîne contenue dans le type BSTR de la variante.|  
|MetaDataLinkerOptions|Contrôle si l’éditeur de liens doit générer un assembly ou un fichier de module .NET Framework.|Doit être une variante de type UI4 et doit contenir une combinaison des valeurs de l’énumération [CorLinkerOptions,](corlinkeroptions-enumeration.md) .|  
|MetaDataRuntimeVersion|Spécifie la version de la common language runtime par rapport à laquelle cette image a été générée. La version est stockée sous forme de chaîne, telle que « v 1.0.3705 ».|Doit être une valeur null, une valeur VT_EMPTY ou un variant de type BSTR. Si `pValue` a la valeur null, la version du runtime est définie sur null. Si `pValue` est VT_EMPTY, la version est définie sur une valeur par défaut, qui est extraite de la version de Mscorwks.dll dans laquelle le code de métadonnées est en cours d’exécution. Dans le cas contraire, la version du runtime est définie sur la chaîne conservée dans le type BSTR de la variante.|  
|MetaDataMergerOptions|Spécifie les options de fusion des métadonnées.|Doit être une variante de type UI4 et doit contenir une combinaison des valeurs de l' `MergeFlags` énumération, qui est décrite dans le fichier corhdr. h.|  
|MetaDataPreserveLocalRefs|Désactive l’optimisation des références locales dans les définitions.|Doit contenir une combinaison des valeurs de l’énumération [corlocalrefpreservation,](corlocalrefpreservation-enumeration.md) .|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenserEx, interface](imetadatadispenserex-interface.md)
- [IMetaDataDispenser, interface](imetadatadispenser-interface.md)
