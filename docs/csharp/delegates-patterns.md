---
title: Modèles courants pour les délégués
description: Découvrez les modèles courants pour l’utilisation de délégués dans votre code afin d’éviter un couplage important entre vos composants.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 40e6ced7337e32d6e9b67b12a15ad7e03a77c4b6
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239870"
---
# <a name="common-patterns-for-delegates"></a>Modèles courants pour les délégués

[Précédent](delegates-strongly-typed.md)

Les délégués fournissent un mécanisme qui autorise des conceptions logicielles impliquant un couplage minimal entre les composants.

LINQ constitue un excellent exemple de ce genre de conception. Le modèle d’expression de requête LINQ s’appuie sur des délégués pour toutes ses fonctionnalités. Prenons l’exemple simple suivant :

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Il filtre la séquence de nombres pour ne sélectionner que ceux qui sont inférieurs à 10.
La méthode `Where` utilise un délégué qui détermine les éléments d’une séquence qui correspondent au filtre. Quand vous créez une requête LINQ, vous fournissez l’implémentation du délégué à cette fin spécifique.

Le prototype de la méthode Where est le suivant :

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

Cet exemple est répété avec toutes les méthodes qui font partie de LINQ. Elles s’appuient toutes sur des délégués pour le code qui gère la requête spécifique. Ce modèle de conception d’API est très puissant, une fois appris et compris.

Cet exemple simple montre que les délégués nécessitent très peu de couplage entre les composants. Vous n’avez pas besoin de créer de classe qui dérive d’une classe de base particulière. Vous n’avez pas besoin d’implémenter une interface spécifique.
La seule exigence consiste à fournir l’implémentation d’une méthode qui est essentielle à la tâche en question.

## <a name="building-your-own-components-with-delegates"></a>Création de vos propres composants avec des délégués

Étendons cet exemple en créant un composant à l’aide d’une conception qui s’appuie sur des délégués.

Nous allons définir un composant qui peut être utilisé pour des messages de journaux dans un système de grande taille. Les composants de bibliothèque pourraient être utilisés dans de nombreux environnements différents, sur plusieurs plateformes différentes. Il existe de nombreuses fonctionnalités courantes dans le composant qui gère les journaux. Il doit accepter des messages en provenance de tout composant du système. Ces messages auront des priorités différentes, que le composant principal peut gérer. Les messages doivent avoir des horodatages dans leur forme finale archivée. Pour des scénarios avancés, vous pouvez filtrer les messages en fonction du composant source.

Il y a un aspect de la fonctionnalité qui changera souvent : l’emplacement d’écriture des messages. Dans certains environnements, ils pourront être écrits dans la console des erreurs. Dans d’autres, il pourra s’agir d’un fichier. Les autres possibilités incluent le stockage de base de données, les journaux des événements du système d’exploitation ou autre stockage de documents.

Il existe également des combinaisons de sortie qui peuvent être utilisées dans différents scénarios. Vous souhaiterez peut-être écrire des messages dans la console et dans un fichier.

Une conception basée sur des délégués offre une très grande souplesse et facilite la prise en charge des mécanismes de stockage qui pourront être ajoutés à l’avenir.

Dans cette conception, le composant de journal principal peut être une classe non virtuelle, voire sealed. Vous pouvez incorporer n’importe quel jeu de délégués pour écrire les messages sur différents supports de stockage. La prise en charge intégrée des délégués multicast facilite la prise en charge des scénarios où les messages doivent être écrits à plusieurs emplacements (dans un fichier et une console).

## <a name="a-first-implementation"></a>Une première implémentation

Commençons par quelque chose de simple : l’implémentation initiale acceptera les nouveaux messages et les écrira à l’aide de n’importe quel délégué attaché. Vous pouvez démarrer avec un délégué qui écrit des messages dans la console.

[!code-csharp[LoggerImplementation](../../samples/snippets/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

La classe statique ci-dessus est la chose la plus simple qui peut fonctionner. Nous devons écrire l’implémentation unique pour la méthode qui écrit des messages dans la console : 

[!code-csharp[LogToConsole](../../samples/snippets/csharp/delegates-and-events/LoggingMethods.cs#LogToConsole "A Console logger.")]

Pour finir, nous devons raccorder le délégué en l’attachant au délégué WriteMessage déclaré dans l’enregistreur d’événements :

[!code-csharp[ConnectDelegate](../../samples/snippets/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a>Méthodes

Jusqu’à présent, notre exemple est assez simple, mais il illustre quand même certaines instructions importantes pour les conceptions impliquant des délégués.

L’utilisation des types délégués définis dans le Core Framework permet aux utilisateurs de travailler facilement avec les délégués. Vous n’avez pas besoin de définir de nouveaux types, et les développeurs qui utilisent votre bibliothèque n’ont pas besoin d’apprendre de nouveaux types délégués spécialisés.

Les interfaces utilisées sont le plus minimal et flexible possible : pour créer un enregistreur d’événements de sortie, vous devez créer une méthode. Il peut s’agir d’une méthode statique ou d’une méthode d’instance. Elle peut avoir n’importe quel accès.

## <a name="formatting-output"></a>Mise en forme de la sortie

Nous allons maintenant rendre cette première version un peu plus robuste et commencer à créer d’autres mécanismes de journalisation.

Ensuite, nous ajouterons quelques arguments à la méthode `LogMessage()` pour que notre classe de journal crée des messages plus structurés :

[!code-csharp[Severity](../../samples/snippets/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

Maintenant, utilisons cet argument `Severity` pour filtrer les messages envoyés à la sortie du journal. 

[!code-csharp[FinalLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a>Méthodes

Nous avons ajouté de nouvelles fonctionnalités à l’infrastructure de journalisation. Le composant enregistreur d’événements étant très faiblement couplé à tout mécanisme de sortie, ces nouvelles fonctionnalités peuvent être ajoutées sans aucun impact sur le code qui implémente le délégué enregistreur d’événements.

Au fil du temps, vous verrez d’autres d’exemples montrant comment ce couplage faible autorise une plus grande souplesse dans la mise à jour des parties du site sans aucune modification des autres emplacements. En fait, dans une application plus grande, les classes de sortie de l’enregistreur d’événements peuvent être dans un autre assembly et ne même pas avoir besoin d’être reconstruites.

## <a name="building-a-second-output-engine"></a>Création d’un deuxième moteur de sortie

Le composant journal commence à prendre forme. Ajoutons un autre moteur de sortie qui enregistre les messages dans un fichier. Ce moteur de sortie est légèrement plus complexe. Il s’agit d’une classe qui encapsule les opérations de fichiers et garantit que le fichier est toujours fermé après chaque écriture. Cela permet de s’assurer que toutes les données sont vidées sur le disque après chaque génération de message.

Voici cet enregistreur d’événements basé sur fichier :

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

Une fois que nous avons créé cette classe, nous pouvons l’instancier, et elle attache sa méthode LogMessage au composant enregistreur d’événements :

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

Ces deux méthodes ne s’excluent pas mutuellement. Nous pourrions attacher les deux méthodes de journalisation et générer des messages dans la console et dans un fichier :

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LoggingMethods.LogToConsole; // LoggingMethods is the static class we utilized earlier
```

Plus tard, même dans la même application, nous pourrions supprimer l’un des délégués sans provoquer d’autre problème dans le système :

```csharp
Logger.WriteMessage -= LoggingMethods.LogToConsole;
```

## <a name="practices"></a>Méthodes

Nous avons maintenant ajouté un deuxième gestionnaire de sortie pour le sous-système de journalisation.
Celui-ci a besoin d’un peu plus d’infrastructure pour correctement prendre en charge le système de fichiers. Le délégué est une méthode d’instance. Il s’agit aussi d’une méthode privée.
Une plus grande accessibilité n’est pas nécessaire, car l’infrastructure de délégué peut connecter les délégués.

Ensuite, la conception basée sur les délégués autorise plusieurs méthodes de sortie sans code supplémentaire. Vous n’avez pas besoin de créer d’infrastructure supplémentaire pour prendre en charge plusieurs méthodes de sortie. Elles viennent simplement s’ajouter comme autre méthode dans la liste d’invocation.

Faites particulièrement attention au code de la méthode de sortie de journalisation de fichier. Cette méthode est codée pour s’assurer qu’elle ne lève pas d’exception. Même si ce n’est pas toujours strictement nécessaire, cette pratique est souvent recommandée. Si l’une des méthodes délégué lève une exception, les délégués restants qui sont sur la liste d’invocation ne sont pas appelés.

Dernière remarque : l’enregistreur d’événements de fichier doit gérer ses ressources en ouvrant et en fermant le fichier à chaque message de journal. Vous pouvez choisir de laisser le fichier ouvert et d’implémenter IDisposable pour fermer le fichier une fois que vous avez terminé.
Les deux méthodes ont leurs avantages et leurs inconvénients. Elles créent toutes les deux un peu plus de couplage entre les classes.

Pour prendre en charge ces deux scénarios, il est inutile de mettre à jour le code de la classe Logger.

## <a name="handling-null-delegates"></a>Gestion des délégués Null

Pour finir, nous allons mettre à jour la méthode LogMessage afin qu’elle soit robuste pour les cas où aucun mécanisme de sortie n’est sélectionné. L’implémentation actuelle lève une `NullReferenceException` quand aucune liste d’invocation n’est attachée au délégué `WriteMessage`.
Vous préférerez peut-être une conception qui continue en mode silencieux quand aucune méthode n’a été attachée. Pour cela, vous pouvez utiliser l’opérateur conditionnel null, combiné avec la méthode `Delegate.Invoke()` :

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

L’opérateur conditionnel null (`?.`) court-circuite quand l’opérande gauche (ici, `WriteMessage`) est null, ce qui signifie que le système ne tente pas de consigner un message dans le journal.

Vous ne trouverez pas la méthode `Invoke()` répertoriée dans la documentation de `System.Delegate` ou `System.MulticastDelegate`. Le compilateur génère une méthode `Invoke` de type sécurisé pour tout type de délégué déclaré. Dans cet exemple, cela signifie que `Invoke` prend un seul argument `string` et a un type de retour void.

## <a name="summary-of-practices"></a>Récapitulatif des méthodes

Nous venons de voir le début d’un composant de journal qui peut être étendu avec d’autres enregistreurs, ainsi que d’autres fonctionnalités. Grâce à l’utilisation de délégués dans la conception, ces différents composants sont très faiblement couplés. Cela présente plusieurs avantages. Il est très facile de créer de nouveaux mécanismes de sortie et de les attacher au système. Ces autres mécanismes n’ont besoin que d’une seule méthode : celle qui écrit le message du journal. Cette conception offre une grande souplesse lors de l’ajout de nouvelles fonctionnalités. Le contrat requis pour tout enregistreur consiste à implémenter une méthode. Il peut s’agir d’une méthode d’instance ou statique. Elle peut être publique, privée ou avoir tout autre accès légal.

La classe Logger peut apporter des améliorations ou des modifications sans introduire de modifications avec rupture. Comme toute classe, vous ne pouvez pas modifier l’API publique sans risque de modifications avec rupture. Toutefois, le couplage entre l’enregistreur d’événements et les moteurs de sortie étant uniquement par l’intermédiaire du délégué, aucun autre type (tel que les interfaces ou classes de base) n’est appelé. Le couplage est aussi réduit que possible.

[Next](events-overview.md)
