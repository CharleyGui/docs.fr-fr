---
title: Processus d'embauche
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: baa6a48a5d16af9c325b47ba5e4c1fc3c820f786
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257208"
---
# <a name="hiring-process"></a>Processus d'embauche

Cet exemple montre comment implémenter un processus d'entreprise à l'aide d'activités de messagerie et de deux workflows hébergés en tant que services de workflow. Ces workflows font partie de l'infrastructure informatique d'une société fictive nommée Contoso, Inc.  
  
 Le processus de workflow `HiringRequest` (implémenté en tant que <xref:System.Activities.Statements.Flowchart>) demande l'autorisation de plusieurs responsables de la société. Pour atteindre cet objectif, le flux de travail utilise d’autres services existants de l’organisation (dans le cas présent, un service de boîte de réception et un service de données organisationnels mis en œuvre en tant que services simples Windows Communication Foundation (WCF)).  
  
 Le workflow `ResumeRequest` (implémenté en tant que <xref:System.Activities.Statements.Sequence>) publie une offre d’emploi sur le site web externe Careers de Contoso et gère l’acquisition de CV. Une offre d’emploi est disponible sur le site web externe pour une durée fixe (jusqu’à son expiration) ou jusqu’à ce qu’un employé de Contoso décide de la supprimer.  
  
 Cet exemple illustre les fonctionnalités suivantes de [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] :  
  
- Workflows <xref:System.Activities.Statements.Flowchart> et <xref:System.Activities.Statements.Sequence> pour la modélisation des processus d'entreprise.  
  
- Services de workflow.  
  
- Activités de messagerie  
  
- Corrélation basée sur le contenu  
  
- Activités personnalisées (déclaratives et basées sur le code)  
  
- Persistance SQL Server fournie par le système  
  
- <xref:System.Activities.Persistence.PersistenceParticipant> personnalisé  
  
- Suivi personnalisé  
  
- Suivi d'événements pour le suivi ETW Windows  
  
- Composition des activités  
  
- Activités <xref:System.Activities.Statements.Parallel>  
  
- Activité <xref:System.Activities.Statements.CancellationScope>  
  
- Minuteurs durables (activité <xref:System.Activities.Statements.Delay>)  
  
- Transactions  
  
- Plusieurs workflows dans la même solution  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Description du processus  

 Contoso, Inc. souhaite contrôler de près le nombre de salariés dans chacun de ses services. Par conséquent, à chaque fois qu'un employé démarre un nouveau processus d'embauche, il doit passer par une approbation du processus de demande d'embauche avant que le recrutement ait lieu. Ce processus est appelé demande de processus d'embauche (définie dans le projet HiringRequestService) et comprend les étapes suivantes :  
  
1. Un employé (le demandeur) démarre la demande de processus d'embauche.  
  
2. Le responsable du demandeur doit approuver la demande :  
  
    1. Le responsable peut refuser la demande.  
  
    2. Le responsable peut retourner la demande au demandeur pour obtenir des informations supplémentaires :  
  
        1. Le demandeur examine et renvoie la demande au responsable.  
  
    3. Le responsable peut approuver la demande.  
  
3. Une fois que le responsable du demandeur a approuvé, le propriétaire du service doit approuver la demande :  
  
    1. Le propriétaire du service peut la refuser.  
  
    2. Le propriétaire du service peut l'approuver.  
  
4. Une fois que le propriétaire du service a approuvé la demande, le processus nécessite l'approbation de deux responsables des Ressources Humaines ou du CEO :  
  
    1. Le processus peut passer à l'état Accepté ou Refusé.  
  
    2. Si le processus est Accepté, une nouvelle instance du workflow `ResumeRequest` démarre (`ResumeRequest` est lié à HiringRequest.csproj par le biais d'une référence de service).  
  
 Une fois que les responsables ont approuvé l'embauche d'un nouvel employé, les Ressources Humaines doivent rechercher le candidat approprié. Ce processus est effectué par le deuxième workflow (`ResumeRequest`, défini dans ResumeRequestService.csproj). Ce workflow définit le processus d'envoi d'une offre d'emploi avec opportunité de carrière au site Web externe Careers de Contoso, reçoit les CV des candidats et contrôle l'état de l'offre d'emploi. Les postes sont disponibles pour une durée fixe (jusqu'à l'expiration du délai) ou jusqu'à ce qu'un employé de Contoso décide de les supprimer. Le workflow `ResumeRequest` est composé des étapes suivantes :  
  
1. Un employé de Contoso saisit les informations sur le poste et une durée avant expiration. Une fois que l’employé a tapé ces informations, le poste est publié sur le site web Careers.  
  
2. Une fois les informations publiées, les parties intéressées peuvent envoyer leur CV. Lorsqu'un CV est envoyé, il est stocké dans un enregistrement associé à l'ouverture du poste.  
  
3. Les candidats peuvent envoyer leur CV jusqu'à ce que le délai expire ou qu'une personne du service Ressources Humaines de Contoso décide de supprimer l'offre en arrêtant le processus.  
  
## <a name="projects-in-the-sample"></a>Projets dans l'exemple  

 Le tableau suivant fournit les projets de l'exemple de solution.  
  
|Projet|Description|  
|-------------|-----------------|  
|ContosoHR|Contient des contrats de données, des objets métier et des classes de référentiel.|  
|HiringRequestService|Contient la définition du workflow Processus de demande d'embauche.<br /><br /> Ce projet est implémenté en tant qu'application console qui héberge automatiquement le workflow (fichier xaml) en tant service.|  
|ResumeRequestService|Service de workflow qui collecte les CV des candidats jusqu'à ce qu'un délai expire ou que quelqu'un décide que le processus doit être arrêté.<br /><br /> Ce projet est implémenté en tant que service de workflow déclaratif (xamlx).|  
|OrgService|Service qui expose les informations organisationnelles (Employees, Positions, PositionTypes et Departments). Ce service s'apparente au module Organigramme d'un projet ERP classique.<br /><br /> Ce projet est implémenté en tant qu’application console qui expose un service Windows Communication Foundation (WCF).|  
|InboxService|Boîte de réception qui contient des tâches interactives pour les employés.<br /><br /> Ce projet est implémenté en tant qu'application console qui expose un service WCF.|  
|InternalClient|Application Web pour l'interaction avec le processus. Les utilisateurs peuvent démarrer et afficher les workflows HiringProcess et y participer. Cette application leur permet également de démarrer et surveiller les processus ResumeRequest.<br /><br /> Ce site est implémenté de manière à se situer sur l'intranet de Contoso. Ce projet est implémenté en tant que site Web ASP.NET.|  
|CareersWebSite|Site web externe qui expose les postes ouverts chez Contoso. Les candidats potentiels peuvent accéder à ce site et envoyer un CV.|  
  
## <a name="feature-summary"></a>Résumé des fonctionnalités  

 Le tableau suivant décrit l’utilisation de chaque fonctionnalité de cet exemple.  
  
|Fonctionnalité|Description|Project|  
|-------------|-----------------|-------------|  
|Organigramme|Le processus métier est représenté par un organigramme. La description de cet organigramme représente le processus de la même façon que s'il était dessiné sur un tableau blanc.|HiringRequestService|  
|Services de workflow|L’organigramme et la définition de processus sont hébergés dans un service (dans cet exemple, le service est hébergé dans une application console).|HiringRequestService|  
|Activités de messagerie|L'organigramme utilise les activités de messagerie de deux façons :<br /><br /> -Pour obtenir des informations de l’utilisateur (pour recevoir les décisions et les informations associées dans chaque étape d’approbation).<br />-Pour interagir avec d’autres services existants (InboxService et OrgDataService, utilisés par le biais de références de service).|HiringRequestService|  
|Corrélation basée sur le contenu|Les messages d'approbation sont mis en corrélation avec la propriété ID de la demande d'embauche :<br /><br /> -Quand un processus est démarré, le descripteur de corrélation est initialisé avec l’ID de la demande.<br />-Les messages d’approbation entrants sont corrélés sur leur ID (le premier paramètre de chaque message d’approbation est l’ID de la demande).|HiringRequestService / ResumeRequestService|  
|Activités personnalisées (déclaratives et basées sur le code)|Cet exemple contient plusieurs activités personnalisées :<br /><br /> -   `SaveActionTracking`: Cette activité émet un personnalisé <xref:System.Activities.Tracking.TrackingRecord> (à l’aide de <xref:System.Activities.NativeActivityContext.Track%2A> ). Elle a été créée à l'aide de code impératif qui étend <xref:System.Activities.NativeActivity>.<br />-   `GetEmployeesByPositionTypes`: Cette activité reçoit une liste d’ID de type de position et retourne une liste des personnes qui ont cette position dans contoso. Cette activité a été créée à l'aide de code déclaratif (à l'aide du concepteur d'activités).<br />-   `SaveHiringRequestInfo`: Cette activité enregistre les informations d’un `HiringRequest` (à l’aide de `HiringRequestRepository.Save` ). Elle a été créée à l'aide de code impératif qui étend <xref:System.Activities.CodeActivity>.|HiringRequestService|  
|Persistance SQL Server fournie par le système|L’instance <xref:System.ServiceModel.Activities.WorkflowServiceHost> qui héberge la définition de processus Flowchart est configurée pour utiliser la persistance SQL Server fournie par le système.|HiringRequestService / ResumeRequestService|  
|Suivi personnalisé|L'exemple comprend un participant de suivi personnalisé qui enregistre l'historique d'un `HiringRequestProcess` (enregistre l'action effectuée, par qui et à quel moment). Le code source se trouve dans le dossier Tracking de HiringRequestService.|HiringRequestService|  
|Suivi ETW|Le suivi ETW fourni par le système est configuré dans le fichier App.config du service HiringRequestService.|HiringRequestService|  
|Composition des activités|La définition de processus utilise la composition libre de <xref:System.Activities.Activity>. L'Organigramme contient plusieurs activités de séquence et parallèles qui contiennent simultanément d'autres activités (et ainsi de suite).|HiringRequestService|  
|Activités parallèles|-   <xref:System.Activities.Statements.ParallelForEach%601> est utilisé pour s’inscrire dans la boîte de réception des responsables du PDG et des RH en parallèle (en attente de l’étape d’approbation de deux responsables des ressources humaines).<br />-   <xref:System.Activities.Statements.Parallel> permet d’effectuer des tâches de nettoyage dans les étapes terminées et rejetées.|HiringRequestService|  
|Annulation de modèle|L'organigramme utilise <xref:System.Activities.Statements.CancellationScope> pour créer le comportement d'annulation (dans ce cas, pour procéder à un nettoyage).|HiringRequestService|  
|Participant de persistance client|`HiringRequestPersistenceParticipant` enregistre les données d'une variable de workflow dans une table stockée dans la base de données des Ressources Humaines de Contoso.|HiringRequestService|  
|Services de workflow|`ResumeRequestService` est implémenté à l'aide de services de workflow. La définition de workflow et les informations de service sont contenues dans ResumeRequestService. xamlx. Le service est configuré pour utiliser la persistance et le suivi.|ResumeRequestService|  
|Minuteurs durables|`ResumeRequestService` utilise des minuteurs durables pour définir la durée de validité d'une offre d'emploi (une fois le délai arrivé à expiration, l'offre d'emploi est fermée).|ResumeRequestService|  
|Transactions|<xref:System.Activities.Statements.TransactionScope> est utilisé pour garantir la cohérence des données lors de l'exécution de plusieurs activités (lors de la réception d'un nouveau CV).|ResumeRequestService|  
|Transactions|Le participant de persistance personnalisé (`HiringRequestPersistenceParticipant`) et le participant de suivi personnalisé (`HistoryFileTrackingParticipant`) utilisent la même transaction.|HiringRequestService|  
|Utilisation [!INCLUDE[wf1](../../../../includes/wf1-md.md)] dans les applications ASP.net.|Les flux de travail sont accessibles à partir de deux applications ASP.NET.|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>Stockage des données  

 Les données sont stockées dans une base de données SQL Server nommée `ContosoHR` (le script pour créer cette base de données se trouve dans le dossier `DbSetup`). Les instances de workflow sont stockées dans une base de données SQL Server nommée `InstanceStore` (les scripts pour créer le magasin d'instances font partie de la distribution [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]).  
  
 Les deux bases de données sont créées en exécutant le script Setup. cmd à partir d’un Invite de commandes développeur pour Visual Studio.  
  
## <a name="running-the-sample"></a>Exécution de l’exemple  
  
#### <a name="to-create-the-databases"></a>Pour créer les bases de données  
  
1. Ouvrez une Invite de commandes développeur pour Visual Studio.  
  
2. Accédez à l’exemple de dossier.  
  
3. Exécutez Setup.cmd.  
  
4. Vérifiez que les deux bases de données `ContosoHR` et `InstanceStore` ont été créées dans SQL Express.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Pour configurer la solution en vue de l'exécution  
  
1. Exécutez Visual Studio en tant qu’administrateur. Ouvrez HiringRequest.sln.  
  
2. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur la solution, puis sélectionnez **Propriétés**.  
  
3. Sélectionnez l’option **plusieurs projets de démarrage** et définissez **CareersWebSite**, **InternalClient**, **HiringRequestService** et **ResumeRequestService** sur **Start**. Laissez **ContosoHR**, **InboxService** et **OrgService** comme None.  
  
4. Générez la solution en appuyant sur Ctrl+Maj+B. Assurez-vous que la génération a réussi.  
  
#### <a name="to-run-the-solution"></a>Pour exécuter la solution  
  
1. Une fois la solution générée, appuyez sur Ctrl+F5 pour une exécution sans débogage. Vérifiez que les services ont démarré.  
  
2. Cliquez avec le bouton droit sur **InternalClient** dans la solution, puis sélectionnez **afficher dans le navigateur**. La page par défaut pour `InternalClient` s'affiche. Assurez-vous que les services s'exécutent, puis cliquez sur le lien.  
  
3. Le module **HiringRequest** est affiché. Vous pouvez suivre le scénario détaillé ici.  
  
4. Une fois `HiringRequest` terminé, vous pouvez démarrer `ResumeRequest`. Vous pouvez suivre le scénario détaillé ici.  
  
5. Si `ResumeRequest` est publié, il est disponible sur le site web public (site web Careers de Contoso). Pour afficher l’offre d’emploi (et postuler pour le poste), accédez au site web Careers.  
  
6. Cliquez avec le bouton droit sur **CareersWebSite** dans la solution, puis sélectionnez **afficher dans le navigateur**.  
  
7. Revenez à la `InternalClient` en cliquant avec le bouton droit sur **InternalClient** dans la solution et en sélectionnant **afficher dans le navigateur**.  
  
8. Accédez à la section **jobpostings** en cliquant sur le lien **postes de travail** dans le menu supérieur de la boîte de réception. Vous pouvez suivre le scénario détaillé ici.  
  
## <a name="scenarios"></a>Scénarios  
  
### <a name="hiring-request"></a>Demande d'embauche  
  
1. Michael Alexander (Software Engineer) souhaite demander la création d'un poste dans le service Engineering pour embaucher un Software Engineer in Test (SDET) disposant au moins de trois ans d'expérience en C#.  
  
2. Une fois créée, la demande apparaît dans la boîte de réception de Michael (cliquez sur **Actualiser** si vous ne voyez pas la demande) en attendant l’approbation de Peter Brehm, qui est le responsable de Michael.  
  
3. Peter souhaite agir sur la demande de Michael. Il pense que le poste exige cinq ans d'expérience en C# plutôt que trois. Il renvoie donc son commentaire pour révision.  
  
4. Michael voit un message dans sa boîte de réception de son responsable et souhaite agir. Michael voit l’historique de la demande de position et accepte Peter. Michael modifie la description pour exiger cinq ans d'expérience en C#, puis il accepte la modification.  
  
5. Peter agit sur la demande modifiée de Michael et l’accepte. La demande doit désormais être approuvée par le Director of Engineering, Tsvi Reiter.  
  
6. Tsvi Reiter souhaite accélérer la demande. Il entre donc un commentaire indiquant qu'elle est urgente et l'accepte.  
  
7. La demande doit désormais être approuvée par deux responsables des Ressources Humaines ou le CEO. Le CEO, Brian Richard Goldstein, voit la demande urgente de Tsvi. Il traite la demande en l'acceptant, et ce faisant il passe outre le processus normal qui exige que la demande soit approuvée par deux responsables des Ressources Humaines.  
  
8. La demande est supprimée de la boîte de réception de Michael et le processus d’embauche d’un SDET a maintenant commencé.  
  
### <a name="start-resume-request"></a>Commencer la demande de CV  
  
1. À présent, le poste est en attente de publication sur un site Web externe où les gens peuvent s’appliquer (vous pouvez le voir en cliquant sur le lien **postes de travail** ). Maintenant, le poste est en cours d'examen par un représentant des Ressources Humaines chargé de sa finalisation et de sa publication.  
  
2. HR souhaite modifier cette position de travail (en cliquant sur le lien **modifier** ) en définissant un délai d’expiration de 60 minutes (en réalité, il peut s’agir de jours ou de semaines). Le délai d’expiration permet de supprimer le poste du site web externe en fonction de la durée spécifiée.  
  
3. Une fois que vous avez enregistré la position du travail modifié, elle apparaît sous l’onglet **CV de réception** (actualisez la page Web pour afficher la nouvelle position du travail).  
  
### <a name="collecting-resumes"></a>Collecte de CV  
  
1. Le poste doit apparaître sur le site web externe. Si vous êtes intéressé par ce poste, vous pouvez postuler et envoyer votre CV.  
  
2. Si vous revenez au service de liste des postes de travail, vous pouvez « afficher les CV » qui ont été collectés jusqu’à présent.  
  
3. Les Ressources Humaines peuvent aussi arrêter la collecte de CV (par exemple, une fois que le candidat approprié a été identifié).  
  
## <a name="troubleshooting"></a>Dépannage  
  
1. Vérifiez que vous exécutez Visual Studio avec des privilèges d’administrateur.  
  
2. En cas d'échec de la génération de la solution, vérifiez les points suivants :  
  
    - La référence à `ContosoHR` n’est pas absente des `InternalClient` `CareersWebSite` projets ou.  
  
3. En cas d'échec de l'exécution de la solution, vérifiez les points suivants :  
  
    1. Tous les services s'exécutent.  
  
    2. Les références de service sont mises à jour.  
  
        1. Ouvrez le dossier App_WebReferences.  
  
        2. Cliquez avec le bouton droit sur **contoso** et sélectionnez **mettre à jour les références Web/de service**.  
  
        3. Régénérez la solution en appuyant sur CTRL + MAJ + B dans Visual Studio.  
  
## <a name="uninstalling"></a>Désinstallation  
  
1. Supprimez le magasin d’instances SQL Server en exécutant Cleanup.bat, situé dans le dossier DbSetup.  
  
2. Supprimez le formulaire de code source de votre disque dur.
