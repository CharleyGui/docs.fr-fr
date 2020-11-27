---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 48d26bfa9074fd605e3545579f0bdc2744dfc7d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267857"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="99709-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="99709-102">MsmqBindingElementBase</span></span>

<span data-ttu-id="99709-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="99709-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99709-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99709-104">Syntax</span></span>  
  
```csharp  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="99709-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="99709-105">Methods</span></span>  

 <span data-ttu-id="99709-106">La classe MsmqBindingElementBase ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="99709-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="99709-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="99709-107">Properties</span></span>  

 <span data-ttu-id="99709-108">La classe MsmqBindingElementBase a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="99709-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="99709-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="99709-109">CustomDeadLetterQueue</span></span>  

 <span data-ttu-id="99709-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="99709-110">Data type: string</span></span>  
  
 <span data-ttu-id="99709-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-112">URI qui contient l'emplacement de la file d'attente de lettres mortes pour chaque application, dans laquelle les messages expirés ou dont le transfert ou la remise a échoué sont placés.</span><span class="sxs-lookup"><span data-stu-id="99709-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="99709-113">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="99709-113">DeadLetterQueue</span></span>  

 <span data-ttu-id="99709-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="99709-114">Data type: string</span></span>  
  
 <span data-ttu-id="99709-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-116">Valeur d'énumération qui indique le type de la file d'attente de lettres mortes à utiliser.</span><span class="sxs-lookup"><span data-stu-id="99709-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="99709-117">Durable</span><span class="sxs-lookup"><span data-stu-id="99709-117">Durable</span></span>  

 <span data-ttu-id="99709-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="99709-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="99709-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-120">Valeur qui indique si les messages traités par cette liaison sont durables ou volatils.</span><span class="sxs-lookup"><span data-stu-id="99709-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="99709-121">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="99709-121">ExactlyOnce</span></span>  

 <span data-ttu-id="99709-122">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="99709-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="99709-123">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-124">Valeur booléenne qui indique si les messages traités par cette liaison sont reçus exactement une fois.</span><span class="sxs-lookup"><span data-stu-id="99709-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="99709-125">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="99709-125">MaxRetryCycles</span></span>  

 <span data-ttu-id="99709-126">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="99709-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="99709-127">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-128">Nombre maximal de cycles de nouvelle tentative de livraison de messages à l'application de réception.</span><span class="sxs-lookup"><span data-stu-id="99709-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="99709-129">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="99709-129">ReceiveErrorHandling</span></span>  

 <span data-ttu-id="99709-130">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="99709-130">Data type: string</span></span>  
  
 <span data-ttu-id="99709-131">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-132">Paramètres de gestion de messages incohérents.</span><span class="sxs-lookup"><span data-stu-id="99709-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="99709-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="99709-133">ReceiveRetryCount</span></span>  

 <span data-ttu-id="99709-134">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="99709-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="99709-135">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-136">Nombre maximal de nouvelles tentatives immédiates sur un message qui est lu à partir de la file d'attente d'application.</span><span class="sxs-lookup"><span data-stu-id="99709-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="99709-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="99709-137">RetryCycleDelay</span></span>  

 <span data-ttu-id="99709-138">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="99709-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="99709-139">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-140">Valeur qui indique l'intervalle entre des cycles de nouvelle tentative de remise d'un message n'ayant pas pu être remis immédiatement.</span><span class="sxs-lookup"><span data-stu-id="99709-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="99709-141">timeToLive</span><span class="sxs-lookup"><span data-stu-id="99709-141">TimeToLive</span></span>  

 <span data-ttu-id="99709-142">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="99709-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="99709-143">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-144">Intervalle qui indique combien de temps les messages traités par cette liaison peuvent séjourner dans la file d’attente avant expiration.</span><span class="sxs-lookup"><span data-stu-id="99709-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="99709-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="99709-145">UseMsmqTracing</span></span>  

 <span data-ttu-id="99709-146">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="99709-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="99709-147">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-148">Valeur booléenne qui indique si les messages traités par cette liaison doivent être suivis.</span><span class="sxs-lookup"><span data-stu-id="99709-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="99709-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="99709-149">UseSourceJournal</span></span>  

 <span data-ttu-id="99709-150">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="99709-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="99709-151">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="99709-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99709-152">Valeur booléenne qui indique si les copies des messages traités par cette liaison doivent être stockées dans la file d’attente du journal source.</span><span class="sxs-lookup"><span data-stu-id="99709-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99709-153">Spécifications</span><span class="sxs-lookup"><span data-stu-id="99709-153">Requirements</span></span>  
  
|<span data-ttu-id="99709-154">MOF</span><span class="sxs-lookup"><span data-stu-id="99709-154">MOF</span></span>|<span data-ttu-id="99709-155">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="99709-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="99709-156">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="99709-156">Namespace</span></span>|<span data-ttu-id="99709-157">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="99709-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99709-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99709-158">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
