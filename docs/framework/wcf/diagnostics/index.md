---
title: Administration et diagnostics
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
ms.openlocfilehash: 703724c3040f2508f011e002c22fa45dd3197884
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285562"
---
# <a name="administration-and-diagnostics"></a>Administration et diagnostics

Windows Communication Foundation (WCF) fournit un ensemble complet de fonctionnalités qui peuvent vous aider à surveiller les différentes étapes de la vie d’une application. Par exemple, utilisez la configuration pour installer les services et les clients lors du déploiement. WCF comprend un grand ensemble de compteurs de performances pour vous aider à évaluer les performances de votre application. WCF expose également les données d’inspection d’un service au moment de l’exécution via un fournisseur WMI (Windows Management Instrumentation WCF). En cas de défaillance ou de fonctionnement incorrect de l'application, vous pouvez utiliser le journal des événements afin de vérifier si un événement significatif s'est produit. Vous pouvez également utiliser la journalisation des messages et le suivi pour afficher les événements qui se produisent sur l'ensemble de votre application. Ces fonctionnalités permettent aux développeurs et aux professionnels de l’informatique de dépanner une application WCF lorsqu’elle ne se comporte pas correctement.  
  
> [!NOTE]
> Si vous recevez des erreurs sans informations détaillées spécifiques, vous devez activer l' `includeExceptionDetailInFaults` attribut de l' [\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) élément de configuration. Cela indique à WCF d’envoyer des détails d’exception aux clients, ce qui vous permet de détecter de nombreux problèmes courants sans nécessiter un diagnostic plus avancé. Pour plus d’informations, consultez [envoi et réception d’erreurs](../sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Fonctionnalités de diagnostic fournies par WCF  

 WCF fournit les fonctionnalités de diagnostic suivantes :  
  
- Le suivi de bout en bout fournit les données d'instrumentation permettant de dépanner une application sans utiliser de débogueur. WCF génère des suivis pour les jalons de processus, ainsi que des messages d’erreur. Cela peut inclure l'ouverture d'une fabrication de canal ou l'envoi et la réception de messages par un hôte de service. Le suivi peut être activé pour une application en cours d'exécution afin de surveiller sa progression. Pour plus d’informations, consultez la rubrique [traçage](./tracing/index.md) . Pour comprendre comment vous pouvez utiliser le suivi pour déboguer votre application, consultez la rubrique [utilisation du suivi pour résoudre les problèmes de votre application](./tracing/using-tracing-to-troubleshoot-your-application.md) .  
  
- La journalisation des messages vous permet de voir la manière dont les messages se présentent à la fois avant et après la transmission. Pour plus d’informations, consultez la rubrique [journalisation des messages](message-logging.md) .  
  
- En cas de problèmes majeurs, le suivi écrit les événements dans le journal. L'observateur d'événements vous permet ensuite d'examiner les anomalies. Pour plus d’informations, consultez la rubrique [journalisation des événements](./event-logging/index.md) .  
  
- Les compteurs de performance exposés via l'analyseur de performances vous permettent de surveiller l'état de votre application et de votre système. Pour plus d’informations, consultez la rubrique [compteurs de performance](./performance-counters/index.md) .  
  
- L'espace de noms <xref:System.ServiceModel.Configuration> vous permet de charger des fichiers de configuration et de configurer un point de terminaison de service ou client. Vous pouvez utiliser le modèle objet pour modifier de nombreuses applications lorsque des mises à jour doivent être déployées sur un grand nombre d'ordinateurs. Vous pouvez également utiliser l' [outil Éditeur de configuration (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) pour modifier les paramètres de configuration à l’aide d’un assistant d’interface utilisateur graphique. Pour plus d’informations, consultez la rubrique [configuration de votre application](configuring-your-application.md) .  
  
- WMI vous permet d'identifier les services qui écoutent sur une machine, ainsi que les liaisons utilisées. Pour plus d’informations, consultez la rubrique [utilisation de Windows Management Instrumentation pour les diagnostics](./wmi/index.md) .  
  
 WCF fournit également plusieurs outils d’interface graphique utilisateur et de ligne de commande pour faciliter la création, le déploiement et la gestion des applications WCF. Pour plus d’informations, consultez [Windows Communication Foundation Tools](../tools.md). Par exemple, vous pouvez utiliser l' [outil Éditeur de configuration (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md) pour créer et modifier les paramètres de configuration WCF à l’aide d’un Assistant, au lieu de modifier directement le code XML. Vous pouvez également utiliser l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) pour afficher, regrouper et filtrer les messages de trace afin de pouvoir diagnostiquer, réparer et vérifier les problèmes liés aux services WCF.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration de votre application](configuring-your-application.md)
- [Déploiement de services](deploying-services.md)
- [Informations de référence sur les exceptions](./exceptions-reference/index.md)
- [Journalisation des événements](./event-logging/index.md)
- [Journalisation des messages](message-logging.md)
- [Outil Éditeur de configuration (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [Outil d'inscription ServiceModel](servicemodel-registration-tool.md)
- [Suivi](./tracing/index.md)
- [Utilisation de Windows Management Instrumentation pour les Diagnostics](./wmi/index.md)
- [Compteurs de performance](./performance-counters/index.md)
- [Outils de Windows Communication Foundation](../tools.md)
