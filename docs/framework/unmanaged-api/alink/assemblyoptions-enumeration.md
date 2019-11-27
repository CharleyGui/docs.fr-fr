---
title: Énumération AssemblyOptions
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
ms.openlocfilehash: ed45e06297b77ea60304cdcfe1b08e97f9e4c085
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446591"
---
# <a name="assemblyoptions-enumeration"></a>Énumération AssemblyOptions
Énumère les options de l’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>Champs  
  
|Champ|Description|  
|-----------|-----------------|  
|optAssemTitle|String : représente le titre de l’assembly.|  
|optAssemDescription|Chaîne : contient la description de l’assembly.|  
|optAssemConfig|Chaîne : contient la configuration de l’assembly.|  
|optAssemOS|Encodée sous forme de chaîne comme : "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".|  
|optAssemProcessor|ULONG|  
|optAssemLocale|Chaîne : contient les paramètres régionaux de l’assembly.|  
|optAssemVersion|Encodée sous forme de chaîne comme : "major. minor. Build. Revision".|  
|optAssemCompany|Chaîne : contient la société.|  
|optAssemProduct|Chaîne : contient le nom du produit.|  
|optAssemProductVersion|Chaîne (également appelée InformationalVersion).|  
|optAssemCopyright|Chaîne : contient les informations de copyright.|  
|optAssemTrademark|Chaîne : contient les informations relatives à la marque.|  
|optAssemKeyFile|Chaîne (nom de fichier).|  
|optAssemKeyName|Chaîne (nom de la clé).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (également appelé DelaySign).|  
|optAssemFileVersion|Encodée sous forme de chaîne « major. minor. Build. Revision »--identique à ProductVersion.|  
|optAssemSatelliteVer|Encodée sous forme de chaîne « major. minor. Build. revision ».|  
|optLastAssemOption|Compteur du nombre d’éléments.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ALink. h  
  
 **Bibliothèque**: ALink. dll  
  
## <a name="see-also"></a>Voir aussi

- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
