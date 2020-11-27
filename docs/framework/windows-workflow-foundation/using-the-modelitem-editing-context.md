---
title: Utilisation du contexte d'édition ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: 2ab002f902833d3b1a69ea0b03b5ca589f4492d1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275968"
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
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem> : gère la liste d'assemblys locaux référencés qui seront utilisés dans le workflow pour les contrôles (tels que l'éditeur d'expression).  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState> : indique si le concepteur affiche un état de lecture seule.  
  
- <xref:System.Activities.Presentation.View.Selection> : définit la collection d'objets actuellement sélectionnés.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem> : fournit des informations sur le fichier sur lequel la session d'édition active repose.  
  
 Services :  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService> : permet d'ajouter les propriétés à l'instance actuelle, à l'aide de <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.  
  
- <xref:System.Activities.Presentation.View.DesignerView> : permet d'accéder aux propriétés de la zone de conception.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService> : permet de mettre à jour le contenu de la boîte à outils.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService> : permet d'intégrer les commandes du concepteur (telles que le menu contextuel) avec les implémentations de service fournies sur demande.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView> : fournit les fonctionnalités du débogueur du concepteur.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService> : fournit l'accès à la boîte de dialogue Éditeur d'expressions.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService> : fournit le concepteur avec une fonctionnalité d'aide.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService> : fournit l'accès aux erreurs de validation à l'aide de <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService> : fournit un service interne pour stocker et récupérer des données. Ce service est utilisé en interne par le .NET Framework et n’est pas destiné à un usage externe.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService> : fournit l'accès à la collection d'erreurs de chargement XAML à l'aide de <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.  
  
- <xref:System.Activities.Presentation.Services.ModelService> : permet au concepteur d'interagir avec le modèle du workflow en cours de modification.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager> : fournit l'accès à la racine de l'arborescence d'éléments de modèle à l'aide de <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
- <xref:System.Activities.Presentation.UndoEngine> : fournit des fonctionnalités d'annulation et de rétablissement.  
  
- <xref:System.Activities.Presentation.Services.ViewService> : mappe les éléments visuels à des éléments de modèles sous-jacents.  
  
- <xref:System.Activities.Presentation.View.ViewStateService> : stocke des états d'affichage pour les éléments de modèles.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService> : utilisé pour personnaliser le comportement de l'interface utilisateur du conteneur virtuel.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService> : permet d'enregistrer et d'annuler l'enregistrement des délégués pour les notifications d'événements. Permet également de définir un propriétaire de la fenêtre.
