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
ms.openlocfilehash: 5df95c6b5f91cd4f36bd03c1bd291f7a44025ee9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600090"
---
# <a name="administration-and-diagnostics"></a>Administration et diagnostics
Windows Communication Foundation (WCF) fournit un ensemble complet de fonctionnalités qui peuvent vous aider à surveiller les différentes étapes de la vie d’une application. Par exemple, utilisez la configuration pour installer les services et les clients lors du déploiement. WCF inclut un grand ensemble de compteurs de performances pour vous aider à mesurer les performances de votre application. WCF expose également les données d’inspection d’un service lors de l’exécution via un fournisseur de services WCF Windows Management Instrumentation (WMI). En cas de défaillance ou de fonctionnement incorrect de l'application, vous pouvez utiliser le journal des événements afin de vérifier si un événement significatif s'est produit. Vous pouvez également utiliser la journalisation des messages et le suivi pour afficher les événements qui se produisent sur l'ensemble de votre application. Ces fonctionnalités aident les développeurs et professionnels de l’informatique à résoudre les problèmes d’une application WCF lorsqu’il ne semble pas fonctionne correctement.  
  
> [!NOTE]
>  Si vous recevez des erreurs sans informations détaillées spécifiques, vous devez activer le `includeExceptionDetailInFaults` attribut de la [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) élément de configuration. Cela indique à WCF pour envoyer les détails de l’exception aux clients, qui vous permet de détecter les problèmes les plus courants sans nécessiter de diagnostic plus avancée. Pour plus d’informations, consultez [Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Fonctionnalités de diagnostic fournies par WCF  
 WCF fournit les fonctionnalités de diagnostic suivantes :  
  
- Le suivi de bout en bout fournit les données d'instrumentation permettant de dépanner une application sans utiliser de débogueur. WCF génère des suivis pour les jalons de processus, ainsi que les messages d’erreur. Cela peut inclure l'ouverture d'une fabrication de canal ou l'envoi et la réception de messages par un hôte de service. Le suivi peut être activé pour une application en cours d'exécution afin de surveiller sa progression. Pour plus d’informations, consultez le [suivi](../../../../docs/framework/wcf/diagnostics/tracing/index.md) rubrique. Pour comprendre comment vous pouvez utiliser le suivi pour déboguer votre application, consultez le [à l’aide de suivi pour résoudre les problèmes de votre Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) rubrique.  
  
- La journalisation des messages vous permet de voir la manière dont les messages se présentent à la fois avant et après la transmission. Pour plus d’informations, consultez le [Message Logging](../../../../docs/framework/wcf/diagnostics/message-logging.md) rubrique.  
  
- En cas de problèmes majeurs, le suivi écrit les événements dans le journal. L'observateur d'événements vous permet ensuite d'examiner les anomalies. Pour plus d’informations, consultez le [la consignation des événements](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) rubrique.  
  
- Les compteurs de performance exposés via l'analyseur de performances vous permettent de surveiller l'état de votre application et de votre système. Pour plus d’informations, consultez le [les compteurs de performances](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) rubrique.  
  
- L'espace de noms <xref:System.ServiceModel.Configuration> vous permet de charger des fichiers de configuration et de configurer un point de terminaison de service ou client. Vous pouvez utiliser le modèle objet pour modifier de nombreuses applications lorsque des mises à jour doivent être déployées sur un grand nombre d'ordinateurs. Vous pouvez également utiliser le [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) pour modifier les paramètres de configuration à l’aide d’un Assistant d’interface utilisateur. Pour plus d’informations, consultez le [configuration de votre Application](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) rubrique.  
  
- WMI vous permet d'identifier les services qui écoutent sur une machine, ainsi que les liaisons utilisées. Pour plus d’informations, consultez le [à l’aide de Windows Management Instrumentation pour les Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md) rubrique.  
  
 WCF fournit également plusieurs outils d’interface utilisateur graphique et ligne de commande pour le rendre plus facile à créer, déployer et gérer des applications WCF. Pour plus d’informations, consultez [outils Windows Communication Foundation](../../../../docs/framework/wcf/tools.md). Par exemple, vous pouvez utiliser la [l’outil Éditeur de Configuration (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) pour créer et modifier les paramètres de configuration WCF à l’aide d’un Assistant, au lieu de modifier XML directement. Vous pouvez également utiliser le [outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pour afficher, regrouper et filtrer les messages de trace afin que vous puissiez diagnostiquer, réparer et vérifier les problèmes avec les services WCF.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration de votre application](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
- [Déploiement de services](../../../../docs/framework/wcf/diagnostics/deploying-services.md)
- [Informations de référence sur les exceptions](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)
- [Journalisation des événements](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [Journalisation des messages](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Outil Éditeur de configuration (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [Outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Outil d’inscription ServiceModel](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)
- [Suivi](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Utilisation de Windows Management Instrumentation pour les diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md)
- [Compteurs de performance](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
- [Outils Windows Communication Foundation](../../../../docs/framework/wcf/tools.md)
