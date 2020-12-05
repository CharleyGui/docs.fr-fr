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
# <a name="binaryformatter-event-source"></a>Source de l’événement BinaryFormatter

À compter de .NET 5,0, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> inclut un intégré <xref:System.Diagnostics.Tracing.EventSource> qui vous donne une visibilité sur le moment où la sérialisation ou la désérialisation d’un objet se produit. Les applications peuvent utiliser des <xref:System.Diagnostics.Tracing.EventListener> types dérivés de pour écouter ces notifications et les enregistrer.

Cette fonctionnalité n’est pas un substitut à <xref:System.Runtime.Serialization.SerializationBinder> ou <xref:System.Runtime.Serialization.ISerializationSurrogate> à et ne peut pas être utilisée pour modifier les données qui sont sérialisées ou désérialisées. Au lieu de cela, ce système d’événement est destiné à fournir des informations sur les types qui sont sérialisés ou désérialisés. Il peut également être utilisé pour détecter les appels inattendus dans l' `BinaryFormatter` infrastructure, tels que les appels provenant d’un code de bibliothèque tiers.

## <a name="description-of-events"></a>Description des événements

La `BinaryFormatter` source de l’événement a le nom connu `System.Runtime.Serialization.Formatters.Binary.BinaryFormatterEventSource` . Les écouteurs peuvent s’abonner à 6 événements.

### <a name="serializationstart-event-id--10"></a>Événement SerializationStart (ID = `10` )

Déclenché quand <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> a été appelé et a démarré le processus de sérialisation. Cet événement est associé à l' `SerializationEnd` événement. L' `SerializationStart` événement peut être appelé de manière récursive si un objet appelle `BinaryFormatter.Serialize` dans sa propre routine de sérialisation.

Cet événement ne contient pas de charge utile.

### <a name="serializationend-event-id--11"></a>Événement SerializationEnd (ID = `11` )

Déclenché quand `BinaryFormatter.Serialize` a terminé son travail. Chaque occurrence de `SerializationEnd` indique l’achèvement du dernier événement non couplé `SerializationStart` .

Cet événement ne contient pas de charge utile.

### <a name="serializingobject-event-id--12"></a>Événement SerializingObject (ID = `12` )

Levée lorsque `BinaryFormatter.Serialize` se trouve dans le processus de sérialisation d’un type non primitif. Les `BinaryFormatter` cas spéciaux de l’infrastructure sont certains types (tels que `string` et `int` ) et ne déclenchent pas cet événement lorsque ces types sont rencontrés. Cet événement est déclenché pour les types définis par l’utilisateur et d’autres types qui `BinaryFormatter` ne sont pas compris en mode natif.

Cet événement peut être déclenché zéro ou plusieurs fois entre `SerializationStart` les `SerializationEnd` événements et.

Cet événement contient une charge utile avec un argument :

* `typeName` ( `string` ) : Nom qualifié d’assembly (consultez <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> ) du type en cours de sérialisation.

### <a name="deserializationstart-event-id--20"></a>Événement DeserializationStart (ID = `20` )

Déclenché quand <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> a été appelé et a démarré le processus de désérialisation. Cet événement est associé à l' `DeserializationEnd` événement. L' `DeserializationStart` événement peut être appelé de manière récursive si un objet appelle `BinaryFormatter.Deserialize` dans sa propre routine de désérialisation.

Cet événement ne contient pas de charge utile.

### <a name="deserializationend-event-id--21"></a>Événement DeserializationEnd (ID = `21` )

Déclenché quand `BinaryFormatter.Deserialize` a terminé son travail. Chaque occurrence de `DeserializationEnd` indique l’achèvement du dernier événement non couplé `DeserializationStart` .

Cet événement ne contient pas de charge utile.

### <a name="deserializingobject-event-id--22"></a>Événement DeserializingObject (ID = `22` )

Levée lorsque `BinaryFormatter.Deserialize` se trouve dans le processus de désérialisation d’un type non primitif. Les `BinaryFormatter` cas spéciaux de l’infrastructure sont certains types (tels que `string` et `int` ) et ne déclenchent pas cet événement lorsque ces types sont rencontrés. Cet événement est déclenché pour les types définis par l’utilisateur et d’autres types qui `BinaryFormatter` ne sont pas compris en mode natif.

Cet événement peut être déclenché zéro ou plusieurs fois entre `DeserializationStart` les `DeserializationEnd` événements et.

Cet événement contient une charge utile avec un seul argument.

* `typeName` ( `string` ) : Nom qualifié d’assembly (consultez <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> ) du type en cours de désérialisation.

### <a name="advanced-subscribing-to-a-subset-of-notifications"></a>\[\]Abonnement avancé à un sous-ensemble de notifications

Les écouteurs qui souhaitent s’abonner à un sous-ensemble de notifications peuvent choisir les mots clés à activer.

* `Serialization` = `(EventKeywords)1`: Déclenche les `SerializationStart` `SerializationEnd` événements, et `SerializingObject` .
* `Deserialization` = `(EventKeywords)2`: Déclenche les `DeserializationStart` `DeserializationEnd` événements, et `DeserializingObject` .

Si aucun filtre de mot clé n’est fourni lors `EventListener` de l’inscription, tous les événements sont déclenchés.

Pour plus d’informations, consultez <xref:System.Diagnostics.Tracing.EventKeywords?displayProperty=nameWithType>.

## <a name="sample-code"></a>Exemple de code

Le code suivant :

- crée un `EventListener` type dérivé de qui écrit dans `System.Console` ,
- abonne cet écouteur à `BinaryFormatter` des notifications produites,
- sérialise et désérialise un graphique d’objets simple à l’aide de `BinaryFormatter` , et
- analyse les événements qui ont été déclenchés.

:::code language="csharp" source="snippets/binaryformatter-event-source/csharp/Program.cs":::

Le code précédent produit une sortie similaire à l’exemple suivant :

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

Dans cet exemple, les journaux basés sur la console `EventListener` que la sérialisation démarre, les instances de `Person` et `Book` sont sérialisés, puis la sérialisation se termine. De même, une fois que la désérialisation a démarré, les instances de `Person` et `Book` sont désérialisées, puis la désérialisation se termine.

L’application imprime ensuite les valeurs contenues dans le désérialisé `Person` pour montrer que l’objet a été correctement sérialisé et désérialisé.

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur l’utilisation `EventListener` de pour recevoir `EventSource` des notifications basées sur, consultez [la `EventListener` classe](xref:System.Diagnostics.Tracing.EventListener).
