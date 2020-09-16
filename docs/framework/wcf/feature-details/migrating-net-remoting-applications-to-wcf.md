---
title: Migration d'applications .NET Remoting vers WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 6233c603c30dbd021050caa2c5fd9c1849c80700
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546508"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migration d'applications .NET Remoting vers WCF
**Cette rubrique est spécifique à une technologie héritée qui est conservée pour la compatibilité descendante avec les applications existantes et n’est pas recommandée pour un nouveau développement. Les applications distribuées doivent maintenant être développées à l’aide de WCF.**  
  
 Il existe deux façons de tirer parti de WCF avec les applications .NET Remoting existantes : intégration et migration. L’intégration vous permet d’avoir .NET Remoting 2,0 et WCF s’exécutant côte à côte, ce qui vous permet d’exposer les mêmes objets métier sur les deux technologies simultanément, sans avoir à modifier votre code .NET Remoting .NET 2,0 Remoting existant. Pour l’intégration, vous devez exécuter sur .NET Framework 2,0 ou une version ultérieure. Si vous souhaitez tirer parti des fonctionnalités WCF et que vous n’avez pas besoin de la compatibilité des câbles avec les systèmes Remoting 2,0, vous pouvez migrer l’ensemble de votre service vers WCF. La migration de .NET Remoting 2,0 vers WCF nécessite des modifications de l’interface de l’objet distant et de ses paramètres de configuration. Ces deux rubriques sont abordées dans [la rubrique de la communication à distance au Windows Communication Foundation](/previous-versions/aa730857(v=vs.80)).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble conceptuelle](../conceptual-overview.md)
