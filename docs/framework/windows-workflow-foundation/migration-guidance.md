---
title: Conseils de migration
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 16f725dcb5d6f6e5d06771b7836fa187be005910
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559198"
---
# <a name="migration-guidance"></a>Conseils de migration

Dans le .NET Framework 4, Microsoft publie la deuxième version principale de Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)] a été publié dans WinFX (cela comprenait les types dans System. Workflow. \* namespaces ; désormais connu sous le nom de WF3) et amélioré dans .NET Framework 3,5. WF3 fait également partie du .NET Framework 4, mais il existe avec la nouvelle technologie de workflow (types dans System. Activities. \* namespaces, appelée WF4). Lorsque vous pensez au moment opportun d'adopter WF4, il est important de savoir tout d'abord que c'est vous qui décidez.  
  
- WF3 est une partie entièrement prise en charge du .NET Framework 4.  
  
- Les applications WF3 s’exécutent sur le .NET Framework 4 sans modification et continuent à être entièrement prises en charge.  
  
- De nouvelles applications WF3 peuvent être créées et vos applications existantes peuvent être modifiées dans Visual Studio 2012 et sont entièrement prises en charge.  
  
 Par conséquent, la décision d’adopter le .NET Framework 4 est dissociée de votre décision de passer à WF4 (System. Activities. \* ) à partir de WF3 (System. Workflow. \* ). Cette rubrique fournit des liens vers des conseils de migration WF qui fournissent des informations sur l'utilisation de WF3 et WF4.  
  
## <a name="wf-migration-white-papers-and-cookbooks"></a>Livres blancs et livres blancs sur la migration WF

 La rubrique [vue d’ensemble de la migration WF](/previous-versions/appfabric/ff383417(v=azure.10)) fournit une vue d’ensemble de la relation entre WF3 et WF4 et les stratégies de migration. Les rubriques d'accompagnement traitent de sujets spécifiques.  
  
 [WF Migration Overview](/previous-versions/appfabric/ff383417(v=azure.10))  
 Décrit la relation entre WF3 et WF4 ainsi que les choix dont vous disposez en tant qu'utilisateur ou qu'utilisateur potentiel de la technologie de workflow dans .NET 4.  
  
 [WF Migration: Best Practices for WF3 Development](/previous-versions/appfabric/ff383417(v=azure.10))  
 Explique comment concevoir des artefacts WF3 afin que leur migration vers WF4 soit plus facile.  
  
 [WF Guidance: Rules](/previous-versions/appfabric/ff383417(v=azure.10))  
 Explique comment faire progresser les investissements liés aux règles dans .NET Framework 4 solutions.  
  
 [WF Guidance: State Machine](/previous-versions/appfabric/ff383417(v=azure.10))  
 Explique la modélisation des flux de contrôle WF4 en l'absence d'une activité Ordinateur-État.  
  
 Notez que ces conseils s'appliquent uniquement aux projets de workflow qui ciblent le .NET Framework 4. Les workflows de machine à états ont été ajoutés dans le .NET 4.0.1 avec la mise en production de la mise à jour 1 de la plateforme, et ont été inclus dans le .NET Framework 4.5. Pour plus d’informations sur les workflows d’ordinateur d’État dans .NET 4.0.1-4.0.3 et .NET Framework 4,5, consultez [mise à jour d' 4.0.1 pour les fonctionnalités de Microsoft .NET Framework 4](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) et [flux de travail d’ordinateur d’État](state-machine-workflows.md).  
  
 [WF Migration Cookbook: Custom Activities](/previous-versions/appfabric/ff383417(v=azure.10))  
 Fournit des exemples et des instructions pour une nouvelle conception des activités personnalisées WF3 sur WF4.  
  
 [WF Migration Cookbook: Advanced Custom Activities](/previous-versions/appfabric/ff383417(v=azure.10))  
 Explique comment reconcevoir des activités personnalisées WF3 avancées qui utilisent les files d'attente WF3 et planifier des activités enfants en tant qu'activités personnalisées WF4.  
  
 [WF Migration Cookbook: Workflows](/previous-versions/appfabric/ff383417(v=azure.10))  
 Fournit des exemples et des instructions pour une nouvelle conception des workflows WF3 sur WF4.  
  
 [Livre de recettes sur la migration WF : Hébergement de workflow](/previous-versions/appfabric/ff383417(v=azure.10))  
 Explique comment reconcevoir code d'hébergement WF3 en tant que code d'hébergement WF4. L'objectif est de couvrir les principales différences de l'hébergement de workflow entre WF3 et WF4.  
  
 [WF Migration Cookbook: Workflow Tracking](/previous-versions/appfabric/ff383417(v=azure.10))  
 Explique comment reconcevoir le code et la configuration de suivi WF3 à l'aide du code et de la configuration de suivi équivalents WF4.  
  
 [WF Guidance: Workflow Services](/previous-versions/appfabric/ff383417(v=azure.10))  
 Fournit des instructions détaillées orientées exemple pour reconcevoir les workflows qui implémentent des services Web Windows Communication Foundation (WCF) (en général connus sous le nom de services de workflowl) créés dans WF3 de façon à utiliser WF4, pour les scénarios courants d'activités prédéfinies.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Statements.Interop>
