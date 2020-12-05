---
title: Source de l’événement BinaryFormatter
description: Découvrez comment utiliser la source d’événements BinaryFormatter pour le journal lors de la sérialisation ou de la désérialisation.
ms.date: 12/03/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: 9ae2af77b6cfc270207fb0f2969ada8c2eca1153
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740419"
---
# <a name="binaryformatter-event-source"></a><span data-ttu-id="f35d1-103">Source de l’événement BinaryFormatter</span><span class="sxs-lookup"><span data-stu-id="f35d1-103">BinaryFormatter event source</span></span>

<span data-ttu-id="f35d1-104">À compter de .NET 5,0, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> inclut un intégré <xref:System.Diagnostics.Tracing.EventSource> qui vous donne une visibilité sur le moment où la sérialisation ou la désérialisation d’un objet se produit.</span><span class="sxs-lookup"><span data-stu-id="f35d1-104">Starting with .NET 5.0, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> includes a built-in <xref:System.Diagnostics.Tracing.EventSource> that gives you visibility into when an object serialization or deserialization is occurring.</span></span> <span data-ttu-id="f35d1-105">Les applications peuvent utiliser des <xref:System.Diagnostics.Tracing.EventListener> types dérivés de pour écouter ces notifications et les enregistrer.</span><span class="sxs-lookup"><span data-stu-id="f35d1-105">Apps can use <xref:System.Diagnostics.Tracing.EventListener>-derived types to listen for these notifications and log them.</span></span>

<span data-ttu-id="f35d1-106">Cette fonctionnalité n’est pas un substitut à <xref:System.Runtime.Serialization.SerializationBinder> ou <xref:System.Runtime.Serialization.ISerializationSurrogate> à et ne peut pas être utilisée pour modifier les données qui sont sérialisées ou désérialisées.</span><span class="sxs-lookup"><span data-stu-id="f35d1-106">This functionality is not a substitute for a <xref:System.Runtime.Serialization.SerializationBinder> or an <xref:System.Runtime.Serialization.ISerializationSurrogate> and can't be used to modify the data being serialized or deserialized.</span></span> <span data-ttu-id="f35d1-107">Au lieu de cela, ce système d’événement est destiné à fournir des informations sur les types qui sont sérialisés ou désérialisés.</span><span class="sxs-lookup"><span data-stu-id="f35d1-107">Rather, this eventing system is intended to provide insight into the types being serialized or deserialized.</span></span> <span data-ttu-id="f35d1-108">Il peut également être utilisé pour détecter les appels inattendus dans l' `BinaryFormatter` infrastructure, tels que les appels provenant d’un code de bibliothèque tiers.</span><span class="sxs-lookup"><span data-stu-id="f35d1-108">It can also be used to detect unintended calls into the `BinaryFormatter` infrastructure, such as calls originating from third-party library code.</span></span>

## <a name="description-of-events"></a><span data-ttu-id="f35d1-109">Description des événements</span><span class="sxs-lookup"><span data-stu-id="f35d1-109">Description of events</span></span>

<span data-ttu-id="f35d1-110">La `BinaryFormatter` source de l’événement a le nom connu `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource` .</span><span class="sxs-lookup"><span data-stu-id="f35d1-110">The `BinaryFormatter` event source has the well-known name `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource`.</span></span> <span data-ttu-id="f35d1-111">Les écouteurs peuvent s’abonner à 6 événements.</span><span class="sxs-lookup"><span data-stu-id="f35d1-111">Listeners may subscribe to 6 events.</span></span>

### <a name="serializationstart-event-id--10"></a><span data-ttu-id="f35d1-112">Événement SerializationStart (ID = `10` )</span><span class="sxs-lookup"><span data-stu-id="f35d1-112">SerializationStart event (id = `10`)</span></span>

<span data-ttu-id="f35d1-113">Déclenché quand <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> a été appelé et a démarré le processus de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="f35d1-113">Raised when <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> has been called and has started the serialization process.</span></span> <span data-ttu-id="f35d1-114">Cet événement est associé à l' `SerializationEnd` événement.</span><span class="sxs-lookup"><span data-stu-id="f35d1-114">This event is paired with the `SerializationEnd` event.</span></span> <span data-ttu-id="f35d1-115">L' `SerializationStart` événement peut être appelé de manière récursive si un objet appelle `BinaryFormatter.Serialize` dans sa propre routine de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="f35d1-115">The `SerializationStart` event can be called recursively if an object calls `BinaryFormatter.Serialize` within its own serialization routine.</span></span>

<span data-ttu-id="f35d1-116">Cet événement ne contient pas de charge utile.</span><span class="sxs-lookup"><span data-stu-id="f35d1-116">This event doesn't contain a payload.</span></span>

### <a name="serializationend-event-id--11"></a><span data-ttu-id="f35d1-117">Événement SerializationEnd (ID = `11` )</span><span class="sxs-lookup"><span data-stu-id="f35d1-117">SerializationEnd event (id = `11`)</span></span>

<span data-ttu-id="f35d1-118">Déclenché quand `BinaryFormatter.Serialize` a terminé son travail.</span><span class="sxs-lookup"><span data-stu-id="f35d1-118">Raised when `BinaryFormatter.Serialize` has completed its work.</span></span> <span data-ttu-id="f35d1-119">Chaque occurrence de `SerializationEnd` indique l’achèvement du dernier événement non couplé `SerializationStart` .</span><span class="sxs-lookup"><span data-stu-id="f35d1-119">Each occurrence of `SerializationEnd` denotes the completion of the last unpaired `SerializationStart` event.</span></span>

<span data-ttu-id="f35d1-120">Cet événement ne contient pas de charge utile.</span><span class="sxs-lookup"><span data-stu-id="f35d1-120">This event doesn't contain a payload.</span></span>

### <a name="serializingobject-event-id--12"></a><span data-ttu-id="f35d1-121">Événement SerializingObject (ID = `12` )</span><span class="sxs-lookup"><span data-stu-id="f35d1-121">SerializingObject event (id = `12`)</span></span>

<span data-ttu-id="f35d1-122">Levée lorsque `BinaryFormatter.Serialize` se trouve dans le processus de sérialisation d’un type non primitif.</span><span class="sxs-lookup"><span data-stu-id="f35d1-122">Raised when `BinaryFormatter.Serialize` is in the process of serializing a non-primitive type.</span></span> <span data-ttu-id="f35d1-123">Les `BinaryFormatter` cas spéciaux de l’infrastructure sont certains types (tels que `string` et `int` ) et ne déclenchent pas cet événement lorsque ces types sont rencontrés.</span><span class="sxs-lookup"><span data-stu-id="f35d1-123">The `BinaryFormatter` infrastructure special-cases certain types (such as `string` and `int`) and doesn't raise this event when these types are encountered.</span></span> <span data-ttu-id="f35d1-124">Cet événement est déclenché pour les types définis par l’utilisateur et d’autres types qui `BinaryFormatter` ne sont pas compris en mode natif.</span><span class="sxs-lookup"><span data-stu-id="f35d1-124">This event is raised for user-defined types and other types that `BinaryFormatter` doesn't natively understand.</span></span>

<span data-ttu-id="f35d1-125">Cet événement peut être déclenché zéro ou plusieurs fois entre `SerializationStart` les `SerializationEnd` événements et.</span><span class="sxs-lookup"><span data-stu-id="f35d1-125">This event may be raised zero or more times between `SerializationStart` and `SerializationEnd` events.</span></span>

<span data-ttu-id="f35d1-126">Cet événement contient une charge utile avec un argument :</span><span class="sxs-lookup"><span data-stu-id="f35d1-126">This event contains a payload with one argument:</span></span>

* <span data-ttu-id="f35d1-127">`typeName` ( `string` ) : Nom qualifié d’assembly (consultez <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> ) du type en cours de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="f35d1-127">`typeName` (`string`): The assembly-qualified name (see <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>) of the type being serialized.</span></span>

### <a name="deserializationstart-event-id--20"></a><span data-ttu-id="f35d1-128">Événement DeserializationStart (ID = `20` )</span><span class="sxs-lookup"><span data-stu-id="f35d1-128">DeserializationStart event (id = `20`)</span></span>

<span data-ttu-id="f35d1-129">Déclenché quand <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> a été appelé et a démarré le processus de désérialisation.</span><span class="sxs-lookup"><span data-stu-id="f35d1-129">Raised when <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> has been called and has started the deserialization process.</span></span> <span data-ttu-id="f35d1-130">Cet événement est associé à l' `DeserializationEnd` événement.</span><span class="sxs-lookup"><span data-stu-id="f35d1-130">This event is paired with the `DeserializationEnd` event.</span></span> <span data-ttu-id="f35d1-131">L' `DeserializationStart` événement peut être appelé de manière récursive si un objet appelle `BinaryFormatter.Deserialize` dans sa propre routine de désérialisation.</span><span class="sxs-lookup"><span data-stu-id="f35d1-131">The `DeserializationStart` event can be called recursively if an object calls `BinaryFormatter.Deserialize` within its own deserialization routine.</span></span>

<span data-ttu-id="f35d1-132">Cet événement ne contient pas de charge utile.</span><span class="sxs-lookup"><span data-stu-id="f35d1-132">This event doesn't contain a payload.</span></span>

### <a name="deserializationend-event-id--21"></a><span data-ttu-id="f35d1-133">Événement DeserializationEnd (ID = `21` )</span><span class="sxs-lookup"><span data-stu-id="f35d1-133">DeserializationEnd event (id = `21`)</span></span>

<span data-ttu-id="f35d1-134">Déclenché quand `BinaryFormatter.Deserialize` a terminé son travail.</span><span class="sxs-lookup"><span data-stu-id="f35d1-134">Raised when `BinaryFormatter.Deserialize` has completed its work.</span></span> <span data-ttu-id="f35d1-135">Chaque occurrence de `DeserializationEnd` indique l’achèvement du dernier événement non couplé `DeserializationStart` .</span><span class="sxs-lookup"><span data-stu-id="f35d1-135">Each occurrence of `DeserializationEnd` denotes the completion of the last unpaired `DeserializationStart` event.</span></span>

<span data-ttu-id="f35d1-136">Cet événement ne contient pas de charge utile.</span><span class="sxs-lookup"><span data-stu-id="f35d1-136">This event doesn't contain a payload.</span></span>

### <a name="deserializingobject-event-id--22"></a><span data-ttu-id="f35d1-137">Événement DeserializingObject (ID = `22` )</span><span class="sxs-lookup"><span data-stu-id="f35d1-137">DeserializingObject event (id = `22`)</span></span>

<span data-ttu-id="f35d1-138">Levée lorsque `BinaryFormatter.Deserialize` se trouve dans le processus de désérialisation d’un type non primitif.</span><span class="sxs-lookup"><span data-stu-id="f35d1-138">Raised when `BinaryFormatter.Deserialize` is in the process of deserializing a non-primitive type.</span></span> <span data-ttu-id="f35d1-139">Les `BinaryFormatter` cas spéciaux de l’infrastructure sont certains types (tels que `string` et `int` ) et ne déclenchent pas cet événement lorsque ces types sont rencontrés.</span><span class="sxs-lookup"><span data-stu-id="f35d1-139">The `BinaryFormatter` infrastructure special-cases certain types (such as `string` and `int`) and doesn't raise this event when these types are encountered.</span></span> <span data-ttu-id="f35d1-140">Cet événement est déclenché pour les types définis par l’utilisateur et d’autres types qui `BinaryFormatter` ne sont pas compris en mode natif.</span><span class="sxs-lookup"><span data-stu-id="f35d1-140">This event is raised for user-defined types and other types that `BinaryFormatter` doesn't natively understand.</span></span>

<span data-ttu-id="f35d1-141">Cet événement peut être déclenché zéro ou plusieurs fois entre `DeserializationStart` les `DeserializationEnd` événements et.</span><span class="sxs-lookup"><span data-stu-id="f35d1-141">This event may be raised zero or more times between `DeserializationStart` and `DeserializationEnd` events.</span></span>

<span data-ttu-id="f35d1-142">Cet événement contient une charge utile avec un seul argument.</span><span class="sxs-lookup"><span data-stu-id="f35d1-142">This event contains a payload with one argument.</span></span>

* <span data-ttu-id="f35d1-143">`typeName` ( `string` ) : Nom qualifié d’assembly (consultez <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> ) du type en cours de désérialisation.</span><span class="sxs-lookup"><span data-stu-id="f35d1-143">`typeName` (`string`): The assembly-qualified name (see <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType>) of the type being deserialized.</span></span>

### <a name="advanced-subscribing-to-a-subset-of-notifications"></a><span data-ttu-id="f35d1-144">\[\]Abonnement avancé à un sous-ensemble de notifications</span><span class="sxs-lookup"><span data-stu-id="f35d1-144">\[Advanced\] Subscribing to a subset of notifications</span></span>

<span data-ttu-id="f35d1-145">Les écouteurs qui souhaitent s’abonner à un sous-ensemble de notifications peuvent choisir les mots clés à activer.</span><span class="sxs-lookup"><span data-stu-id="f35d1-145">Listeners who wish to subscribe to only a subset of notifications can choose which keywords to enable.</span></span>

* <span data-ttu-id="f35d1-146">`Serialization` = `(EventKeywords)1`: Déclenche les `SerializationStart` `SerializationEnd` événements, et `SerializingObject` .</span><span class="sxs-lookup"><span data-stu-id="f35d1-146">`Serialization` = `(EventKeywords)1`: Raises the `SerializationStart`, `SerializationEnd`, and `SerializingObject` events.</span></span>
* <span data-ttu-id="f35d1-147">`Deserialization` = `(EventKeywords)2`: Déclenche les `DeserializationStart` `DeserializationEnd` événements, et `DeserializingObject` .</span><span class="sxs-lookup"><span data-stu-id="f35d1-147">`Deserialization` = `(EventKeywords)2`: Raises the `DeserializationStart`, `DeserializationEnd`, and `DeserializingObject` events.</span></span>

<span data-ttu-id="f35d1-148">Si aucun filtre de mot clé n’est fourni lors `EventListener` de l’inscription, tous les événements sont déclenchés.</span><span class="sxs-lookup"><span data-stu-id="f35d1-148">If no keyword filters are provided during `EventListener` registration, all events are raised.</span></span>

<span data-ttu-id="f35d1-149">Pour plus d’informations, consultez <xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f35d1-149">For more information, see <xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>.</span></span>

## <a name="sample-code"></a><span data-ttu-id="f35d1-150">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="f35d1-150">Sample code</span></span>

<span data-ttu-id="f35d1-151">Le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f35d1-151">The following code:</span></span>

- <span data-ttu-id="f35d1-152">crée un `EventListener` type dérivé de qui écrit dans `System.Console` ,</span><span class="sxs-lookup"><span data-stu-id="f35d1-152">creates an `EventListener`-derived type that writes to `System.Console`,</span></span>
- <span data-ttu-id="f35d1-153">abonne cet écouteur à `BinaryFormatter` des notifications produites,</span><span class="sxs-lookup"><span data-stu-id="f35d1-153">subscribes that listener to `BinaryFormatter`-produced notifications,</span></span>
- <span data-ttu-id="f35d1-154">sérialise et désérialise un graphique d’objets simple à l’aide de `BinaryFormatter` , et</span><span class="sxs-lookup"><span data-stu-id="f35d1-154">serializes and deserializes a simple object graph using `BinaryFormatter`, and</span></span>
- <span data-ttu-id="f35d1-155">analyse les événements qui ont été déclenchés.</span><span class="sxs-lookup"><span data-stu-id="f35d1-155">analyzes the events that have been raised.</span></span>

:::code language="csharp" source="snippets/binaryformatter-event-source/csharp/Program.cs":::

<span data-ttu-id="f35d1-156">Le code précédent produit une sortie similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f35d1-156">The preceding code produces output similar to the following example:</span></span>

```output
Event SerializationStart (id=10) received.
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializingObject (id=12) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event SerializationStop (id=11) received.
Event DeserializationStart (id=20) received.
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Person, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializingObject (id=22) received.
typeName = BinaryFormatterEventSample.Book, BinaryFormatterEventSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
Event DeserializationStop (id=21) received.
Rehydrated person Logan Edwards
Favorite book: A Tale of Two Cities by Charles Dickens, list price 10.25
```

<span data-ttu-id="f35d1-157">Dans cet exemple, les journaux basés sur la console `EventListener` que la sérialisation démarre, les instances de `Person` et `Book` sont sérialisés, puis la sérialisation se termine.</span><span class="sxs-lookup"><span data-stu-id="f35d1-157">In this sample, the console-based `EventListener` logs that serialization starts, instances of `Person` and `Book` are serialized, and then serialization completes.</span></span> <span data-ttu-id="f35d1-158">De même, une fois que la désérialisation a démarré, les instances de `Person` et `Book` sont désérialisées, puis la désérialisation se termine.</span><span class="sxs-lookup"><span data-stu-id="f35d1-158">Similarly, once deserialization has started, instances of `Person` and `Book` are deserialized, and then deserialization completes.</span></span>

<span data-ttu-id="f35d1-159">L’application imprime ensuite les valeurs contenues dans le désérialisé `Person` pour montrer que l’objet a été correctement sérialisé et désérialisé.</span><span class="sxs-lookup"><span data-stu-id="f35d1-159">The app then prints the values contained in the deserialized `Person` to demonstrate that the object did in fact serialize and deserialize properly.</span></span>

## <a name="see-also"></a><span data-ttu-id="f35d1-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f35d1-160">See also</span></span>

<span data-ttu-id="f35d1-161">Pour plus d’informations sur l’utilisation `EventListener` de pour recevoir `EventSource` des notifications basées sur, consultez [la `EventListener` classe](xref:System.Diagnostics.Tracing.EventListener).</span><span class="sxs-lookup"><span data-stu-id="f35d1-161">For more information on using `EventListener` to receive `EventSource`-based notifications, see [the `EventListener` class](xref:System.Diagnostics.Tracing.EventListener).</span></span>
