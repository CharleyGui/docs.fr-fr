---
title: Extension de l’espace de noms My
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 2a7b0b84061fccd9a333a68e4a19477bd19ca4ff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330319"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Extension de `My` l’espace de noms dans Visual Basic

L' `My` espace de noms de Visual Basic expose les propriétés et les méthodes qui vous permettent de tirer facilement parti de la puissance du .NET Framework. L' `My` espace de noms simplifie les problèmes de programmation courants, en réduisant souvent une tâche difficile à une seule ligne de code. En outre, l' `My` espace de noms est entièrement extensible afin que vous puissiez personnaliser le `My` comportement de et ajouter de nouveaux services à sa hiérarchie pour adapter à des besoins spécifiques de l’application. Cette rubrique explique comment personnaliser les membres existants de l' `My` espace de noms et comment ajouter vos propres classes personnalisées à l' `My` espace de noms.

## <a name="customizing-existing-my-namespace-members"></a>Personnalisation des membres `My` d’espace de noms existants

L' `My` espace de noms de Visual Basic expose des informations fréquemment utilisées sur votre application, sur votre ordinateur, et bien plus encore. Pour obtenir la liste complète des objets de l' `My` espace de noms, consultez [ma référence](../../language-reference/keywords/my-reference.md). Vous devrez peut-être personnaliser les membres existants `My` de l’espace de noms pour qu’ils correspondent mieux aux besoins de votre application. Toute propriété d’un objet dans l' `My` espace de noms qui n’est pas en lecture seule peut être définie sur une valeur personnalisée.

Par exemple, supposons que vous utilisez fréquemment `My.User` l’objet pour accéder au contexte de sécurité actuel pour l’utilisateur qui exécute votre application. Toutefois, votre entreprise utilise un objet utilisateur personnalisé pour exposer des informations et des fonctionnalités supplémentaires aux utilisateurs au sein de l’entreprise. Dans ce scénario, vous pouvez remplacer la valeur par défaut de `My.User.CurrentPrincipal` la propriété par une instance de votre propre objet principal personnalisé, comme illustré dans l’exemple suivant :

[!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]

La définition `CurrentPrincipal` de la propriété `My.User` sur l’objet modifie l’identité sous laquelle l’application s’exécute. À `My.User` son tour, l’objet retourne des informations sur l’utilisateur qui vient d’être spécifié.
  
## <a name="adding-members-to-my-objects"></a>Ajout de membres `My` aux objets

Les types `My.Application` retournés `My.Computer` par et sont `Partial` définis en tant que classes. Par conséquent, vous pouvez étendre `My.Application` les `My.Computer` objets et en créant `Partial` une classe `MyApplication` nommée `MyComputer`ou. La classe ne peut pas `Private` être une classe. Si vous spécifiez la classe dans le cadre `My` de l’espace de noms, vous pouvez ajouter des propriétés et des méthodes `My.Application` qui `My.Computer` seront incluses avec les objets ou.

L’exemple suivant ajoute une propriété nommée `DnsServerIPAddresses` à l' `My.Computer` objet :

[!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]

## <a name="adding-custom-objects-to-the-my-namespace"></a>Ajout d’objets personnalisés à `My` l’espace de noms

Bien que `My` l’espace de noms fournit des solutions pour de nombreuses tâches de programmation courantes, `My` vous pouvez rencontrer des tâches que l’espace de noms ne traite pas. Par exemple, votre application peut accéder aux services d’annuaire personnalisés pour les données utilisateur, ou votre application peut utiliser des assemblys qui ne sont pas installés par défaut avec Visual Basic. Vous pouvez étendre l' `My` espace de noms pour inclure des solutions personnalisées aux tâches courantes spécifiques à votre environnement. L' `My` espace de noms peut facilement être étendu pour ajouter de nouveaux membres afin de répondre aux besoins croissants de l’application. En outre, vous pouvez déployer vos `My` extensions d’espace de noms sur d’autres développeurs en tant que modèle de Visual Basic.
  
### <a name="adding-members-to-the-my-namespace"></a>Ajout de membres à `My` l’espace de noms

Étant `My` donné que est un espace de noms comme tout autre espace de noms, vous pouvez y ajouter des propriétés de niveau supérieur en ajoutant `Namespace` simplement `My`un module et en spécifiant un de. Annotez le module avec `HideModuleName` l’attribut, comme indiqué dans l’exemple suivant. L' `HideModuleName` attribut garantit qu’IntelliSense n’affichera pas le nom du module lorsqu’il affichera les `My` membres de l’espace de noms.

[!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]

Pour ajouter des membres à `My` l’espace de noms, ajoutez les propriétés nécessaires au module. Pour chaque propriété ajoutée à l' `My` espace de noms, ajoutez un champ privé `ThreadSafeObjectProvider(Of T)`de type, où le type est le type retourné par votre propriété personnalisée. Ce champ est utilisé pour créer des instances d’objet thread-safe qui doivent être retournées par `GetInstance` la propriété en appelant la méthode. Par conséquent, chaque thread qui accède à la propriété étendue reçoit sa propre instance du type retourné. L’exemple suivant ajoute une propriété nommée `SampleExtension` qui est de type `SampleExtension` à l' `My` espace de noms :

[!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]

## <a name="adding-events-to-custom-my-objects"></a>Ajout d’événements aux `My` objets personnalisés

Vous pouvez utiliser l' `My.Application` objet pour exposer des événements pour vos `My` objets personnalisés en étendant la `MyApplication` classe partielle `My` dans l’espace de noms. Pour les projets basés sur Windows, vous pouvez double-cliquer sur le nœud **My Project** dans pour votre projet dans **Explorateur de solutions**. Dans le **Concepteur de projet**Visual Basic, cliquez sur l’onglet **application** , puis cliquez sur le bouton afficher les **événements d’application** . Un nouveau fichier nommé *ApplicationEvents. vb* sera créé. Il contient le code suivant pour l’extension `MyApplication` de la classe :

[!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]

Vous pouvez ajouter des gestionnaires d’événements pour vos `My` objets personnalisés en ajoutant des gestionnaires d’événements personnalisés `MyApplication` à la classe. Les événements personnalisés vous permettent d’ajouter du code qui s’exécute lorsqu’un gestionnaire d’événements est ajouté, supprimé ou lorsque l’événement est déclenché. Notez que le `AddHandler` code d’un événement personnalisé s’exécute uniquement si le code est ajouté par un utilisateur pour gérer l’événement. Par exemple, considérez que `SampleExtension` l’objet de la section précédente a `Load` un événement auquel vous souhaitez ajouter un gestionnaire d’événements personnalisé. L’exemple de code suivant montre un gestionnaire d’événements `SampleExtensionLoad` personnalisé nommé qui est appelé lorsque l' `My.SampleExtension.Load` événement se produit. Lorsque du code est ajouté pour gérer le `My.SampleExtensionLoad` nouvel événement, `AddHandler` la partie de ce code d’événement personnalisé est exécutée. La `MyApplication_SampleExtensionLoad` méthode est incluse dans l’exemple de code pour illustrer un exemple de gestionnaire d’événements qui `My.SampleExtensionLoad` gère l’événement. Notez que l' `SampleExtensionLoad` événement est disponible lorsque vous sélectionnez l’option **mes événements d’application** dans la liste déroulante de gauche au-dessus de l’éditeur de code lorsque vous modifiez le fichier *ApplicationEvents. vb* .

[!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]

## <a name="design-guidelines"></a>Recommandations en matière de conception

Lorsque vous développez des extensions `My` de l’espace de noms, utilisez les instructions suivantes pour réduire les coûts de maintenance de vos composants d’extension :

- **Incluez uniquement la logique d’extension.** La logique incluse dans l' `My` extension de l’espace de noms doit inclure uniquement le code nécessaire pour exposer les fonctionnalités requises `My` dans l’espace de noms. Étant donné que votre extension réside dans des projets utilisateur en tant que code source, la mise à jour du composant d’extension entraîne un coût de maintenance élevé et doit être évitée si possible.
- **Réduire les hypothèses du projet.** Lorsque vous créez vos extensions de l' `My` espace de noms, ne supposez pas un ensemble de références, d’importations au niveau du projet ou de paramètres spécifiques `Option Strict` du compilateur (par exemple, désactivé). Au lieu de cela, réduisez les dépendances et qualifiez `Global` entièrement toutes les références de type à l’aide du mot clé. En outre, assurez-vous que l’extension `Option Strict` est compilée avec sur pour réduire les erreurs dans l’extension.
- **Isolez le code de l’extension.** Si vous placez le code dans un seul fichier, votre extension peut facilement être déployée en tant que modèle d’élément Visual Studio. Pour plus d’informations, consultez « packages et déploiement d’extensions » plus loin dans cette rubrique. Le placement de `My` tout le code d’extension d’espace de noms dans un fichier unique ou dans un dossier distinct d’un `My` projet permet également aux utilisateurs de localiser l’extension d’espace de noms.

## <a name="designing-class-libraries-for-my"></a>Conception de bibliothèques de classes pour`My`

Comme c’est le cas avec la plupart des modèles objet, certains modèles de conception `My` fonctionnent bien dans l’espace de noms, et d’autres non. Lorsque vous concevez une extension `My` de l’espace de noms, tenez compte des principes suivants :

- **Méthodes sans État.** Les méthodes de `My` l’espace de noms doivent fournir une solution complète à une tâche spécifique. Assurez-vous que les valeurs de paramètre passées à la méthode fournissent toutes les entrées requises pour terminer la tâche particulière. Évitez de créer des méthodes qui reposent sur un état antérieur, telles que des connexions ouvertes à des ressources.
- **Instances globales.** Le seul État géré dans l' `My` espace de noms est global pour le projet. Par exemple, `My.Application.Info` encapsule l’état partagé au sein de l’application.
- **Types de paramètres simples.** N’oubliez pas de simplifier les choses en évitant les types de paramètres complexes. Au lieu de cela, créez des méthodes qui ne prennent aucune entrée de paramètre ou qui acceptent des types d’entrée simples tels que des chaînes, des types primitifs, etc.
- **Méthodes de fabrique.** Certains types sont nécessairement difficiles à instancier. Fournir des méthodes de fabrique comme extensions `My` de l’espace de noms vous permet de découvrir et de consommer plus facilement les types qui appartiennent à cette catégorie. Un exemple de méthode de fabrique qui fonctionne bien est `My.Computer.FileSystem.OpenTextFileReader`. Plusieurs types de flux sont disponibles dans le .NET Framework. En spécifiant des fichiers texte spécifiquement `OpenTextFileReader` , le permet à l’utilisateur de comprendre le flux à utiliser.

Ces recommandations n’empêchent pas les principes de conception généraux pour les bibliothèques de classes. Au lieu de cela, il s’agit de recommandations optimisées pour les développeurs qui `My` utilisent Visual Basic et l’espace de noms. Pour connaître les principes de conception généraux de la création de bibliothèques de classes, consultez [instructions de conception d’infrastructure](../../../standard/design-guidelines/index.md).

## <a name="packaging-and-deploying-extensions"></a>Empaquetage et déploiement d’extensions

Vous pouvez inclure `My` des extensions d’espace de noms dans un modèle de projet Visual Studio, ou vous pouvez empaqueter vos extensions et les déployer en tant que modèle d’élément Visual Studio. Lorsque vous empaquetez vos `My` extensions d’espace de noms en tant que modèle d’élément Visual Studio, vous pouvez tirer parti des fonctionnalités supplémentaires fournies par Visual Basic. Ces fonctionnalités vous permettent d’inclure une extension lorsqu’un projet fait référence à un assembly particulier ou de permettre aux utilisateurs `My` d’ajouter explicitement votre extension d’espace de noms à l’aide de la page **Extensions My** du concepteur de projet Visual Basic.

Pour plus d’informations sur le `My` déploiement des extensions d’espace de noms, consultez [empaquetage et déploiement d’extensions My personnalisées](packaging-and-deploying-custom-my-extensions.md).

## <a name="see-also"></a>Voir aussi

- [Empaquetage et déploiement des extensions My personnalisées](packaging-and-deploying-custom-my-extensions.md)
- [Extension du modèle d’application Visual Basic](extending-the-visual-basic-application-model.md)
- [Personnalisation de la disponibilité ou non des objets dans My](customizing-which-objects-are-available-in-my.md)
- [Page Mes extensions, Concepteur de projets](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Page Application, Concepteur de projet (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partielle](../../language-reference/modifiers/partial.md)
