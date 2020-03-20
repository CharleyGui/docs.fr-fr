---
title: Événements ETW de chargeur
ms.date: 03/30/2017
helpviewer_keywords:
- loader events [.NET Framework]
- ETW, loader events (CLR)
ms.assetid: cb403cc6-56f8-4609-b467-cdfa09f07909
ms.openlocfilehash: 0f8f96cf73882ef6556e5b9e64cf9adf389a2318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180562"
---
# <a name="loader-etw-events"></a>Événements ETW de chargeur
Ces événements collectent des informations relatives au chargement et déchargement des domaines d'application, des assemblys et des modules.  
  
 Tous les événements de chargeur sont déclenchés sous le mot clé `LoaderKeyword` (0x8). Les événements `DCStart` et `DCEnd` sont déclenchés sous `LoaderRundownKeyword` (0x8) avec `StartRundown`/`EndRundown` activé. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  

## <a name="application-domain-events"></a>Événements de domaine d'application
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Événement|Level|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AppDomainLoad_V1` et `AppDomainUnLoad_V1`|Informatif (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AppDomainDCStart_V1`|Informatif (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AppDomainDCEnd_V1`|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Description|  
|-----------|--------------|-----------------|  
|`AppDomainLoad_V1` (journalisé pour tous les domaines d'application)|156|Déclenché chaque fois qu'un domaine d'application est créé pendant la durée de vie d'un processus.|  
|`AppDomainUnLoad_V1`|157|Déclenché chaque fois qu'un domaine d'application est détruit pendant la durée de vie d'un processus.|  
|`AppDomainDCStart_V1`|157|Énumère les domaines d'application pendant un arrêt de début.|  
|`AppDomainDCEnd_V1`|158|Énumère les domaines d'application pendant un arrêt de fin.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identificateur unique d’un domaine d'application.|  
|AppDomainFlags|win:UInt32|0x1 : domaine par défaut.<br /><br /> 0x2 : exécutable.<br /><br /> 0x4 : domaine d'application, bit 28-31 : partage de la stratégie de ce domaine.<br /><br /> 0 : domaine partagé.|  
|AppDomainName|win:UnicodeString|Nom convivial du domaine d'application. Peut changer pendant la durée de vie du processus.|  
|AppDomainIndex|win:UInt32|Index de ce domaine d'application.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  

## <a name="clr-loader-assembly-events"></a>Événements d'assembly de chargeur du CLR  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Événement|Level|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`AssemblyLoad` et `AssemblyUnload`|Informatif (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`AssemblyDCStart`|Informatif (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`AssemblyDCEnd`|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Description|  
|-----------|--------------|-----------------|  
|`AssemblyLoad_V1`|154|Déclenché quand un assembly est chargé.|  
|`AssemblyUnload_V1`|155|Déclenché quand un assembly est déchargé.|  
|`AssemblyDCStart_V1`|155|Énumère les assemblys pendant un arrêt de début.|  
|`AssemblyDCEnd_V1`|156|Énumère les assemblys pendant un arrêt de fin.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|AssemblyID|win:UInt64|ID unique de l'assembly.|  
|AppDomainID|win:UInt64|ID du domaine de cet assembly.|  
|BindingID|win:UInt64|ID qui identifie de façon unique la liaison d'assembly.|  
|AssemblyFlags|win:UInt32|0x1 : assembly indépendant du domaine.<br /><br /> 0x2 : assembly dynamique.<br /><br /> 0x4 : l’assembly possède une image native.<br /><br /> 0x8 : assembly pouvant être collecté.|  
|AssemblyName|win:UnicodeString|Nom qualifié complet de l'assembly.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="module-events"></a>Événements de module
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Événement|Level|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`ModuleLoad_V2` et `ModuleUnload_V2`|Informatif (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`ModuleDCStart_V2`|Informatif (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`ModuleDCEnd_V2`|Informatif (4)|  
||||  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Description|  
|-----------|--------------|-----------------|  
|`ModuleLoad_V2`|152|Déclenché quand un module est chargé pendant la durée de vie d'un processus.|  
|`ModuleUnload_V2`|153|Déclenché quand un module est déchargé pendant la durée de vie d'un processus.|  
|`ModuleDCStart_V2`|153|Énumère les modules pendant un arrêt de début.|  
|`ModuleDCEnd_V2`|154|Énumère les modules pendant un arrêt de fin.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt64|ID unique du module.|  
|AssemblyID|win:UInt64|ID de l'assembly dans lequel ce module réside.|  
|ModuleFlags|win:UInt32|0x1 : module indépendant du domaine.<br /><br /> 0x2 : le module possède une image native.<br /><br /> 0x4 : module dynamique.<br /><br /> 0x8 : module de manifeste.|  
|Reserved1|win:UInt32|Champ réservé.|  
|ModuleILPath|win:UnicodeString|Chemin d'accès de l'image MSIL (Microsoft Intermediate Language) du module ou nom du module dynamique s'il s'agit d'un assembly dynamique (se terminant par null).|  
|ModuleNativePath|win:UnicodeString|Chemin d'accès de l'image native du module, si elle est présente (se terminant par null).|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
|ManagedPdbSignature|win:GUID|Signature GUID de la base de données du programme géré (PDB) qui correspond à ce module. (Consultez la section Notes.)|  
|ManagedPdbAge|win:UInt32|Nombre relatif à l’âge écrit sur le fichier PDB managé qui correspond à ce module. (Consultez la section Notes.)|  
|ManagedPdbBuildPath|win:UnicodeString|Chemin d'accès à l'emplacement où le fichier PDB managé qui correspond à ce module a été créé. Dans certains cas, cela peut simplement être un nom de fichier. (Consultez la section Notes.)|  
|NativePdbSignature|win:GUID|Signature GUID du fichier PDB de Native Image Generator (NGen) correspondant à ce module, le cas échéant. (Consultez la section Notes.)|  
|NativePdbAge|win:UInt32|Nombre relatif à l’âge écrit dans le fichier PDB NGen qui correspond à ce module, le cas échéant. (Consultez la section Notes.)|  
|NativePdbBuildPath|win:UnicodeString|Chemin d'accès à l'emplacement où le fichier PDB NGen qui correspond à ce module a été créé, le cas échéant. Dans certains cas, cela peut simplement être un nom de fichier. (Consultez la section Notes.)|  
  
### <a name="remarks"></a>Notes   
  
- Les champs dont le nom contient « Pdb » peuvent être utilisés par les outils de profilage pour localiser les fichiers PDB qui correspondent aux modules qui ont été chargés au cours de la session de profilage. Les valeurs de ces champs correspondent aux données écrites dans les sections IMAGE_DIRECTORY_ENTRY_DEBUG du module normalement utilisé par les débogueurs pour favoriser la localisation des fichiers PDB qui correspondent aux modules chargés.  
  
- Les noms de champ qui commencent par « ManagedPdb » font référence au fichier PDB managé correspondant au module MSIL qui a été généré par le compilateur managé (tels que le compilateur C# ou Visual Basic). Ce fichier PDB utilise le format de fichier PDB managé et décrit comment les éléments issus du code source managé d'origine, tels que les fichiers, les numéros de lignes et les noms de symboles, correspondent aux éléments MSIL qui sont compilés dans le module MSIL.  
  
- Les noms de champs qui commencent par « NativePdb » font référence au fichier PDB NGen généré par l'appel à `NGEN createPDB`. Ce fichier PDB utilise le format de fichier PDB natif et décrit comment les éléments issus du code source managé d'origine, tels que les fichiers, les numéros de lignes et les noms de symboles sont mappés aux éléments natifs qui sont compilés dans le module NGen.  

## <a name="clr-domain-module-events"></a>Événements de module de domaine du CLR
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Événement|Level|  
|-----------------------------------|-----------|-----------|  
|`LoaderKeyword` (0x8)|`DomainModuleLoad_V1`|Informatif (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `StartRundownKeyword`|`DomainModuleDCStart_V1`|Informatif (4)|  
|`LoaderRundownKeyword` (0x8) +<br /><br /> `EndRundownKeyword`|`DomainModuleDCEnd_V1`|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Description|  
|-----------|--------------|-----------------|  
|`DomainModuleLoad_V1`|151|Déclenché quand un module est chargé pour un domaine d'application.|  
|`DomainModuleDCStart_V1`|151|Énumère les modules chargés pour un domaine d'application pendant un arrêt de début, et est consigné pour tous les domaines d'application.|  
|`DomainModuleDCEnd_V1`|152|Énumère les modules chargés pour un domaine d'application pendant un arrêt de fin, et est consigné pour tous les domaines d'application.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ModuleID|win:UInt64|Identifie l'assembly auquel ce module appartient.|  
|AssemblyID|win:UInt64|ID de l'assembly dans lequel ce module réside.|  
|AppDomainID|win:UInt64|ID du domaine d'application dans lequel ce module est utilisé.|  
|ModuleFlags|win:UInt32|0x1 : module indépendant du domaine.<br /><br /> 0x2 : le module possède une image native.<br /><br /> 0x4 : module dynamique.<br /><br /> 0x8 : module de manifeste.|  
|Reserved1|win:UInt32|Champ réservé.|  
|ModuleILPath|win:UnicodeString|Chemin d'accès de l'image MSIL pour le module, ou nom du module dynamique s'il s'agit d'un assembly dynamique (se terminant par null).|  
|ModuleNativePath|win:UnicodeString|Chemin d'accès de l'image native du module, si elle est présente (se terminant par null).|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  

## <a name="module-range-events"></a>Événements de plage de module
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Événement|Level|  
|-----------------------------------|-----------|-----------|  
|`PerfTrackKeyWord`)|`ModuleRange`|Informatif (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCStart`|Informatif (4)|  
|`PerfTrackKeyWord`|`ModuleRangeDCEnd`|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Description|  
|-----------|--------------|-----------------|  
|`ModuleRange`|158|Cet événement est présent si une image Native Image Generator (NGen) chargée a été optimisée à l’aide d’IBC et contient des informations sur les sections à chaud de l'image NGen.|  
|`ModuleRangeDCStart`|160|Événement `ModuleRange` déclenché au début d'un arrêt.|  
|`ModuleRangeDCEnd`|161|Événement `ModuleRange` déclenché à la fin d'un arrêt.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win:UInt16|Identifie de façon unique une instance spécifique du CLR dans un processus si plusieurs instances du CLR sont chargées.|  
|ModuleID|win:UInt64|Identifie l'assembly auquel ce module appartient.|  
|RangeBegin|win:UInt32|Le décalage dans le module qui représente le début de la plage du type de plage spécifié.|  
|RangeSize|win:UInt32|Taille de la plage spécifiée en octets.|  
|RangeType|win:UInt32|Valeur unique, 0x4, représentant des plages IBC froides. Ce champ pourra représenter des valeurs supplémentaires dans le futur.|  
|RangeSize1|win:UInt32|0 indique des données incorrectes.|  
|RangeBegin2|win:UnicodeString||  
  
### <a name="remarks"></a>Notes   
 Si une image NGen chargée dans un processus du .NET Framework a été optimisée à l’aide d’IBC, l’événement `ModuleRange` qui contient les plages à chaud dans l'image NGen est consigné avec ses `moduleID` et `ClrInstanceID`.  Si l'image NGen n'est pas optimisée à l’aide d’IBC, cet événement n'est pas consigné. Pour déterminer le nom du module, cet événement doit être assemblé avec les événements ETW de chargement de module.  
  
 La taille de charge utile pour cet événement est variable. Le champ `Count` indique le nombre de décalages de plages contenus dans cet événement.  Cet événement doit être assemblé avec l’événement `IStart` de Windows afin de déterminer les plages réelles. L'événement de chargement d'image Windows est consigné chaque fois qu'une image est chargée, et il contient l'adresse virtuelle de l'image chargée.  
  
 Les événements de plage de module sont déclenchés sous n'importe quel niveau ETW supérieur ou égal à 4 et sont classés en tant qu'événements d'information.  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](clr-etw-events.md)
