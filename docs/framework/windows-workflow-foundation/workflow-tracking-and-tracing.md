---
title: Suivi et traçage de workflow
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], tracking and tracing
ms.assetid: b965ded6-370a-483d-8790-f794f65b137e
ms.openlocfilehash: 88c4982d45c1a3c450afe0c199a1f8a376348262
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655656"
---
# <a name="workflow-tracking-and-tracing"></a>Suivi et traçage de workflow
Le suivi Windows Workflow est une fonctionnalité de [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] conçue pour offrir plus de visibilité lors de l’exécution de workflow. Il fournit une infrastructure de suivi pour suivre l'exécution d'une instance de workflow. L'infrastructure de suivi WF instrumente de façon transparente un workflow pour émettre des enregistrements qui reflètent des événements clés pendant l'exécution. Cette fonctionnalité est disponible par défaut pour tous les workflows [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Il n'est pas nécessaire de modifier un workflow [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] pour activer son suivi. Il suffit seulement de déterminer quelles données vous souhaitez obtenir. Lorsqu'une instance de workflow démarre ou se termine, les enregistrements de suivi de son exécution sont émis. Le suivi peut également extraire des données métier pertinentes associées aux variables de workflow. Par exemple, si le workflow représente un système de traitement des commandes, l'ID de commande peut être extrait avec l'objet <xref:System.Activities.Tracking.TrackingRecord>. En règle générale, le suivi WF facilite l'accès aux diagnostics ou aux analyses d'entreprise depuis l'exécution du workflow.  
  
 Ces composants de suivi sont équivalents au service de suivi dans [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]. Dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], les performances ont été améliorées et le modèle de programmation simplifié pour la fonctionnalité de suivi WF. L'exécution du suivi instrumente une instance de workflow pour émettre des événements associés au cycle de vie de workflow, aux activités de workflow et aux événements personnalisés.  
  
 Windows Server AppFabric permet également de surveiller l'exécution de WCF et des services de workflow. Pour plus d’informations, consultez [analyse de Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273) et [analyse des Applications avec Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=201287)  
  
 Pour résoudre les problèmes d'exécution de workflow, vous pouvez activer le suivi de workflow diagnostique. Pour plus d’informations, consultez [suivi de flux de travail](workflow-tracing.md).  
  
 Pour vous aider à comprendre le modèle de programmation, les principaux composants de l'infrastructure de suivi sont traités dans cette rubrique :  
  
- Des objets <xref:System.Activities.Tracking.TrackingRecord> sont émis par l'exécution du workflow. Pour plus d’informations, consultez [des enregistrements de suivi](tracking-records.md).  
  
- Les objets <xref:System.Activities.Tracking.TrackingParticipant>  s'abonnent aux objets <xref:System.Activities.Tracking.TrackingRecord>. Les participants de suivi contiennent la logique nécessaire pour traiter la charge utile des objets <xref:System.Activities.Tracking.TrackingRecord> (par exemple, ils peuvent choisir d'écrire dans un fichier). Pour plus d’informations, consultez [les participants au suivi](tracking-participants.md).  
  
- Les objets <xref:System.Activities.Tracking.TrackingProfile> filtrent les enregistrements de suivi émis par une instance de workflow. Pour plus d’informations, consultez [modèles de suivi](tracking-profiles.md).  
  
## <a name="workflow-tracking-infrastructure"></a>Infrastructure du suivi des flux de travail  
 L'infrastructure de suivi de workflow fonctionne sur un modèle Publier/Abonner. L’instance de workflow est le serveur de publication des enregistrements de suivi, alors que les abonnés des enregistrements de suivi sont inscrits en tant qu’extensions du workflow. Ces extensions qui s’abonnent aux objets <xref:System.Activities.Tracking.TrackingRecord> sont appelées des participants de suivi. Les participants de suivi sont des points d'extensibilité qui accèdent aux objets <xref:System.Activities.Tracking.TrackingRecord> afin de les traiter de la manière prévue. L'infrastructure de suivi permet l'application d'un filtre sur les enregistrements de suivi sortants pour permettre à un participant de s'abonner à un sous-ensemble des enregistrements. Ce mécanisme de filtrage s'effectue à l'aide d'un fichier modèle de suivi.  
  
 Une vue de haut niveau de l’infrastructure de suivi est indiquée dans l’illustration suivante :  
  
 ![Capture d’écran montrant l’infrastructure de suivi de flux de travail. ](./media/workflow-tracking-and-tracing/workflow-tracking-infrastructure.gif "WV")  
  
## <a name="in-this-section"></a>Dans cette section  
 [Enregistrements de suivi](tracking-records.md)  
 Décrit les enregistrements de suivi émis par l'exécution du workflow.  
  
 [Profils de suivi](tracking-profiles.md)  
 Explique l'utilisation des modèles de suivi.  
  
 [Participants de suivi](tracking-participants.md)  
 Décrit comment utiliser le participant de suivi fourni par le système ou comment créer des participants de suivi personnalisés.  
  
 [Configuration du suivi d’un workflow](configuring-tracking-for-a-workflow.md)  
 Décrit comment configurer le suivi pour un workflow.  
  
 [Suivi de workflow](workflow-tracing.md)  
 Décrit les deux méthodes d'activation du suivi de débogage pour un workflow.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi SQL](./samples/sql-tracking.md)
