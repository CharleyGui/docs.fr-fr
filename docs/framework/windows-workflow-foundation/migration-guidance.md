---
title: Conseils de migration
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: b9b90aedc06fb4a4564596d61aa0ac2dc4c6143f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733592"
---
# <a name="migration-guidance"></a>Conseils de migration

Dans le .NET Framework 4, Microsoft publie la deuxième version principale de Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)] a été publié dans WinFX (cela comprenait les types dans System. Workflow. \* namespaces ; désormais connu sous le nom de WF3) et amélioré dans .NET Framework 3,5. WF3 fait également partie du .NET Framework 4, mais il existe avec la nouvelle technologie de workflow (types dans System. Activities. \* namespaces, appelée WF4). Lorsque vous pensez au moment opportun d'adopter WF4, il est important de savoir tout d'abord que c'est vous qui décidez.

- WF3 est une partie entièrement prise en charge du .NET Framework 4.

- Les applications WF3 s’exécutent sur le .NET Framework 4 sans modification et continuent à être entièrement prises en charge.

- De nouvelles applications WF3 peuvent être créées et vos applications existantes peuvent être modifiées dans Visual Studio 2012 et sont entièrement prises en charge.

 Par conséquent, la décision d’adopter le .NET Framework 4 est dissociée de votre décision de passer à WF4 (System. Activities. \* ) à partir de WF3 (System. Workflow. \* ). Cette rubrique fournit des liens vers des conseils de migration WF qui fournissent des informations sur l'utilisation de WF3 et WF4.

## <a name="wf-migration-white-papers-and-cookbooks"></a>Livres blancs et livres blancs sur la migration WF

 La rubrique [vue d’ensemble de la migration WF](/previous-versions/appfabric/ff383417(v=azure.10)) fournit une vue d’ensemble de la relation entre WF3 et WF4 et les stratégies de migration. Les rubriques d'accompagnement traitent de sujets spécifiques.

 [Vue d’ensemble de la migration WF](/previous-versions/appfabric/ff383417(v=azure.10)) Décrit la relation entre WF3 et WF4, ainsi que les choix dont vous disposez en tant qu’utilisateur ou en tant qu’utilisateur potentiel de la technologie de workflow dans .NET Framework 4.

 [Migration de WF : meilleures pratiques pour le développement de WF3](/previous-versions/appfabric/ff383417(v=azure.10)) Explique comment concevoir des artefacts WF3 pour qu’ils puissent être migrés plus facilement vers WF4.

 [Aide de WF : règles](/previous-versions/appfabric/ff383417(v=azure.10)) Explique comment faire progresser les investissements liés aux règles dans .NET Framework 4 solutions.

 [Aide WF : machine à États](/previous-versions/appfabric/ff383417(v=azure.10)) Décrit la modélisation de workflow de contrôle WF4 en l’absence d’une activité de State-Machine.

 Notez que ces conseils s'appliquent uniquement aux projets de workflow qui ciblent le .NET Framework 4. Les workflows d’ordinateur d’État ont été ajoutés à .NET Framework 4.0.1 avec la version de la mise à jour de plate-forme 1. ils ont été inclus dans le cadre de .NET Framework 4,5. Pour plus d’informations sur les workflows de machine à États dans .NET Framework 4.0.1-4.0.3 et .NET Framework 4,5, consultez [mettre à jour 4.0.1 pour les fonctionnalités de Microsoft .NET Framework 4](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) et les [flux de travail d’ordinateur d’État](state-machine-workflows.md).

 Livre de recettes sur la [migration WF : activités personnalisées](/previous-versions/appfabric/ff383417(v=azure.10)) Fournit des exemples et des instructions pour la reconception d’activités personnalisées WF3 sur WF4.

 Livre de recettes sur la [migration WF : activités personnalisées avancées](/previous-versions/appfabric/ff383417(v=azure.10)) Fournit des conseils pour la reconception d’activités personnalisées WF3 avancées qui utilisent des files d’attente WF3 et planifient des activités enfants comme des activités personnalisées WF4.

 Livre de recettes sur la [migration WF : workflows](/previous-versions/appfabric/ff383417(v=azure.10)) Fournit des exemples et des instructions pour la reconception des flux de travail WF3 sur WF4.

 Livre de recettes sur la [migration WF : Hébergement de workflow](/previous-versions/appfabric/ff383417(v=azure.10)) Fournit des conseils pour redéfinir le code d’hébergement WF3 comme code d’hébergement WF4. L'objectif est de couvrir les principales différences de l'hébergement de workflow entre WF3 et WF4.

 Livre de recettes sur la [migration WF : suivi de workflow](/previous-versions/appfabric/ff383417(v=azure.10)) Fournit des conseils pour la nouvelle conception du code de suivi WF3 et de la configuration à l’aide du code de suivi et de la configuration équivalents WF4.

 [Aide de WF : Workflow Services](/previous-versions/appfabric/ff383417(v=azure.10)) Fournit des instructions pas à pas orientées exemple pour la reconception de flux de travail qui implémentent des services Web Windows Communication Foundation (WCF) (communément appelés services de flux de travail) créés dans WF3 pour utiliser WF4, pour des scénarios courants pour les activités prêtes à l’emploi.

## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Statements.Interop>
