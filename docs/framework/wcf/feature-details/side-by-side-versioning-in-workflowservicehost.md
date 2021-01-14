---
title: Versioning côte à côte dans WorkflowServiceHost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
ms.openlocfilehash: 1505582e5ac7303a2df20539fdcf67435746b9d3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190492"
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a>Versioning côte à côte dans WorkflowServiceHost

Le contrôle <xref:System.ServiceModel.Activities.WorkflowServiceHost> de version côte à côte introduit dans .NET Framework 4,5 offre la possibilité d’héberger plusieurs versions d’un service de flux de travail sur un seul point de terminaison. Une fonctionnalité côte à côte fournie permet de configurer un service de workflow de façon à ce que les nouvelles instances du service de workflow soient créées à l'aide de la nouvelle définition de workflow, alors que les instances en cours de exécution s'achèvent à l'aide de définition existante. Cette rubrique fournit une vue d'ensemble de l'exécution de service de workflow côte à côte à l'aide de <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a>Hébergement de plusieurs versions dans un service de workflow  

 <xref:System.ServiceModel.Activities.WorkflowServiceHost> contient deux propriétés qui peuvent être configurées pour permettre à plusieurs versions d'un flux de travail de s'exécuter côte à côte : <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> et <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>. <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contient les versions prises en charge du service de workflow, et <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> est utilisé pour identifier chaque service de workflow. Cela est effectué en associant un <xref:System.Activities.WorkflowIdentity> au service de workflow. <xref:System.Activities.WorkflowIdentity> contient trois informations d'identification. <xref:System.Activities.WorkflowIdentity.Name%2A> et <xref:System.Activities.WorkflowIdentity.Version%2A> contiennent un nom et un <xref:System.Version> et sont obligatoire, et <xref:System.Activities.WorkflowIdentity.Package%2A> est facultatif et peut être utilisé pour spécifier une chaîne supplémentaire contenant des informations telles que le nom de l'assembly ou d'autres informations souhaitées. Chaque service de workflow contenu de la collection <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> doit disposer d’un <xref:System.Activities.WorkflowIdentity> unique. <xref:System.Activities.WorkflowIdentity> est unique si l'une de ses trois propriétés est différente d'un autre <xref:System.Activities.WorkflowIdentity>. Un `null` <xref:System.Activities.WorkflowIdentity> est une valeur autorisée pour <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , mais une seule version antérieure d’un service de workflow peut avoir un `null` <xref:System.Activities.WorkflowIdentity> .  
  
> [!IMPORTANT]
> Un <xref:System.Activities.WorkflowIdentity> ne devrait contenir aucune information d'identification personnelle (PII). Un <xref:System.Activities.WorkflowIdentity> se compose de trois parties : un <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), un <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>) et un <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>). Les informations relatives au <xref:System.Activities.WorkflowIdentity> utilisées pour créer une instance sont émises vers n'importe quel service de suivi configuré sur plusieurs points du cycle de vie du workflow différents par le runtime. Le suivi WF ne dispose pas d'un mécanisme de masquage des informations PII (données utilisateur sensibles). Par conséquent, une instance <xref:System.Activities.WorkflowIdentity> ne doit contenir aucune donnée PII, car elle est émise par le runtime dans les enregistrements de suivi et peut être vue par n'importe quelle personne qui dispose d'un accès permettant d'afficher les enregistrements de suivi.  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a>Règles pour héberger plusieurs versions d'un service de workflow  

 Lorsqu'un utilisateur ajoute une version supplémentaire à <xref:System.ServiceModel.Activities.WorkflowServiceHost>, il existe plusieurs conditions à respecter pour qu'un service de workflow soit hébergé avec le même ensemble de points de terminaison et de description. Si l'une des versions supplémentaires ne satisfait pas ces conditions, <xref:System.ServiceModel.Activities.WorkflowServiceHost> lève une exception lorsque `Open` est appelée. Chaque définition de flux de travail fournie à l’hôte comme une version supplémentaire doit satisfaire les exigences suivantes (où la version principale est la définition de service de workflow qui est fournie au constructeur hôte). La version supplémentaire du flux de travail doit :  
  
- Avoir le même <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> que la version principale du service de workflow.  
  
- Ne doit pas avoir d'activité <xref:System.ServiceModel.Activities.Receive> ou <xref:System.ServiceModel.Activities.SendReply> dans son <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> qui ne sont pas dans la version principale, et doit correspondre au contrat d'opération.  
  
- Avoir un <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> unique. Une seule définition de workflow peut avoir une propriété `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.  
  
 Certaines modifications sont autorisées. Les éléments suivants peuvent être différents selon les versions :  
  
- <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> peut avoir un nom et un package différents de ceux de la version principale.  
  
- La valeur <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> peut être différente de celle de la version principale.  
  
- La valeur <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> peut être différente de celle de la version principale.  
  
- La valeur <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> peut être différente de celle de la version principale.  
  
### <a name="configuring-the-definitionidentity"></a>Configurer le DefinitionIdentity  

 Lorsqu’un service de workflow est créé à l’aide du concepteur de flux de travail, le <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> est défini à l’aide de la fenêtre **Propriétés** . Cliquez en dehors de l’activité racine du service dans le concepteur pour sélectionner le service de flux de travail, puis choisissez **fenêtre Propriétés** dans le menu **affichage** . Sélectionnez **WorkflowIdentity** dans la liste déroulante qui s’affiche en regard de la propriété **DefinitionIdentity** , puis développez et spécifiez les propriétés souhaitées <xref:System.Activities.WorkflowIdentity> . Dans l’exemple suivant <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , le est configuré avec le <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` et un <xref:System.Activities.WorkflowIdentity.Version%2A> de `1.0.0.0` . <xref:System.Activities.WorkflowIdentity.Package%2A> est facultatif et dans cet exemple est `null`.  
  
 ![Capture d’écran qui montre la propriété DefinitionIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-property.bmp)  
  
 Lorsqu'un service de workflow est auto-hébergé, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> est configuré lorsque le service de workflow est construit. Dans l’exemple suivant, le <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> est configuré avec les mêmes valeurs que l’exemple précédent, avec les <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` et un <xref:System.Activities.WorkflowIdentity.Name%2A> de `1.0.0.0` .  
  
```csharp  
WorkflowService service = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflow(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
```  
  
```vb  
Dim service As New WorkflowService  
With service  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflow  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
```  
  
 Un <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> n’est pas obligatoire, bien qu’une seule version du service de workflow puisse avoir une **valeur null** <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> .  
  
> [!NOTE]
> Cela est utile si le service a été déployé initialement sans <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configuré, et une version mise à jour est créée.  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a>Ajout d'une nouvelle version à un service de workflow hébergé sur le Web  

 La première étape de configuration d'une nouvelle version d'un service de flux de travail dans un service hébergé sur le Web consiste à créer un nouveau dossier dans le dossier `App_Code` portant le même nom que le fichier de service. Si le fichier `xamlx` du service est nommé `MortgageWorkflow.xamlx`, le dossier doit être nommé `MortgageWorkflow`. Placez une copie du fichier `xamlx` du service initial dans ce dossier et renommez-le, par exemple `MortgageWorkflowV1.xamlx`. Apportez les modifications souhaitées au service principal, mettez à jour son <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, puis déployez le service. Dans l'exemple suivant, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> a été mis à jour avec un <xref:System.Activities.WorkflowIdentity.Name%2A> de `MortgageWorkflow` et un <xref:System.Activities.WorkflowIdentity.Version%2A> de `2.0.0.0`.  
  
 ![Capture d’écran montrant DefinitionIdentity de WorkflowIdentity.](./media/side-by-side-versioning-in-workflowservicehost/definitionidentity-workflowidentity.bmp)  
  
 Lorsque le service redémarre, la version précédente est automatiquement ajoutée à la collection <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>, car elle se trouve dans le sous-dossier `App_Code` désigné. Notez que si la version principale du service de flux de travail a un `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , les versions précédentes ne seront pas ajoutées. Une version peut avoir une propriété `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, mais s’il existe plusieurs versions, la version principale ne doit pas être celle avec la propriété `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, sinon les versions précédentes ne seront pas ajoutées à la collection <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>.  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a>Ajout d'une nouvelle version à un service de workflow auto-hébergé  

 Lors de l’ajout d’une nouvelle version à un service de flux de travail auto-hébergé, <xref:System.ServiceModel.Activities.WorkflowServiceHost> est configuré avec la version principale du service de flux de travail, et les versions antérieures doivent être explicitement ajoutées à la collection <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>. Dans l'exemple suivant, <xref:System.ServiceModel.Activities.WorkflowServiceHost> est configuré avec un service de workflow principal qui utilise une définition de workflow `MortgageWorkflowV2`, et un service de workflow configuré avec une définition de workflow `MortgageWorkflowV1` est ajouté à la collection <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>. Chaque service de workflow est configuré avec un <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> unique qui reflète la version de la définition de workflow.  
  
```csharp  
// Create the primary version of the workflow service.  
WorkflowService serviceV2 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV2(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(2, 0, 0, 0)  
    }  
};  
  
// Configure the WorkflowServiceHost with the current version  
// of the workflow service. This code requires Administrator  
// privileges to function correctly. If running from Visual  
// Studio, Visual Studio must be run with Administrator privileges.  
WorkflowServiceHost host = new WorkflowServiceHost(serviceV2,
    new Uri("http://localhost:8080/MortgageWorkflowService"));  
  
// Create the previous version of the workflow service.  
WorkflowService serviceV1 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV1(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
  
// Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1);  
```  
  
```vb  
'Create the primary version of the workflow service  
Dim serviceV2 As New WorkflowService  
With serviceV2  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV2  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(2, 0, 0, 0) _  
    }  
End With  
  
'Configure the WorkflowServiceHost with the current version  
'of the workflow service. This code requires Administrator  
'privileges to function correctly. If running from Visual  
'Studio, Visual Studio must be run with Administrator privileges.  
  
Dim host As New WorkflowServiceHost(serviceV2, _  
    New Uri("http://localhost:8080/MortgageWorkflowService"))  
  
'Create the previous version of the workflow service.  
Dim serviceV1 As New WorkflowService  
With serviceV1  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV1  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
  
'Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1)  
```
