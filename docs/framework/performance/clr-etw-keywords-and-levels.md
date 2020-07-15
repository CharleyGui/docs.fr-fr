---
title: Niveaux et mots clés ETW du CLR
description: Passez en revue les mots clés et niveaux du suivi d’événements common language runtime (CLR) pour Windows (ETW). Les mots clés ETW du CLR d’événement permettent de filtrer les événements par catégorie.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
ms.openlocfilehash: dfbe047640a3a640cf37adeea6fa3656cfd9ec6d
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309675"
---
# <a name="clr-etw-keywords-and-levels"></a>Niveaux et mots clés ETW du CLR
Les événements de suivi d'événements pour Windows (ETW) peuvent être filtrés par catégorie et par niveau. Les [Mots clés ETW du CLR](#clr-etw-keywords) d’événement permettent de filtrer les événements par catégorie. Ils sont utilisés sous forme de combinaisons pour les fournisseurs d’arrêt et de runtime. Les [niveaux d'événement](#etw-event-levels) sont identifiés par des indicateurs.  
  
## <a name="clr-etw-keywords"></a>Mots clés ETW du CLR  
 Les mots clés sont des indicateurs qui peuvent être combinés pour générer des valeurs. Dans la pratique, vous utilisez les valeurs hexadécimales des mots clés au lieu de leurs noms lorsque vous appelez des utilitaires en ligne de commande.  
  
 Les mots clés sont décrits dans les tableaux suivants :  
  
- [Mots clés du runtime ETW du CLR](#runtime)  
  
- [Mots clés d’arrêt ETW du CLR](#rundown)  
  
- [Combinaisons de mots clés pour la résolution des symboles pour le fournisseur de Runtime](#runtime_combo)  
  
- [Combinaisons de mots clés pour la résolution des symboles pour le fournisseur d’arrêt](#rundown_combo)  
  
<a name="runtime"></a>
### <a name="clr-etw-runtime-keywords"></a>Mots clés de runtime ETW du CLR  
 Le tableau suivant répertorie les mots clés de runtime ETW du CLR, leurs valeurs et leur usage.  
  
|Nom du mot clé de runtime|Valeur|Objectif|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Active la collecte d' [événements de garbage collection](garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Active la collecte d’ [événements de chargeur](loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Active la collecte d’ [événements juste-à-temps (JIT)](jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Active la collecte d'événements pour les méthodes d'images natives (méthodes traitées par le générateur d'images natives, Ngen.exe) ; utilisé avec `StartEnumerationKeyword` et `EndEnumerationKeyword`. Ce mot clé possède une charge mémoire élevée. Il génère des événements pour chaque méthode à l'intérieur de chaque module NGen chargé. Si possible, au lieu d'utiliser ce mot clé, nous vous recommandons d'utiliser les bases de données de programme (PDB) générées par les outils de profilage pour récupérer des informations sur les méthodes à partir des modules NGen. Voir aussi `OverrideAndSuppressNGenEventsKeyword` plus bas dans ce tableau.|  
|`StartEnumerationKeyword`|0x00000040|Active l'énumération de toutes les méthodes dans le runtime ; utilisé conjointement à `NGenKeyword`.|  
|`EndEnumerationKeyword`|0x00000080|Active l'énumération de toutes les méthodes détruites dans le runtime ; utilisé conjointement à `JITKeyword` et `NGenKeyword`.|  
|`SecurityKeyword`|0x00000400|Active la collecte d’ [événements de sécurité](security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Active la collecte d'événements d’analyse de ressource au niveau d'un domaine d'application.|  
|`JITTracingKeyword`|0x00001000|Active la collecte d’ [événements de traçage JIT](jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Active la collecte d’ [événements d’interopérabilité](interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Active la collecte d’ [événements de conflit](contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Active la collecte d’ [événements d’exception](exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Active la collecte d’ [événements de pool de threads](thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(Disponible dans la .NET Framework 4,5 et versions ultérieures.) Supprime le mot clé de surcharge élevée `NGenKeyword` et empêche la génération d’événements pour les méthodes qui se trouvent dans les modules Ngen. À partir de la .NET Framework 4,5, les outils de profilage doivent utiliser `OverrideAndSuppressNGenEventsKeyword` et `NGenKeyword` ensemble pour supprimer la génération d’événements pour les méthodes dans les modules Ngen. Cela permet à l'outil de profilage d’utiliser les fichiers PDB NGen plus efficaces pour obtenir des informations sur les méthodes dans les modules NGen. Le CLR dans le .NET Framework 4 et versions antérieures ne prend pas en charge la création de fichiers PDB NGen. Dans les versions antérieures, le CLR ne reconnaîtra pas `OverrideAndSuppressNGenEventsKeyword` et traitera `NGenKeyword` pour générer des événements pour les méthodes dans les modules NGen.|  
|`PerfTrackKeyWord`|0x2000000|Active la collecte des événements `ModuleLoad` et `ModuleRange` .|  
|`StackKeyword`|0x40000000|Active la collecte des [événements de trace de la pile](stack-etw-event.md).|  
  
<a name="rundown"></a>
### <a name="clr-etw-rundown-keywords"></a>Mots clés d’arrêt ETW du CLR  
 Le tableau suivant répertorie les mots clés d’arrêt ETW du CLR, leurs valeurs et leur usage.  
  
|Nom du mot clé d’arrêt|Valeur|Objectif|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Active la collecte d’événements de chargeur quand il est utilisé avec `StartRundownKeyword` et `EndRundownKeyword`.|  
|`JitRundownKeyword`|0x00000010|Active la collecte des événements `DCStart` et `DCEnd` de méthode pour les méthodes compilées juste-à-temps (JIT) quand il est utilisé avec `StartRundownKeyword` et `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Active la collecte des événements `DCStart` et `DCEnd` de méthode pour les méthodes d’images natives NGen quand il est utilisé avec `StartRundownKeyword` et `EndRundownKeyword`. Ce mot clé possède une charge mémoire élevée. Il génère des événements pour chaque méthode à l'intérieur de chaque module NGen chargé. Si possible, au lieu d'utiliser ce mot clé, nous vous recommandons d'utiliser les bases de données de programme (PDB) générées par les outils de profilage pour récupérer des informations sur les méthodes à partir des modules NGen. Voir aussi `OverrideAndSuppressNGenEventsRundownKeyword` plus bas dans ce tableau.|  
|`StartRundownKeyword`|0x00000040|Active l'énumération de l'état du système pendant un arrêt de début.|  
|`EndRundownKeyword`|0x00000100|Active l'énumération de l'état du système pendant un arrêt de fin.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Active la collecte d'événements d'analyse de ressource à un niveau <xref:System.AppDomain> lorsqu'il est utilisé avec `StartRundownKeyword` ou `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|Active la collecte d’événements de pool de threads.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(Disponible dans la .NET Framework 4,5 et versions ultérieures.) Supprime le mot clé de surcharge élevée `NGenRundownKeyword` et empêche la génération d’événements pour les méthodes qui se trouvent dans les modules Ngen. À partir de la .NET Framework 4,5, les outils de profilage doivent utiliser `OverrideAndSuppressNGenEventsRundownKeyword` et `NGenRundownKeyword` ensemble pour supprimer la génération d’événements pour les méthodes dans les modules Ngen. Cela permet à l'outil de profilage d’utiliser les fichiers PDB NGen plus efficaces pour obtenir des informations sur les méthodes dans les modules NGen. Le CLR dans le .NET Framework 4 et versions antérieures ne prend pas en charge la création de fichiers PDB NGen. Dans les versions antérieures, le CLR ne reconnaîtra pas `OverrideAndSuppressNGenEventsRundownKeyword` et traitera `NGenRundownKeyword` pour générer des événements pour les méthodes dans les modules NGen.|  
|`PerfTrackKeyWord`|0x2000000|Active la collecte des événements `ModuleDCStart`, `ModuleDCEnd`, `ModuleRangeDCStart`et `ModuleRangeDCEnd` .|
  
<a name="runtime_combo"></a>
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Combinaisons de mots clés pour la résolution des symboles pour le fournisseur de runtime  
  
|Mots clés et indicateurs|Domaine d'application, assembly, événements de chargement/déchargement de module|Événements de chargement/déchargement de méthode (sauf événements dynamiques)|Événements de chargement/destruction de méthode dynamique|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Événements de chargement et déchargement.|Aucun.|Aucun.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` n'ajoute rien)|Aucun.|Événements de chargement.|Événements de chargement et déchargement.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Aucun.|Événements de chargement et déchargement.|Événements de chargement et déchargement.|  
|`NGenKeyword`|Aucun.|Aucun.|Non applicable.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Aucun.|Événements de chargement.|Non applicable.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Aucun.|Événements de déchargement.|Non applicable.|  
  
<a name="rundown_combo"></a>
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Combinaisons de mots clés pour la résolution des symboles pour le fournisseur d’arrêt  
  
|Mots clés et indicateurs|Domaine d'application, assembly, événements DCStart/DCEnd de module|Événements DCStart/DCEnd de méthode (y compris les événements de méthode dynamique)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|Événements`DCStart` .|Aucun.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|Événements`DCEnd` .|Aucun.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Aucun.|Événements`DCStart` .|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Aucun.|Événements`DCEnd` .|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Aucun.|Événements`DCStart` .|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Aucun.|Événements`DCEnd` .|  

## <a name="etw-event-levels"></a>Niveaux d'événement ETW  
 Les événements ETW peuvent également être filtrés par niveau. Si le niveau est défini sur 0x5, les événements de tous les niveaux, y compris 0x5 et inférieurs (qui sont des événements qui appartiennent aux catégories activées via des mots clés), sont déclenchés. Si le niveau est défini sur 0x2, seuls les événements de niveau 0x2 et inférieurs sont déclenchés.  
  
 Les niveaux ont les significations suivantes :  
  
 0x5 - Détaillé  
  
 0x4 - Informatif  
  
 0x3 - Avertissement  
  
 0x2 - Erreur  
  
 0x1 - Critique  
  
 0x0 - Toujours journaliser  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseurs ETW du CLR](clr-etw-providers.md)
- [Événements ETW du CLR](clr-etw-events.md)
- [Événements ETW dans le Common Language Runtime](etw-events-in-the-common-language-runtime.md)
