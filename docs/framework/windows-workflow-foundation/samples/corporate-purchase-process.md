---
title: Processus d'achat d'entreprise
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: aa2ca2577eb68204ffcb755ce1b16b9354348ee3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293466"
---
# <a name="corporate-purchase-process"></a>Processus d'achat d'entreprise

Cet exemple montre comment créer un processus d'achat basé sur des appels d'offres très simples avec sélection automatique de la meilleure proposition. Il combine <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601> et <xref:System.Activities.Statements.ForEach%601> ainsi qu'une activité personnalisée pour créer un workflow qui représente le processus.

 Cet exemple contient une application cliente ASP.NET qui permet d’interagir avec le processus comme des participants différents (comme demandeur d’origine ou un fournisseur particulier).

## <a name="requirements"></a>Spécifications

- Visual Studio 2012.

- [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].

## <a name="demonstrates"></a>Illustre le

- Activités personnalisées.

- Composition des activités

- les signets ;

- Persistance.

- Persistance schématisée.

- Traçage.

- Suivi.

- Hébergement [!INCLUDE[wf1](../../../../includes/wf1-md.md)] dans différents clients (applications Web ASP.net et applications WinForms).

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Description du processus  

 Cet exemple montre une implémentation d’un programme Windows Workflow Foundation (WF) pour rassembler des propositions de fournisseurs pour une société générique.  
  
1. Un employé de la Société X crée un appel d'offres.  
  
    1. L'employé tape le titre et la description de l'appel d'offres.  
  
    2. L’employé sélectionne les fournisseurs qu’il souhaite inviter à soumettre des propositions.  
  
2. L'employé soumet la proposition.  
  
    1. Une instance du workflow est créée.  
  
    2. Le workflow attend que tous les fournisseurs soumettent leurs propositions.  
  
3. Une fois toutes les propositions reçues, le workflow effectue une itération au sein d'entre elles et sélectionne la meilleure.  
  
    1. Chaque fournisseur a une réputation (cet exemple stocke la liste des réputations dans VendorRepository.cs).  
  
    2. La valeur totale de la proposition est déterminée par (Valeur tapée par le fournisseur) * (Réputation enregistrée du fournisseur) / 100.  
  
4. Le demandeur d'origine peut consulter toutes les propositions soumises. La meilleure proposition est présentée dans une section spéciale du rapport.  
  
## <a name="process-definition"></a>Définition de processus  

 La logique principale de l'exemple utilise une activité <xref:System.Activities.Statements.ParallelForEach%601> qui attend les offres de chaque fournisseur (à l'aide d'une activité personnalisée qui crée un signet) et inscrit la proposition de fournisseur comme un appel d'offres (à l'aide d'une activité <xref:System.Activities.Statements.InvokeMethod> ).  
  
 L'exemple effectue ensuite une itération au sein de toutes les propositions reçues stockées dans le `RfpRepository`, en calculant la valeur ajustée (à l'aide d'une activité <xref:System.Activities.Statements.Assign> et d'activités <xref:System.Activities.Expressions>) et, si la valeur ajustée est meilleure que la meilleure offre précédente, assigne la nouvelle valeur comme meilleure offre (à l'aide des activités <xref:System.Activities.Statements.If> et <xref:System.Activities.Statements.Assign>).  
  
## <a name="projects-in-this-sample"></a>Projets dans cet exemple  

 Cet exemple contient les projets suivants.  
  
|Projet|Description|  
|-------------|-----------------|  
|Courant|Objets entité utilisés dans le processus (Appel d'offres, Fournisseur et Proposition de fournisseur).|  
|WfDefinition|Définition du processus (comme un programme [!INCLUDE[wf1](../../../../includes/wf1-md.md)]) et hôte (`PurchaseProcessHost`) utilisé par les applications clientes pour la création et l'utilisation des instances du workflow du processus d'achat.|  
|WebClient|Application cliente ASP.NET qui permet aux utilisateurs de créer et de participer à des instances du processus d’achat. Elle utilise un hôte créé de façon personnalisée pour interagir avec le moteur de workflow.|  
|WinFormsClient|Application cliente Windows Forms qui permet aux utilisateurs de créer des instances du processus d'achat et d'y participer. Elle utilise un hôte créé de façon personnalisée pour interagir avec le moteur de workflow.|  
  
### <a name="wfdefinition"></a>WfDefinition  

 Le tableau suivant contient une description des fichiers les plus importants dans le projet WfDefinition.  
  
|Fichier|Description|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|Interface pour l'hôte du workflow.|  
|PurchaseProcessHost.cs|Implémentation d'un hôte pour le workflow. L'hôte rend les détails de l'exécution du workflow abstraits et est utilisé dans toutes les applications clientes pour charger et exécuter les instances de workflow `PurchaseProcess`, et interagir avec celles-ci.|  
|PurchaseProcessWorkflow.cs|Activité qui contient la définition du workflow du processus d'achat (dérive de <xref:System.Activities.Activity>).<br /><br /> Les activités qui dérivent de <xref:System.Activities.Activity> composent les fonctionnalités en assemblant des activités personnalisées existantes et des activités de la bibliothèque d'activités [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Assembler ces activités est la méthode la plus simple pour créer des fonctionnalités personnalisées.|  
|WaitForVendorProposal.cs|Cette activité personnalisée dérive de <xref:System.Activities.NativeActivity> et crée un signet nommé qui doit être repris ultérieurement par un fournisseur lors de l'envoi de la proposition.<br /><br /> Les activités qui dérivent de <xref:System.Activities.NativeActivity>, comme celles qui dérivent de <xref:System.Activities.CodeActivity>, créent des fonctionnalités impératives en remplaçant la méthode <xref:System.Activities.NativeActivity.Execute%2A>, mais elles ont également accès à toutes les fonctionnalités d'exécution de workflow via le contexte <xref:System.Activities.ActivityContext> passé dans la méthode `Execute`. Ce contexte prend en charge la planification et l’annulation des activités enfants, la configuration de zones de non-persistance (blocs d’exécution pendant lesquels l’exécution ne rend pas persistantes les données du workflow, par exemple dans les transactions atomiques) et les <xref:System.Activities.Bookmark> objets (Handles de reprise des workflows suspendus).|  
|TrackingParticipant.cs|<xref:System.Activities.Tracking.TrackingParticipant> qui reçoit tous les événements de suivi et les enregistre dans un fichier texte.<br /><br /> Les participants de suivi sont ajoutés à l’instance de workflow comme Extensions.|  
|XmlWorkflowInstanceStore.cs|<xref:System.Runtime.DurableInstancing.InstanceStore> personnalisé qui enregistre des applications de workflow dans des fichiers XML.|  
|XmlPersistenceParticipant.cs|<xref:System.Activities.Persistence.PersistenceParticipant> personnalisé qui enregistre une instance d'appel d'offres dans un fichier XML.|  
|AsyncResult.cs / CompletedAsyncResult.cs|Classes d’assistance pour l’implémentation du modèle asynchrone dans les composants de persistance.|  
  
### <a name="common"></a>Courant  

 Le tableau suivant contient une description des classes les plus importantes dans le projet Common.  
  
|Classe|Description|  
|-----------|-----------------|  
|Fournisseur|Fournisseur qui soumet des propositions dans un appel d'offres.|  
|RequestForProposal|Un appel d'offres est une invitation pour les fournisseurs à soumettre des propositions sur une marchandise ou un service spécifique.|  
|VendorProposal|Proposition soumise par un fournisseur dans un appel d'offres concret.|  
|VendorRepository|Référentiel de fournisseurs. Cette implémentation contient une collection en mémoire d'instances de Fournisseur et de méthodes pour l'exposition de ces instances.|  
|RfpRepository|Référentiel d'appels d'offres. Cette implémentation contient des utilisations de LINQ to XML pour interroger le fichier XML d'appels d'offres généré par la persistance schématisée. |  
|IOHelper|Cette classe gère tous les problèmes liés aux E/S (dossiers, chemins d'accès, et ainsi de suite).|  
  
### <a name="web-client"></a>Client web  

 Le tableau suivant contient une description des pages web les plus importantes dans le projet web Client.  
  
|Fichier|Description|  
|-|-|  
|CreateRfp.aspx|Crée et soumet un nouvel appel d'offres.|  
|Default.aspx|Affiche tous les appels d'offres actifs et terminés.|  
|GetVendorProposal.aspx|Obtient une proposition d'un fournisseur dans un appel d'offres concret. Cette page est utilisée uniquement par les fournisseurs.|  
|ShowRfp.aspx|Affiche toutes les informations sur un appel d'offres (propositions reçues, dates, valeurs et autres informations). Cette page est utilisée uniquement par le créateur de l'appel d'offres.|  
  
### <a name="winforms-client"></a>WinForms Client  

 Le tableau suivant contient une description des formulaires les plus importants dans le projet Win Forms.  
  
|Formulaire|Description|  
|-|-|  
|NewRfp|Crée et soumet un nouvel appel d'offres.|  
|ShowProposals|Affiche tous les appels d'offres actifs et terminés. **Remarque :**  Vous devrez peut-être cliquer sur le bouton **Actualiser** dans l’interface utilisateur pour afficher les modifications apportées à cet écran après la création ou la modification d’une demande de proposition.|  
|SubmitProposal|Obtient une proposition d'un fournisseur dans un appel d'offres concret. Cette fenêtre est utilisée uniquement par les fournisseurs.|  
|ViewRfp|Affiche toutes les informations sur un appel d'offres (propositions reçues, dates, valeurs et autres informations). Cette fenêtre est utilisée uniquement par le créateur de l'appel d'offres.|  
  
### <a name="persistence-files"></a>Fichiers de persistance  

 Le tableau suivant indique que les fichiers générés par le fournisseur de persistance (`XmlPersistenceProvider`) se trouvent dans le chemin d’accès du dossier temporaire du système actuel (à l’aide de <xref:System.IO.Path.GetTempPath%2A>). Le fichier de suivi est créé dans le chemin d’exécution actuel.  
  
|Nom de fichier|Description|Path|  
|-|-|-|  
|rfps.xml|Fichier XML avec tous les appels d'offres actifs et terminés.|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceid]|Ce fichier contient toutes les informations sur une instance de workflow.<br /><br /> Ce fichier est généré par l'implémentation de persistance schématisée (PersistenceParticipant dans XmlPersistenceProvider).|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceId].tracking|Fichier texte avec tous les événements qui se sont produits dans une instance concrète.<br /><br /> Ce fichier est généré par TrackingParticipant.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess.Tracing.TraceLog.txt|Fichier de suivi généré par le workflow selon les paramètres de configuration dans les fichiers App.config ou Web.config.|Chemin d’exécution actuel|  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1. À l’aide de Visual Studio 2010, ouvrez le fichier solution PurchaseProcess. sln.  
  
2. Pour exécuter le projet de client Web, ouvrez **Explorateur de solutions** et cliquez avec le bouton droit sur le projet de **client Web** . Sélectionnez **définir comme projet de démarrage**.  
  
3. Pour exécuter le projet client WinForms, ouvrez **Explorateur de solutions** et cliquez avec le bouton droit sur le projet **WinForms client** . Sélectionnez **définir comme projet de démarrage**.  
  
4. Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
5. Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
### <a name="web-client-options"></a>Options de Web Client  
  
- **Créer un appel d’offres**: crée une demande de propositions et démarre un flux de travail de processus d’achat.  
  
- **Actualiser : actualise** la liste des appels d’offres actifs et terminés dans la fenêtre principale.  
  
- **Vue**: affiche le contenu d’un appel d’offres existant. Les fournisseurs peuvent soumettre leurs propositions (s'ils y sont invités ou si l'appel d'offres n'est pas terminé).  
  
- Afficher comme : l’utilisateur peut accéder à l’appel d’offres à l’aide de différentes identités en sélectionnant le participant souhaité dans la zone de liste déroulante **afficher comme** dans la grille des appels d’offres actifs.  
  
### <a name="winforms-client-options"></a>Options de WinForms Client  
  
- **Créer un appel d’offres**: crée une demande de propositions (RFP) et démarre un workflow de processus d’achat.  
  
- **Actualiser : actualise** la liste des appels d’offres actifs et terminés dans la fenêtre principale.  
  
- **Afficher l’appel d’offres**: affiche le contenu d’un appel d’offres existant. Les fournisseurs peuvent soumettre leurs propositions (s'ils y sont invités ou si l'appel d'offres n'est pas terminé).  
  
- **Se connecter en tant que**: l’utilisateur peut accéder à l’appel d’offres à l’aide de différentes identités en sélectionnant le participant souhaité dans la zone de liste déroulante **afficher en tant que** dans la grille des appels d’offres
