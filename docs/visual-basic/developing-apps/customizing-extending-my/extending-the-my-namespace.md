---
title: Extension de l'espace de noms My dans Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 6da0914c9d2d4dc1220ede5d6fa9f1aa6b43426a
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775303"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Extension de l’espace de noms `My` dans Visual Basic

L’espace de noms `My` dans Visual Basic expose les propriétés et les méthodes qui vous permettent de tirer facilement parti de la puissance du .NET Framework. L’espace de noms `My` simplifie les problèmes de programmation courants, en réduisant souvent une tâche difficile sur une seule ligne de code. En outre, l’espace de noms `My` est entièrement extensible pour vous permettre de personnaliser le comportement de `My` et d’ajouter de nouveaux services à sa hiérarchie pour s’adapter aux besoins spécifiques de l’application. Cette rubrique explique comment personnaliser les membres existants de l’espace de noms `My` et comment ajouter vos propres classes personnalisées à l’espace de noms `My`.

## <a name="customizing-existing-my-namespace-members"></a>Personnalisation des membres existants de l’espace de noms `My`

L’espace de noms `My` dans Visual Basic expose des informations fréquemment utilisées sur votre application, sur votre ordinateur, et bien plus encore. Pour obtenir la liste complète des objets de l’espace de noms `My`, consultez [ma référence](../../language-reference/keywords/my-reference.md). Vous devrez peut-être personnaliser les membres existants de l’espace de noms `My` pour qu’ils correspondent mieux aux besoins de votre application. Toute propriété d’un objet dans l’espace de noms `My` qui n’est pas en lecture seule peut être définie sur une valeur personnalisée.

Par exemple, supposons que vous utilisez fréquemment l’objet `My.User` pour accéder au contexte de sécurité actuel pour l’utilisateur qui exécute votre application. Toutefois, votre entreprise utilise un objet utilisateur personnalisé pour exposer des informations et des fonctionnalités supplémentaires aux utilisateurs au sein de l’entreprise. Dans ce scénario, vous pouvez remplacer la valeur par défaut de la propriété `My.User.CurrentPrincipal` par une instance de votre propre objet principal personnalisé, comme indiqué dans l’exemple suivant :

[!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]

La définition de la propriété `CurrentPrincipal` sur l’objet `My.User` modifie l’identité sous laquelle l’application s’exécute. L’objet `My.User` retourne, à son tour, des informations sur l’utilisateur qui vient d’être spécifié.
  
## <a name="adding-members-to-my-objects"></a>Ajout de membres à des objets `My`

Les types retournés à partir de `My.Application` et `My.Computer` sont définis comme des classes de `Partial`. Par conséquent, vous pouvez étendre les objets `My.Application` et `My.Computer` en créant une classe `Partial` nommée `MyApplication` ou `MyComputer`. La classe ne peut pas être une classe `Private`. Si vous spécifiez la classe dans le cadre de l’espace de noms `My`, vous pouvez ajouter des propriétés et des méthodes qui seront incluses avec les objets `My.Application` ou `My.Computer`.

L’exemple suivant ajoute une propriété nommée `DnsServerIPAddresses` à l’objet `My.Computer` :

[!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]

## <a name="adding-custom-objects-to-the-my-namespace"></a>Ajout d’objets personnalisés à l’espace de noms `My`

Bien que l’espace de noms `My` fournit des solutions pour de nombreuses tâches de programmation courantes, vous pouvez rencontrer des tâches que l’espace de noms `My` ne traite pas. Par exemple, votre application peut accéder aux services d’annuaire personnalisés pour les données utilisateur, ou votre application peut utiliser des assemblys qui ne sont pas installés par défaut avec Visual Basic. Vous pouvez étendre l’espace de noms `My` pour inclure des solutions personnalisées aux tâches courantes spécifiques à votre environnement. L’espace de noms `My` peut facilement être étendu pour ajouter de nouveaux membres afin de répondre aux besoins croissants de l’application. En outre, vous pouvez déployer vos extensions d’espace de noms `My` sur d’autres développeurs en tant que modèle de Visual Basic.
  
### <a name="adding-members-to-the-my-namespace"></a>Ajout de membres à l’espace de noms `My`

Étant donné que `My` est un espace de noms comme tout autre espace de noms, vous pouvez y ajouter des propriétés de niveau supérieur en ajoutant simplement un module et en spécifiant une `Namespace` de `My`. Annotez le module avec l’attribut `HideModuleName`, comme indiqué dans l’exemple suivant. L’attribut `HideModuleName` garantit qu’IntelliSense n’affichera pas le nom du module lorsqu’il affichera les membres de l’espace de noms `My`.

[!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]

Pour ajouter des membres à l’espace de noms `My`, ajoutez les propriétés nécessaires au module. Pour chaque propriété ajoutée à l’espace de noms `My`, ajoutez un champ privé de type `ThreadSafeObjectProvider(Of T)`, où le type est le type retourné par votre propriété personnalisée. Ce champ est utilisé pour créer des instances d’objet thread-safe qui doivent être retournées par la propriété en appelant la méthode `GetInstance`. Par conséquent, chaque thread qui accède à la propriété étendue reçoit sa propre instance du type retourné. L’exemple suivant ajoute une propriété nommée `SampleExtension` qui est de type `SampleExtension` à l’espace de noms `My` :

[!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]

## <a name="adding-events-to-custom-my-objects"></a>Ajout d’événements aux objets de `My` personnalisés

Vous pouvez utiliser l’objet `My.Application` pour exposer des événements pour vos objets `My` personnalisés en étendant la classe partielle `MyApplication` dans l’espace de noms `My`. Pour les projets basés sur Windows, vous pouvez double-cliquer sur le nœud **My Project** dans pour votre projet dans **Explorateur de solutions**. Dans le **Concepteur de projet**Visual Basic, cliquez sur l’onglet **application** , puis cliquez sur le bouton afficher les **événements d’application** . Un nouveau fichier nommé *ApplicationEvents. vb* sera créé. Il contient le code suivant pour l’extension de la classe `MyApplication` :

[!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]

Vous pouvez ajouter des gestionnaires d’événements pour vos objets `My` personnalisés en ajoutant des gestionnaires d’événements personnalisés à la classe `MyApplication`. Les événements personnalisés vous permettent d’ajouter du code qui s’exécute lorsqu’un gestionnaire d’événements est ajouté, supprimé ou lorsque l’événement est déclenché. Notez que le code `AddHandler` pour un événement personnalisé s’exécute uniquement si le code est ajouté par un utilisateur pour gérer l’événement. Par exemple, considérez que l’objet `SampleExtension` de la section précédente a un événement `Load` auquel vous souhaitez ajouter un gestionnaire d’événements personnalisé. L’exemple de code suivant montre un gestionnaire d’événements personnalisé nommé `SampleExtensionLoad` qui sera appelé lorsque l’événement `My.SampleExtension.Load` se produit. Lorsque du code est ajouté pour gérer le nouvel événement `My.SampleExtensionLoad`, la partie `AddHandler` de ce code d’événement personnalisé est exécutée. La méthode `MyApplication_SampleExtensionLoad` est incluse dans l’exemple de code pour illustrer un exemple de gestionnaire d’événements qui gère l’événement `My.SampleExtensionLoad`. Notez que l’événement `SampleExtensionLoad` est disponible lorsque vous sélectionnez l’option **mes événements d’application** dans la liste déroulante de gauche au-dessus de l’éditeur de code lorsque vous modifiez le fichier *ApplicationEvents. vb* .

[!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]

## <a name="design-guidelines"></a>Instructions de conception

Lorsque vous développez des extensions vers l’espace de noms `My`, utilisez les instructions suivantes pour réduire les coûts de maintenance de vos composants d’extension :

- **Incluez uniquement la logique d’extension.** La logique incluse dans l’extension de l’espace de noms `My` doit inclure uniquement le code nécessaire pour exposer les fonctionnalités requises dans l’espace de noms `My`. Étant donné que votre extension réside dans des projets utilisateur en tant que code source, la mise à jour du composant d’extension entraîne un coût de maintenance élevé et doit être évitée si possible.
- **Réduire les hypothèses du projet.** Lorsque vous créez vos extensions de l’espace de noms `My`, ne supposez pas un ensemble de références, d’importations au niveau du projet ou de paramètres spécifiques du compilateur (par exemple, `Option Strict` désactivé). Au lieu de cela, réduisez les dépendances et qualifiez entièrement toutes les références de type à l’aide du mot clé `Global`. En outre, assurez-vous que l’extension est compilée avec `Option Strict` sur pour réduire les erreurs dans l’extension.
- **Isolez le code de l’extension.** Si vous placez le code dans un seul fichier, votre extension peut facilement être déployée en tant que modèle d’élément Visual Studio. Pour plus d’informations, consultez « packages et déploiement d’extensions » plus loin dans cette rubrique. Le placement de tout le code d’extension de l’espace de noms `My` dans un fichier unique ou dans un dossier distinct d’un projet permet également aux utilisateurs de localiser l’extension de l’espace de noms `My`.

## <a name="designing-class-libraries-for-my"></a>Conception de bibliothèques de classes pour `My`

Comme c’est le cas avec la plupart des modèles objet, certains modèles de conception fonctionnent bien dans l’espace de noms `My`, et d’autres non. Lorsque vous concevez une extension de l’espace de noms `My`, tenez compte des principes suivants :

- **Méthodes sans État.** Les méthodes de l’espace de noms `My` doivent fournir une solution complète à une tâche spécifique. Assurez-vous que les valeurs de paramètre passées à la méthode fournissent toutes les entrées requises pour terminer la tâche particulière. Évitez de créer des méthodes qui reposent sur un état antérieur, telles que des connexions ouvertes à des ressources.
- **Instances globales.** Le seul État géré dans l’espace de noms `My` est global pour le projet. Par exemple, `My.Application.Info` encapsule l’état partagé au sein de l’application.
- **Types de paramètres simples.** N’oubliez pas de simplifier les choses en évitant les types de paramètres complexes. Au lieu de cela, créez des méthodes qui ne prennent aucune entrée de paramètre ou qui acceptent des types d’entrée simples tels que des chaînes, des types primitifs, etc.
- **Méthodes de fabrique.** Certains types sont nécessairement difficiles à instancier. Fournir des méthodes de fabrique comme extensions de l’espace de noms `My` vous permet de découvrir et de consommer plus facilement les types qui appartiennent à cette catégorie. @No__t_0 est un exemple de méthode de fabrique qui fonctionne bien. Plusieurs types de flux sont disponibles dans le .NET Framework. En spécifiant des fichiers texte spécifiquement, le `OpenTextFileReader` aide l’utilisateur à comprendre le flux à utiliser.

Ces recommandations n’empêchent pas les principes de conception généraux pour les bibliothèques de classes. Au lieu de cela, il s’agit de recommandations optimisées pour les développeurs qui utilisent Visual Basic et l’espace de noms `My`. Pour connaître les principes de conception généraux de la création de bibliothèques de classes, consultez [instructions de conception d’infrastructure](../../../standard/design-guidelines/index.md).

## <a name="packaging-and-deploying-extensions"></a>Empaquetage et déploiement d’extensions

Vous pouvez inclure des extensions d’espace de noms `My` dans un modèle de projet Visual Studio, ou vous pouvez empaqueter vos extensions et les déployer en tant que modèle d’élément Visual Studio. Quand vous empaquetez vos extensions d’espace de noms `My` en tant que modèle d’élément Visual Studio, vous pouvez tirer parti des fonctionnalités supplémentaires fournies par Visual Basic. Ces fonctionnalités vous permettent d’inclure une extension lorsqu’un projet fait référence à un assembly particulier, ou d’autoriser les utilisateurs à ajouter explicitement votre extension d’espace de noms `My` à l’aide de la page **Extensions My** du concepteur de projet Visual Basic.

Pour plus d’informations sur le déploiement des extensions d’espace de noms `My`, consultez [empaquetage et déploiement d’extensions My personnalisées](packaging-and-deploying-custom-my-extensions.md).

## <a name="see-also"></a>Voir aussi

- [Empaquetage et déploiement des extensions My personnalisées](packaging-and-deploying-custom-my-extensions.md)
- [Extension du modèle d’application Visual Basic](extending-the-visual-basic-application-model.md)
- [Personnalisation de la disponibilité ou non des objets dans My](customizing-which-objects-are-available-in-my.md)
- [Extensions My, page du Concepteur de projets](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Page Application, Concepteur de projet (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partial](../../language-reference/modifiers/partial.md)
