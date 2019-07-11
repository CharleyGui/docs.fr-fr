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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6916e6344fe5c112b216ca753c372fa73a4d5af5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777701"
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption, méthode
Définit l’option spécifiée à une valeur donnée pour la portée de métadonnées actuelle. L’option contrôle la gestion des appels à la portée de métadonnées actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `optionId`  
 [in] Pointeur vers un GUID qui spécifie l’option à définir.  
  
 `pValue`  
 [in] La valeur à utiliser pour définir l’option. Le type de cette valeur doit être un variant de type de l’option spécifiée.  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant répertorie les GUID disponibles qui le `optionId` paramètre peut pointer vers et les valeurs valides correspondantes pour le `pValue` paramètre.  
  
|GUID|Description|`pValue` Paramètre|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Contrôle quels éléments sont activés pour les doublons. Chaque fois que vous appelez un [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) méthode qui crée un nouvel élément, vous pouvez demander à la méthode pour vérifier si l’élément existe déjà dans la portée actuelle. Par exemple, vous pouvez vérifier l’existence de `mdMethodDef` éléments ; dans ce cas, lorsque vous appelez [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), il vérifie que la méthode n’existe pas déjà dans la portée actuelle. Cette vérification utilise la clé qui identifie de façon unique une méthode donnée : parent de type, nom et signature.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) énumération.|  
|MetaDataRefToDefCheck|Contrôle quels éléments référencés est convertis en définitions. Par défaut, le moteur de métadonnées optimisera le code en convertissant un élément référencé à sa définition si l’élément référencé est défini dans la portée actuelle.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) énumération.|  
|MetaDataNotificationForTokenMovement|Contrôles quel jeton remappe qui se produisent pendant une fusion des métadonnées génèrent des rappels. Utilisez le [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) méthode pour établir votre [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) énumération.|  
|MetaDataSetENC|Contrôle le comportement de modifier et continuer (ENC). Qu’un seul mode de comportement peut être défini à la fois.|Doit être un variant de type UI4 et doit contenir une valeur de la [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) énumération. La valeur n’est pas un masque de bits.|  
|MetaDataErrorIfEmitOutOfOrder|Contrôles quelles erreurs émis--ordonnés génèrent des rappels. Émission de métadonnées en désordre n’est pas irrécupérable ; Toutefois, si vous émettez les métadonnées dans un ordre préconisé par le moteur de métadonnées, les métadonnées sont plus compacte et par conséquent peuvent être recherchée plus efficacement. Utilisez le `IMetaDataEmit::SetHandler` méthode pour établir votre [IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) interface.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) énumération.|  
|MetaDataImportOption|Contrôle quels types d’éléments qui ont été supprimés pendant un ENC sont récupérés par un énumérateur.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorImportOptions, énumération](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) énumération.|  
|MetaDataThreadSafetyOptions|Contrôle si le moteur de métadonnées obtient des verrous, ce qui garantit la sécurité des threads lecteur/enregistreur. Par défaut, le moteur suppose que l’accès est monothread par l’appelant, donc aucun verrou n’est obtenues. Les clients sont chargés de gérer la synchronisation des threads appropriée lors de l’utilisation de l’API de métadonnées.|Doit être un variant de type UI4 et doit contenir une valeur de la [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) énumération. La valeur n’est pas un masque de bits.|  
|MetaDataGenerateTCEAdapters|Contrôle si l’importateur de bibliothèques doit générer les adaptateurs d’événements fortement couplés (TCE) pour les conteneurs de point de connexion COM.|Doit être un variant de type BOOL. Si `pValue` a la valeur `true`, l’importateur de bibliothèques génère les adaptateurs TCE.|  
|MetaDataTypeLibImportNamespace|Spécifie un espace de noms non définis par défaut pour la bibliothèque de types qui est en cours d’importation.|Doit être une valeur null ou un variant de type BSTR. Si `pValue` est une valeur null, l’espace de noms actuel est défini à null ; sinon, l’espace de noms actuel est défini sur la chaîne qui est conservée dans le type du variant BSTR.|  
|MetaDataLinkerOptions|Contrôle si l’éditeur de liens doit générer un assembly ou un fichier de module .NET Framework.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) énumération.|  
|MetaDataRuntimeVersion|Spécifie la version du common language runtime sur laquelle cette image a été générée. La version est stockée sous forme de chaîne, telles que « v1.0.3705 ».|Doit être une valeur null, une valeur VT_EMPTY ou un variant de type BSTR. Si `pValue` est null, la version du runtime est définie avec la valeur null. Si `pValue` est VT_EMPTY, la version est définie sur une valeur par défaut, qui est dessinée à partir de la version de Mscorwks.dll dans laquelle le code de métadonnées est en cours d’exécution. Sinon, la version du runtime est définie à la chaîne qui est conservée dans le type du variant BSTR.|  
|MetaDataMergerOptions|Spécifie les options de fusion des métadonnées.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la `MergeFlags` énumération, qui est décrite dans le fichier CorHdr.h.|  
|MetaDataPreserveLocalRefs|Désactive l’optimisation des références locales dans des définitions.|Doit contenir une combinaison des valeurs de la [CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) énumération.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateforme :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenserEx, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
