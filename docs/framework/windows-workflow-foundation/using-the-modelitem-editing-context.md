---
title: Utilisation du contexte d'édition ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a47cb53e50d221c0ae07cf0841688fe4f8ced7d4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988918"
---
# <a name="using-the-modelitem-editing-context"></a>Utilisation du contexte d'édition ModelItem
Le contexte d'édition <xref:System.Activities.Presentation.Model.ModelItem> est l'objet que l'application hôte utilise pour communiquer avec le concepteur. <xref:System.Activities.Presentation.EditingContext> expose deux méthodes, <xref:System.Activities.Presentation.EditingContext.Items%2A> et <xref:System.Activities.Presentation.EditingContext.Services%2A>, qui peuvent être utilisées  
  
## <a name="the-items-collection"></a>La collection Items  
 La collection <xref:System.Activities.Presentation.EditingContext.Items%2A> permet d'accéder aux données partagées entre l'hôte et le concepteur ou aux données disponibles pour tous les concepteurs. Cette collection fournit les fonctionnalités suivantes, accessibles via la classe <xref:System.Activities.Presentation.ContextItemManager> :  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>La collection Services  
 La collection <xref:System.Activities.Presentation.EditingContext.Services%2A> permet d’accéder aux services que le concepteur utilise pour interagir avec l’hôte ou aux services que les concepteurs utilisent. Cette collection présente les méthodes de références suivantes :  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Assignation d'une activité à un concepteur  
 L'attribut Designer permet de spécifier le concepteur utilisé par une activité.  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a>Création d'un service  
 Pour créer un service servant de canal de transmission des informations entre le concepteur et l'hôte, une interface et une implémentation doivent être créées. L'interface est utilisée par la méthode <xref:System.Activities.Presentation.ServiceManager.Publish%2A> pour définir les membres du service et l'implémentation contient la logique du service. Dans l'exemple de code suivant, une interface et une implémentation de service sont créées.  
  
```csharp  
public interface IMyService  
    {  
        IEnumerable<string> GetValues(string DisplayName);  
    }  
  
    public class MyServiceImpl : IMyService  
    {  
        public IEnumerable<string> GetValues(string DisplayName)  
        {  
            return new string[]  {   
                DisplayName + " One",   
                DisplayName + " Two",  
                "Three " + DisplayName  
            } ;  
        }  
    }  
```  
  
## <a name="publishing-a-service"></a>Publication d'un service  
 Pour qu'un concepteur puisse consommer un service, il doit d'abord être publié par l'hôte à l'aide de la méthode <xref:System.Activities.Presentation.ServiceManager.Publish%2A>.  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Abonnement à un service  
 Le concepteur obtient l'accès au service à l'aide de la méthode <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> dans la méthode <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A>. L'extrait de code suivant montre comment s'abonner à un service.  
  
```csharp  
protected override void OnModelItemChanged(object newItem)  
{  
    if (!subscribed)  
    {  
        this.Context.Services.Subscribe<IMyService>(  
            servInstance =>  
            {  
                listBox1.ItemsSource = servInstance.GetValues(this.ModelItem.Properties["DisplayName"].ComputedValue.ToString());  
            }  
            );  
        subscribed = true;   
    }  
}  
```  
  
## <a name="sharing-data-using-the-items-collection"></a>Partage de données à l’aide de la collection Items  
 L'utilisation de la collection Items est similaire à celle de la collection Services, à ceci près que <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> est utilisé à la place de Publish. Cette collection est plus appropriée pour le partage de données simples entre les concepteurs et l’hôte qu’une fonctionnalité complexe.  
  
## <a name="editingcontext-host-items-and-services"></a>Éléments et services de l'hôte EditingContext  
 Le .NET Framework fournit un certain nombre d’éléments intégrés et de services accessibles via le contexte d’édition.  
  
 Éléments :  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Gère la liste des assemblys locaux référencés qui seront utilisés dans le flux de travail pour les contrôles (tels que l’éditeur d’expressions).  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indique si le concepteur est en lecture seule.  
  
- <xref:System.Activities.Presentation.View.Selection>: Définit la collection d’objets actuellement sélectionnés.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>: Fournit des informations sur le fichier sur lequel la session d’édition actuelle est basée.  
  
 Services :  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Autorise l’ajout de propriétés à l’instance actuelle, à <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>l’aide de.  
  
- <xref:System.Activities.Presentation.View.DesignerView>: Autorise l’accès aux propriétés de la zone de dessin du concepteur.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>: Permet de mettre à jour le contenu de la boîte à outils.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>: Utilisé pour intégrer les commandes du concepteur (telles que le menu contextuel) aux implémentations de service personnalisées.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Fournit des fonctionnalités pour le débogueur du concepteur.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>: Donne accès à la boîte de dialogue Éditeur d’expressions.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>: Fournit le concepteur avec des fonctionnalités d’aide intégrées.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Fournit l’accès aux erreurs de <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>validation à l’aide de.  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Fournit un service interne pour stocker et récupérer des données. Ce service est utilisé en interne par le .NET Framework et n’est pas destiné à un usage externe.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>: Fournit l’accès à la collection d’erreurs de <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>chargement XAML à l’aide de.  
  
- <xref:System.Activities.Presentation.Services.ModelService>: Utilisé par le concepteur pour interagir avec le modèle du workflow en cours de modification.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>: Fournit l’accès à la racine de l’arborescence d’éléments <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>de modèle à l’aide de.  
  
- <xref:System.Activities.Presentation.UndoEngine>: Fournit les fonctionnalités d’annulation et de rétablissement.  
  
- <xref:System.Activities.Presentation.Services.ViewService>: Mappe des éléments visuels à des éléments de modèle sous-jacents.  
  
- <xref:System.Activities.Presentation.View.ViewStateService>: Stocke les États d’affichage pour les éléments de modèle.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Utilisé pour personnaliser le comportement de l’interface utilisateur du conteneur virtuel.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Permet d’inscrire et d’annuler l’enregistrement des délégués pour les notifications d’événements. Permet également de définir un propriétaire de la fenêtre.
