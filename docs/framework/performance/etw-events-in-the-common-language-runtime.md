---
title: Événements ETW dans le Common Language Runtime
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46ad58813da5b71b884ad55f796db3522b2f1920
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046611"
---
# <a name="etw-events-in-the-common-language-runtime"></a>Événements ETW dans le Common Language Runtime
Le CLR (Common Language Runtime) fournit des informations de diagnostic utiles pour le suivi d’événements pour Windows (ETW) par le biais d’une grande variété d’événements de débogage et de profilage. Les événements ETW du CLR tirent parti du système de suivi Windows (ETW) pour améliorer la prise en charge du profilage et du débogage déjà proposée par le common language runtime.  
  
 Vous trouverez des informations supplémentaires sur ETW dans l’article [Améliorez le débogage et l’optimisation des performances avec ETW](https://go.microsoft.com/fwlink/?LinkID=161142) sur MSDN. Des informations relatives à Xperf sont disponibles à la page [Windows Performance Toolkit - Xperf](https://go.microsoft.com/fwlink/?LinkID=161144) du blog NTDebugging.  
  
 Le .NET Framework 4 ou version ultérieure est requis pour tous les événements décrits dans les rubriques relatives aux événements. Le système d’exploitation Windows Vista est le client minimal pris en charge, et Windows Server 2008 est le serveur minimal pris en charge.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Contrôle de l’enregistrement .NET Framework](controlling-logging.md)  
 Décrit les outils et les commandes permettant de capturer et d’afficher des événements ETW.  
  
 [Fournisseurs ETW du CLR](clr-etw-providers.md)  
 Fournit des informations sur les fournisseurs d’arrêt et de runtime, et sur la façon de les utiliser pour collecter des données ETW.  
  
 [Niveaux et mots clés ETW du CLR](clr-etw-keywords-and-levels.md)  
 Décrit les mots clés pour les fournisseurs d’arrêt et de runtime qui permettent de filtrer des événements par catégorie.  
  
 [Événements ETW du CLR](clr-etw-events.md)  
 Fournit des informations détaillées sur les événements ETW du CLR, leurs mots clés, leurs niveaux et leurs données d’événement.  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW dans le .NET Framework](etw-events.md)
