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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 324e30f6cbcaa1d1d81c7c03967dbb629d2cd6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742263"
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
|optAssemTitle|Chaîne - représente le titre de l’assembly.|  
|optAssemDescription|Chaîne - contient la description de l’assembly.|  
|optAssemConfig|Chaîne - contient la configuration de l’assembly.|  
|optAssemOS|Chaîne - encodée comme : « dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion ».|  
|optAssemProcessor|ULONG|  
|optAssemLocale|Chaîne - contient les paramètres régionaux d’assembly.|  
|optAssemVersion|Chaîne - encodée sous la forme : « Major.Minor.Build.Revision ».|  
|optAssemCompany|Chaîne - contient la société.|  
|optAssemProduct|Chaîne - contient le nom du produit.|  
|optAssemProductVersion|Chaîne (également appelé InformationalVersion).|  
|optAssemCopyright|Chaîne - contient les informations de copyright.|  
|optAssemTrademark|Chaîne - contient les informations de marque.|  
|optAssemKeyFile|String (nom de fichier).|  
|optAssemKeyName|Chaîne (le nom de clé).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (également appelé DelaySign).|  
|optAssemFileVersion|Chaîne - codée comme « Major.Minor.Build.Revision » - identique à la version de produit.|  
|optAssemSatelliteVer|Chaîne - encodée sous la forme « Major.Minor.Build.Revision ».|  
|optLastAssemOption|Un compteur du nombre d’éléments.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** alink.h  
  
 **Bibliothèque**: alink.dll  
  
## <a name="see-also"></a>Voir aussi

- [Al.exe (Assembly Linker)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
