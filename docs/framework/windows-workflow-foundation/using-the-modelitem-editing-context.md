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
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="5ba61-102">Utilisation du contexte d'édition ModelItem</span><span class="sxs-lookup"><span data-stu-id="5ba61-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="5ba61-103">Le contexte d'édition <xref:System.Activities.Presentation.Model.ModelItem> est l'objet que l'application hôte utilise pour communiquer avec le concepteur.</span><span class="sxs-lookup"><span data-stu-id="5ba61-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="5ba61-104"><xref:System.Activities.Presentation.EditingContext> expose deux méthodes, <xref:System.Activities.Presentation.EditingContext.Items%2A> et <xref:System.Activities.Presentation.EditingContext.Services%2A>, qui peuvent être utilisées</span><span class="sxs-lookup"><span data-stu-id="5ba61-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="5ba61-105">La collection Items</span><span class="sxs-lookup"><span data-stu-id="5ba61-105">The Items collection</span></span>  
 <span data-ttu-id="5ba61-106">La collection <xref:System.Activities.Presentation.EditingContext.Items%2A> permet d'accéder aux données partagées entre l'hôte et le concepteur ou aux données disponibles pour tous les concepteurs.</span><span class="sxs-lookup"><span data-stu-id="5ba61-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="5ba61-107">Cette collection fournit les fonctionnalités suivantes, accessibles via la classe <xref:System.Activities.Presentation.ContextItemManager> :</span><span class="sxs-lookup"><span data-stu-id="5ba61-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="5ba61-108">La collection Services</span><span class="sxs-lookup"><span data-stu-id="5ba61-108">The Services collection</span></span>  
 <span data-ttu-id="5ba61-109">La collection <xref:System.Activities.Presentation.EditingContext.Services%2A> permet d’accéder aux services que le concepteur utilise pour interagir avec l’hôte ou aux services que les concepteurs utilisent.</span><span class="sxs-lookup"><span data-stu-id="5ba61-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="5ba61-110">Cette collection présente les méthodes de références suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ba61-110">This collection has the following methods of note:</span></span>  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="5ba61-111">Assignation d'une activité à un concepteur</span><span class="sxs-lookup"><span data-stu-id="5ba61-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="5ba61-112">L'attribut Designer permet de spécifier le concepteur utilisé par une activité.</span><span class="sxs-lookup"><span data-stu-id="5ba61-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="5ba61-113">Création d'un service</span><span class="sxs-lookup"><span data-stu-id="5ba61-113">Creating a service</span></span>  
 <span data-ttu-id="5ba61-114">Pour créer un service servant de canal de transmission des informations entre le concepteur et l'hôte, une interface et une implémentation doivent être créées.</span><span class="sxs-lookup"><span data-stu-id="5ba61-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="5ba61-115">L'interface est utilisée par la méthode <xref:System.Activities.Presentation.ServiceManager.Publish%2A> pour définir les membres du service et l'implémentation contient la logique du service.</span><span class="sxs-lookup"><span data-stu-id="5ba61-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="5ba61-116">Dans l'exemple de code suivant, une interface et une implémentation de service sont créées.</span><span class="sxs-lookup"><span data-stu-id="5ba61-116">In the following code example, a service interface and implementation are created.</span></span>  
  
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
  
## <a name="publishing-a-service"></a><span data-ttu-id="5ba61-117">Publication d'un service</span><span class="sxs-lookup"><span data-stu-id="5ba61-117">Publishing a service</span></span>  
 <span data-ttu-id="5ba61-118">Pour qu'un concepteur puisse consommer un service, il doit d'abord être publié par l'hôte à l'aide de la méthode <xref:System.Activities.Presentation.ServiceManager.Publish%2A>.</span><span class="sxs-lookup"><span data-stu-id="5ba61-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="5ba61-119">Abonnement à un service</span><span class="sxs-lookup"><span data-stu-id="5ba61-119">Subscribing to a service</span></span>  
 <span data-ttu-id="5ba61-120">Le concepteur obtient l'accès au service à l'aide de la méthode <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> dans la méthode <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="5ba61-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="5ba61-121">L'extrait de code suivant montre comment s'abonner à un service.</span><span class="sxs-lookup"><span data-stu-id="5ba61-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="5ba61-122">Partage de données à l’aide de la collection Items</span><span class="sxs-lookup"><span data-stu-id="5ba61-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="5ba61-123">L'utilisation de la collection Items est similaire à celle de la collection Services, à ceci près que <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> est utilisé à la place de Publish.</span><span class="sxs-lookup"><span data-stu-id="5ba61-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="5ba61-124">Cette collection est plus appropriée pour le partage de données simples entre les concepteurs et l’hôte qu’une fonctionnalité complexe.</span><span class="sxs-lookup"><span data-stu-id="5ba61-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="5ba61-125">Éléments et services de l'hôte EditingContext</span><span class="sxs-lookup"><span data-stu-id="5ba61-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="5ba61-126">Le .NET Framework fournit un certain nombre d’éléments intégrés et de services accessibles via le contexte d’édition.</span><span class="sxs-lookup"><span data-stu-id="5ba61-126">The .NET Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="5ba61-127">Éléments :</span><span class="sxs-lookup"><span data-stu-id="5ba61-127">Items:</span></span>  
  
- <span data-ttu-id="5ba61-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Gère la liste des assemblys locaux référencés qui seront utilisés dans le flux de travail pour les contrôles (tels que l’éditeur d’expressions).</span><span class="sxs-lookup"><span data-stu-id="5ba61-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
- <span data-ttu-id="5ba61-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indique si le concepteur est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="5ba61-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
- <span data-ttu-id="5ba61-130"><xref:System.Activities.Presentation.View.Selection>: Définit la collection d’objets actuellement sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="5ba61-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
- <span data-ttu-id="5ba61-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="5ba61-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
- <span data-ttu-id="5ba61-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Fournit des informations sur le fichier sur lequel la session d’édition actuelle est basée.</span><span class="sxs-lookup"><span data-stu-id="5ba61-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="5ba61-133">Services :</span><span class="sxs-lookup"><span data-stu-id="5ba61-133">Services:</span></span>  
  
- <span data-ttu-id="5ba61-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Autorise l’ajout de propriétés à l’instance actuelle, à <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>l’aide de.</span><span class="sxs-lookup"><span data-stu-id="5ba61-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
- <span data-ttu-id="5ba61-135"><xref:System.Activities.Presentation.View.DesignerView>: Autorise l’accès aux propriétés de la zone de dessin du concepteur.</span><span class="sxs-lookup"><span data-stu-id="5ba61-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
- <span data-ttu-id="5ba61-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Permet de mettre à jour le contenu de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="5ba61-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
- <span data-ttu-id="5ba61-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Utilisé pour intégrer les commandes du concepteur (telles que le menu contextuel) aux implémentations de service personnalisées.</span><span class="sxs-lookup"><span data-stu-id="5ba61-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
- <span data-ttu-id="5ba61-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Fournit des fonctionnalités pour le débogueur du concepteur.</span><span class="sxs-lookup"><span data-stu-id="5ba61-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
- <span data-ttu-id="5ba61-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Donne accès à la boîte de dialogue Éditeur d’expressions.</span><span class="sxs-lookup"><span data-stu-id="5ba61-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
- <span data-ttu-id="5ba61-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Fournit le concepteur avec des fonctionnalités d’aide intégrées.</span><span class="sxs-lookup"><span data-stu-id="5ba61-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
- <span data-ttu-id="5ba61-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Fournit l’accès aux erreurs de <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>validation à l’aide de.</span><span class="sxs-lookup"><span data-stu-id="5ba61-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
- <span data-ttu-id="5ba61-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Fournit un service interne pour stocker et récupérer des données.</span><span class="sxs-lookup"><span data-stu-id="5ba61-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="5ba61-143">Ce service est utilisé en interne par le .NET Framework et n’est pas destiné à un usage externe.</span><span class="sxs-lookup"><span data-stu-id="5ba61-143">This service is used internally by the .NET Framework, and is not intended for external use.</span></span>  
  
- <span data-ttu-id="5ba61-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Fournit l’accès à la collection d’erreurs de <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>chargement XAML à l’aide de.</span><span class="sxs-lookup"><span data-stu-id="5ba61-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
- <span data-ttu-id="5ba61-145"><xref:System.Activities.Presentation.Services.ModelService>: Utilisé par le concepteur pour interagir avec le modèle du workflow en cours de modification.</span><span class="sxs-lookup"><span data-stu-id="5ba61-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
- <span data-ttu-id="5ba61-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Fournit l’accès à la racine de l’arborescence d’éléments <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>de modèle à l’aide de.</span><span class="sxs-lookup"><span data-stu-id="5ba61-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
- <span data-ttu-id="5ba61-147"><xref:System.Activities.Presentation.UndoEngine>: Fournit les fonctionnalités d’annulation et de rétablissement.</span><span class="sxs-lookup"><span data-stu-id="5ba61-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
- <span data-ttu-id="5ba61-148"><xref:System.Activities.Presentation.Services.ViewService>: Mappe des éléments visuels à des éléments de modèle sous-jacents.</span><span class="sxs-lookup"><span data-stu-id="5ba61-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
- <span data-ttu-id="5ba61-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stocke les États d’affichage pour les éléments de modèle.</span><span class="sxs-lookup"><span data-stu-id="5ba61-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
- <span data-ttu-id="5ba61-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Utilisé pour personnaliser le comportement de l’interface utilisateur du conteneur virtuel.</span><span class="sxs-lookup"><span data-stu-id="5ba61-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
- <span data-ttu-id="5ba61-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Permet d’inscrire et d’annuler l’enregistrement des délégués pour les notifications d’événements.</span><span class="sxs-lookup"><span data-stu-id="5ba61-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="5ba61-152">Permet également de définir un propriétaire de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="5ba61-152">Also allows a window owner to be set.</span></span>
