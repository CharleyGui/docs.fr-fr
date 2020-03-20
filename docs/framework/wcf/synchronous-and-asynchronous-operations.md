---
title: Opérations synchrones et asynchrones
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 75a585efcdf316f407f3617fef8e1e279dcd922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143211"
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="164bb-102">Opérations synchrones et asynchrones</span><span class="sxs-lookup"><span data-stu-id="164bb-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="164bb-103">Cette rubrique traite de l'implémentation et de l'appel des opérations de service asynchrones.</span><span class="sxs-lookup"><span data-stu-id="164bb-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="164bb-104">De nombreuses applications appellent des méthodes de façon asynchrone, car elles peuvent ainsi continuer à effectuer un travail utile pendant que l'appel de méthode s'exécute.</span><span class="sxs-lookup"><span data-stu-id="164bb-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="164bb-105">Les services et les clients Windows Communication Foundation (WCF) peuvent participer à des appels d'opération asynchrones à deux niveaux distincts de l'application, qui procurent aux applications WCF plus de souplesse pour optimiser le débit en fonction de l'interactivité.</span><span class="sxs-lookup"><span data-stu-id="164bb-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="164bb-106">Types d'opérations asynchrones</span><span class="sxs-lookup"><span data-stu-id="164bb-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="164bb-107">Tous les contrats de service dans WCF, indépendamment des types de paramètres et des valeurs de retour, utilisent des attributs WCF pour spécifier un modèle d’échange de messages particulier entre le client et le service.</span><span class="sxs-lookup"><span data-stu-id="164bb-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="164bb-108">WCF route automatiquement les messages entrants et sortants vers l'opération de service appropriée ou le code client exécuté.</span><span class="sxs-lookup"><span data-stu-id="164bb-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="164bb-109">Le client possède uniquement le contrat de service qui spécifie le modèle d’échange de messages pour une opération particulière.</span><span class="sxs-lookup"><span data-stu-id="164bb-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="164bb-110">Les clients peuvent offrir au développeur un modèle de programmation de leur choix, tant que le modèle d’échange de messages sous-jacent est respecté.</span><span class="sxs-lookup"><span data-stu-id="164bb-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="164bb-111">De même, les services peuvent implémenter des opérations de quelque manière que ce soit, à condition que le modèle de message spécifié soit respecté.</span><span class="sxs-lookup"><span data-stu-id="164bb-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="164bb-112">L'indépendance du contrat de service vis-à-vis de l'implémentation du service ou du client autorise les types d'exécutions asynchrones suivants dans les applications WCF :</span><span class="sxs-lookup"><span data-stu-id="164bb-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
- <span data-ttu-id="164bb-113">Les clients peuvent appeler de façon asynchrone des opérations de demande/réponse à l'aide d'un échange de messages synchrone.</span><span class="sxs-lookup"><span data-stu-id="164bb-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="164bb-114">Les services peuvent implémenter de façon asynchrone une opération de demande/réponse à l’aide d’un échange de messages synchrone.</span><span class="sxs-lookup"><span data-stu-id="164bb-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
- <span data-ttu-id="164bb-115">Les échanges de messages peuvent être unidirectionnels, indépendamment de l'implémentation du client ou service.</span><span class="sxs-lookup"><span data-stu-id="164bb-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="164bb-116">Scénarios asynchrones suggérés</span><span class="sxs-lookup"><span data-stu-id="164bb-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="164bb-117">Utilisez une approche asynchrone dans une implémentation de l'opération de service si celle-ci passe un appel bloquant, par exemple une tâche en E/S.</span><span class="sxs-lookup"><span data-stu-id="164bb-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="164bb-118">Lorsque vous êtes dans une implémentation d’opération asynchrone, essayez d’appeler des méthodes et des opérations asynchrones pour étendre le chemin d’appel asynchrone aussi loin que possible.</span><span class="sxs-lookup"><span data-stu-id="164bb-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="164bb-119">Par exemple, appelez `BeginOperationTwo()` à partir d'un `BeginOperationOne()`.</span><span class="sxs-lookup"><span data-stu-id="164bb-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
- <span data-ttu-id="164bb-120">Utilisez une approche asynchrone dans une application cliente ou appelante dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="164bb-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
- <span data-ttu-id="164bb-121">Si vous appelez des opérations à partir d'une application intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="164bb-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="164bb-122">(Pour plus d’informations sur ces scénarios, consultez [Applications clientes de niveau intermédiaire](./feature-details/middle-tier-client-applications.md).)</span><span class="sxs-lookup"><span data-stu-id="164bb-122">(For more information about such scenarios, see [Middle-Tier Client Applications](./feature-details/middle-tier-client-applications.md).)</span></span>  
  
- <span data-ttu-id="164bb-123">Si vous appelez des opérations à partir d'une page ASP.NET, utiliser des pages asynchrones.</span><span class="sxs-lookup"><span data-stu-id="164bb-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
- <span data-ttu-id="164bb-124">Si vous appelez des opérations à partir de n'importe quelle application monothread, telle que Windows Forms ou Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="164bb-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="164bb-125">Lorsque vous utilisez le modèle d'appel asynchrone basé sur des événements, l'événement résultant est déclenché sur le thread d'interface utilisateur, ce qui accroît la réactivité de l'application sans exiger la gestion de plusieurs threads.</span><span class="sxs-lookup"><span data-stu-id="164bb-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
- <span data-ttu-id="164bb-126">En général, si vous avez le choix entre un appel synchrone et asynchrone, choisissez l’appel asynchrone.</span><span class="sxs-lookup"><span data-stu-id="164bb-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="164bb-127">Implémentation d'une opération de service asynchrone</span><span class="sxs-lookup"><span data-stu-id="164bb-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="164bb-128">Les opérations asynchrones peuvent être implémentées à l'aide d'une des trois méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="164bb-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1. <span data-ttu-id="164bb-129">Modèle asynchrone basé sur des tâches</span><span class="sxs-lookup"><span data-stu-id="164bb-129">The task-based asynchronous pattern</span></span>  
  
2. <span data-ttu-id="164bb-130">Modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="164bb-130">The event-based asynchronous pattern</span></span>  
  
3. <span data-ttu-id="164bb-131">Modèle asynchrone IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="164bb-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="164bb-132">Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)</span><span class="sxs-lookup"><span data-stu-id="164bb-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="164bb-133">Le modèle asynchrone basé sur des tâches constitue le meilleur moyen d’implémenter des opérations asynchrones, car il est le plus facile et le plus simple.</span><span class="sxs-lookup"><span data-stu-id="164bb-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="164bb-134">Pour utiliser cette méthode, implémentez simplement votre opération de service et spécifiez un type de retour Task\<T>, où T est le type retourné par l'opération logique.</span><span class="sxs-lookup"><span data-stu-id="164bb-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="164bb-135">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="164bb-135">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService
{
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)
   {
      return Task<string>.Factory.StartNew(() =>
      {
         return msg;
      });
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="164bb-136">L’opération SampleMethodTaskAsync retourne Task\<string>, car l’opération logique retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="164bb-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="164bb-137">Pour plus d'informations sur le modèle asynchrone basé sur des tâches, consultez [Modèle asynchrone basé sur des tâches](https://go.microsoft.com/fwlink/?LinkId=232504).</span><span class="sxs-lookup"><span data-stu-id="164bb-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="164bb-138">Lorsque vous utilisez le modèle asynchrone basé sur des tâches, une exception T:System.AggregateException peut être levée si une exception se produit lors de l’attente de la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="164bb-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="164bb-139">Cette exception peut se produire sur le client ou les services.</span><span class="sxs-lookup"><span data-stu-id="164bb-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="164bb-140">Modèle asynchrone basé sur des événements</span><span class="sxs-lookup"><span data-stu-id="164bb-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="164bb-141">Un service prenant en charge le modèle asynchrone basé sur des événements possédera une ou plusieurs opérations nommées MethodNameAsync.</span><span class="sxs-lookup"><span data-stu-id="164bb-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="164bb-142">Ces méthodes peuvent refléter des versions synchrones qui exécutent la même opération sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="164bb-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="164bb-143">La classe peut également posséder un événement MethodNameCompleted et une méthode MethodNameAsyncCancel (ou simplement CancelAsync).</span><span class="sxs-lookup"><span data-stu-id="164bb-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="164bb-144">Un client souhaitant appeler l'opération définira un gestionnaire d'événements à appeler lorsque l'opération se termine.</span><span class="sxs-lookup"><span data-stu-id="164bb-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="164bb-145">L'extrait de code suivant montre comment déclarer des opérations asynchrones à l'aide du modèle asynchrone basé sur des événements.</span><span class="sxs-lookup"><span data-stu-id="164bb-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="164bb-146">Pour plus d'informations sur le modèle asynchrone basé sur des événements, consultez [Modèle asynchrone basé sur des événements](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="164bb-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="164bb-147">Modèle asynchrone IAsyncResult</span><span class="sxs-lookup"><span data-stu-id="164bb-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="164bb-148">Une opération de service peut être mise en œuvre d’une manière asynchrone en utilisant le modèle de programmation asynchrone .NET Framework et le marquage de la `<Begin>` méthode avec la <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> propriété définie à `true`.</span><span class="sxs-lookup"><span data-stu-id="164bb-148">A service operation can be implemented in an asynchronous fashion using the .NET Framework asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="164bb-149">Dans ce cas, l'opération asynchrone est exposée dans les métadonnées sous la forme d'une opération synchrone: Elle est exposée comme une seule opération avec un message de demande et un message de réponse corrélé.</span><span class="sxs-lookup"><span data-stu-id="164bb-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="164bb-150">Les modèles de programmation clients doivent ensuite choisir entre deux options.</span><span class="sxs-lookup"><span data-stu-id="164bb-150">Client programming models then have a choice.</span></span> <span data-ttu-id="164bb-151">Ils peuvent représenter ce modèle comme une opération synchrone ou asynchrone, tant qu'un échange de messages de réponse-demande a lieu lorsque le service est appelé.</span><span class="sxs-lookup"><span data-stu-id="164bb-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="164bb-152">En général, avec la nature asynchrone des systèmes, vous ne devez pas exploiter de dépendance sur les threads.</span><span class="sxs-lookup"><span data-stu-id="164bb-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="164bb-153">La méthode la plus fiable pour transmettre des données à différentes étapes du traitement de la distribution des opérations consiste à utiliser les extensions.</span><span class="sxs-lookup"><span data-stu-id="164bb-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="164bb-154">Pour voir un exemple, consultez [Guide pratique pour implémenter une opération de service asynchrone](how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="164bb-154">For an example, see [How to: Implement an Asynchronous Service Operation](how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="164bb-155">Pour définir une opération de contrat `X` exécutée de façon asynchrone quelle que soit la manière dont elle est appelée dans l'application cliente :</span><span class="sxs-lookup"><span data-stu-id="164bb-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
- <span data-ttu-id="164bb-156">Définissez deux méthodes à l’aide du modèle `BeginOperation` et `EndOperation`.</span><span class="sxs-lookup"><span data-stu-id="164bb-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
- <span data-ttu-id="164bb-157">La méthode `BeginOperation` inclut les paramètres `in` et `ref` pour l'opération et retourne un type <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="164bb-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
- <span data-ttu-id="164bb-158">La méthode `EndOperation` inclut un paramètre <xref:System.IAsyncResult> ainsi que les paramètres `out` et `ref` et elle retourne le type de retour des opérations.</span><span class="sxs-lookup"><span data-stu-id="164bb-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="164bb-159">Par exemple, reportez-vous à la méthode suivante :</span><span class="sxs-lookup"><span data-stu-id="164bb-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="164bb-160">Voici les deux méthodes pour créer une opération asynchrone :</span><span class="sxs-lookup"><span data-stu-id="164bb-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
> <span data-ttu-id="164bb-161">L'attribut <xref:System.ServiceModel.OperationContractAttribute> est appliqué uniquement à la méthode `BeginDoWork`.</span><span class="sxs-lookup"><span data-stu-id="164bb-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="164bb-162">Le contrat obtenu a une opération WSDL nommée `DoWork`.</span><span class="sxs-lookup"><span data-stu-id="164bb-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="164bb-163">Appels asynchrones côté client</span><span class="sxs-lookup"><span data-stu-id="164bb-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="164bb-164">Une application cliente WCF peut utiliser un des modèles d'appel asynchrone décrits précédemment</span><span class="sxs-lookup"><span data-stu-id="164bb-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="164bb-165">Lors de l'utilisation du modèle basé sur des tâches, appelez simplement l'opération en utilisant le mot clé await comme indiqué dans l'extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="164bb-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="164bb-166">L’utilisation du modèle asynchrone basé sur des événements ne nécessite que l’ajout d’un gestionnaire d’événements pour recevoir une notification de la réponse, et l’événement résultant est déclenché automatiquement sur le thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="164bb-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="164bb-167">Pour utiliser cette approche, spécifiez les options de commande **/async** et **/tcv:Version35** avec l’[outil Service Model Metadata Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="164bb-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="164bb-168">Au terme de cette opération, l'outil Svcutil.exe génère une classe cliente WCF avec l'infrastructure d'événement qui permet à l'application appelante d'implémenter et d'affecter un gestionnaire d'événements de recevoir la réponse et prendre la mesure appropriée.</span><span class="sxs-lookup"><span data-stu-id="164bb-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="164bb-169">Pour voir un exemple complet, consultez [Guide pratique pour appeler des opérations de service de façon asynchrone](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="164bb-169">For a complete example, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="164bb-170">Le modèle asynchrone basé sur l’événement, cependant, n’est disponible que dans .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="164bb-170">The event-based asynchronous model, however, is only available in .NET Framework 3.5.</span></span> <span data-ttu-id="164bb-171">En outre, il n’est pas pris en charge, même dans .NET Framework <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>3.5 quand un canal client WCF est créé en utilisant un .</span><span class="sxs-lookup"><span data-stu-id="164bb-171">In addition, it is not supported even in .NET Framework 3.5 when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="164bb-172">Avec les objets de canal client WCF, vous devez utiliser des objets <xref:System.IAsyncResult?displayProperty=nameWithType> pour appeler vos opérations de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="164bb-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="164bb-173">Pour utiliser cette approche, spécifiez l'option de commande **async** avec l’[outil ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="164bb-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async
```  
  
 <span data-ttu-id="164bb-174">Vous générez ainsi un contrat de service dans lequel chaque opération est modelée comme une méthode `<Begin>` et où la propriété <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> a la valeur `true` et une méthode correspondante `<End>`.</span><span class="sxs-lookup"><span data-stu-id="164bb-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="164bb-175">Pour voir un exemple complet utilisant une <xref:System.ServiceModel.ChannelFactory%601>, consultez [Guide pratique pour appeler des opérations de façon asynchrone à l’aide d’une fabrique de canaux](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="164bb-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="164bb-176">Dans l'un ou l'autre cas, les applications peuvent appeler une opération de façon asynchrone même si le service est implémenté de façon synchrone, de la même façon qu'une application peut utiliser le même modèle pour appeler une méthode synchrone locale de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="164bb-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="164bb-177">La façon dont l’opération est mise en œuvre n’est pas importante pour le client; lorsque le message de réponse arrive, son contenu est envoyé à la `End` méthode asynchrone <> du client et le client récupère l’information.</span><span class="sxs-lookup"><span data-stu-id="164bb-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="164bb-178">Modèles d’échange de messages unidirectionnels</span><span class="sxs-lookup"><span data-stu-id="164bb-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="164bb-179">Vous pouvez également créer un modèle d'échange de messages asynchrone dans lequel les opérations unidirectionnelles (les opérations pour lesquelles <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> a la valeur `true` n'ont aucune réponse corrélée) peuvent être envoyées dans chaque direction par le client ou le service, indépendamment du côté opposé.</span><span class="sxs-lookup"><span data-stu-id="164bb-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="164bb-180">(Cela utilise le modèle d’échange de messages en duplex avec des messages à sens unique.) Dans ce cas, le contrat de service spécifie un échange de messages à sens unique que l’une ou l’autre partie peut mettre en œuvre comme des appels ou des implémentations asynchrones, ou non, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="164bb-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="164bb-181">En général, lorsque le contrat est un échange de messages unidirectionnels, les implémentations sont en grande partie asynchrones car, après l'envoi d'un message, l'application n'attend pas de réponse et peut continuer à effectuer d'autres tâches.</span><span class="sxs-lookup"><span data-stu-id="164bb-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="164bb-182">Contrats de message et clients asynchrones basés sur les événements</span><span class="sxs-lookup"><span data-stu-id="164bb-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="164bb-183">Les règles de conception pour le modèle asynchrone basé sur les événements stipulent que si plusieurs valeurs sont retournées, une valeur est retournée comme la propriété `Result` et les autres sont retournées comme les propriétés sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="164bb-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="164bb-184">Il en découle que si un client importe des métadonnées à l'aide des options de commande asynchrone basées sur les événements et que l'opération retourne plusieurs valeurs, l'objet <xref:System.EventArgs> par défaut retourne une valeur comme la propriété `Result` et le reste sont des propriétés de l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="164bb-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="164bb-185">Pour recevoir l'objet message comme propriété `Result` et pour que les valeurs retournées sur cet objet soient des propriétés, utilisez l'option de commande **/messageContract**.</span><span class="sxs-lookup"><span data-stu-id="164bb-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="164bb-186">Cette opération génère une signature qui retourne le message de réponse comme la propriété `Result` sur l'objet <xref:System.EventArgs>.</span><span class="sxs-lookup"><span data-stu-id="164bb-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="164bb-187">Toutes les valeurs de retour internes sont ensuite des propriétés de l'objet de message de réponse.</span><span class="sxs-lookup"><span data-stu-id="164bb-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="164bb-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="164bb-188">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
