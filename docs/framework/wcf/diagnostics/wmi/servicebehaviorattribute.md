---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: e3716d42d479bcbdfd900b4fd2e335576a71574b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295598"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="e68fa-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="e68fa-102">ServiceBehaviorAttribute</span></span>

<span data-ttu-id="e68fa-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="e68fa-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e68fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e68fa-104">Syntax</span></span>  
  
```csharp
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e68fa-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e68fa-105">Methods</span></span>  

 <span data-ttu-id="e68fa-106">La classe ServiceBehaviorAttribute ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="e68fa-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e68fa-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e68fa-107">Properties</span></span>  

 <span data-ttu-id="e68fa-108">La classe ServiceBehaviorAttribute a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="e68fa-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="e68fa-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="e68fa-109">AutomaticSessionShutdown</span></span>  

 <span data-ttu-id="e68fa-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="e68fa-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e68fa-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-112">Indique s'il faut fermer automatiquement une session lorsqu'un client ferme une session de sortie.</span><span class="sxs-lookup"><span data-stu-id="e68fa-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="e68fa-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="e68fa-113">ConcurrencyMode</span></span>  

 <span data-ttu-id="e68fa-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e68fa-114">Data type: string</span></span>  
<span data-ttu-id="e68fa-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-116">Indique si un service prend en charge un thread, plusieurs threads ou des appels réentrants.</span><span class="sxs-lookup"><span data-stu-id="e68fa-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="e68fa-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="e68fa-117">ConfigurationName</span></span>  

 <span data-ttu-id="e68fa-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e68fa-118">Data type: string</span></span>  
  
 <span data-ttu-id="e68fa-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-120">Nom de la configuration du service.</span><span class="sxs-lookup"><span data-stu-id="e68fa-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="e68fa-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="e68fa-121">IgnoreExtensionDataObject</span></span>  

 <span data-ttu-id="e68fa-122">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="e68fa-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="e68fa-123">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-124">Spécifie s'il faut envoyer des données de sérialisation inconnues sur le câble.</span><span class="sxs-lookup"><span data-stu-id="e68fa-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="e68fa-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="e68fa-125">IncludeExceptionDetailInFaults</span></span>  

 <span data-ttu-id="e68fa-126">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="e68fa-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="e68fa-127">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-128">Spécifie s'il convient d'inclure des informations d'exception gérées dans les détails des fautes SOAP renvoyées aux clients à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="e68fa-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="e68fa-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="e68fa-129">InstanceContextMode</span></span>  

 <span data-ttu-id="e68fa-130">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e68fa-130">Data type: string</span></span>  
  
 <span data-ttu-id="e68fa-131">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-132">Spécifie quand un nouvel objet de service est créé.</span><span class="sxs-lookup"><span data-stu-id="e68fa-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="e68fa-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="e68fa-133">MaxItemsInObjectGraph</span></span>  

 <span data-ttu-id="e68fa-134">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="e68fa-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="e68fa-135">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-136">Nombre maximal d'éléments autorisés dans un objet sérialisé.</span><span class="sxs-lookup"><span data-stu-id="e68fa-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="e68fa-137">Nom</span><span class="sxs-lookup"><span data-stu-id="e68fa-137">Name</span></span>  

 <span data-ttu-id="e68fa-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e68fa-138">Data type: string</span></span>  
  
 <span data-ttu-id="e68fa-139">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-140">Attribut de nom du service dans WSDL.</span><span class="sxs-lookup"><span data-stu-id="e68fa-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="e68fa-141">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="e68fa-141">Namespace</span></span>  

 <span data-ttu-id="e68fa-142">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e68fa-142">Data type: string</span></span>  
  
 <span data-ttu-id="e68fa-143">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-144">Espace de noms cible du service dans WSDL.</span><span class="sxs-lookup"><span data-stu-id="e68fa-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="e68fa-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="e68fa-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  

 <span data-ttu-id="e68fa-146">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="e68fa-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="e68fa-147">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-148">Spécifie si l’objet de service est recyclé lorsque la transaction actuelle se termine.</span><span class="sxs-lookup"><span data-stu-id="e68fa-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="e68fa-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="e68fa-149">TransactionAutoCompleteOnSessionClose</span></span>  

 <span data-ttu-id="e68fa-150">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="e68fa-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="e68fa-151">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-152">Spécifie si les transactions en attente sont complétées lorsque la session actuelle se ferme.</span><span class="sxs-lookup"><span data-stu-id="e68fa-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="e68fa-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="e68fa-153">TransactionIsolationLevel</span></span>  

 <span data-ttu-id="e68fa-154">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e68fa-154">Data type: string</span></span>  
  
 <span data-ttu-id="e68fa-155">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-156">Spécifie le niveau d’isolation de la transaction.</span><span class="sxs-lookup"><span data-stu-id="e68fa-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="e68fa-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="e68fa-157">TransactionTimeout</span></span>  

 <span data-ttu-id="e68fa-158">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="e68fa-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="e68fa-159">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-160">Période pendant laquelle une transaction doit s’effectuer.</span><span class="sxs-lookup"><span data-stu-id="e68fa-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="e68fa-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="e68fa-161">UseSynchronizationContext</span></span>  

 <span data-ttu-id="e68fa-162">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="e68fa-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="e68fa-163">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-164">Spécifie s’il faut utiliser le contexte de synchronisation actuel pour choisir l’exécution d’un thread.</span><span class="sxs-lookup"><span data-stu-id="e68fa-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="e68fa-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="e68fa-165">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="e68fa-166">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="e68fa-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="e68fa-167">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="e68fa-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e68fa-168">Spécifie si le système ou l'application applique le traitement d'en-tête SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="e68fa-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e68fa-169">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e68fa-169">Requirements</span></span>  
  
|<span data-ttu-id="e68fa-170">MOF</span><span class="sxs-lookup"><span data-stu-id="e68fa-170">MOF</span></span>|<span data-ttu-id="e68fa-171">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e68fa-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e68fa-172">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="e68fa-172">Namespace</span></span>|<span data-ttu-id="e68fa-173">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e68fa-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e68fa-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e68fa-174">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
