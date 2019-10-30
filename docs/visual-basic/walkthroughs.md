---
title: Procédures pas à pas relatives au langage Visual Basic
description: Instructions pas à pas pour les scénarios courants de développement Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, walkthroughs
- examples [Visual Basic]
- Visual Basic code, walkthroughs
- walkthroughs [Visual Basic]
ms.assetid: e4e1f849-e1ce-4cf7-8483-d9b4c4887a8e
ms.openlocfilehash: f6a4c5b5376c5ee746bb0fadfeeac7ac9793e91f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040950"
---
# <a name="visual-basic-language-walkthroughs"></a>Procédures pas à pas relatives au langage Visual Basic

Les procédures pas à pas fournissent des instructions détaillées pour les scénarios courants, ce qui en fait un bon point de départ pour apprendre à utiliser le produit ou une fonctionnalité particulière.

- [Écriture d’un programme asynchrone](./programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 Explique comment créer une solution asynchrone avec [Async](language-reference/modifiers/async.md) et [Await](language-reference/operators/await-operator.md).

- [Déclaration et déclenchement des événements](programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 Explique comment les événements sont déclarés et déclenchés en Visual Basic.

- [Gestion des événements](programming-guide/language-features/events/walkthrough-handling-events.md)  
 Explique comment gérer les événements en utilisant le mot clé `WithEvents` standard ou les nouveaux mots clés `AddHandler`/`RemoveHandler`.

- [Création et implémentation d’interfaces](programming-guide/language-features/interfaces/walkthrough-creating-and-implementing-interfaces.md)  
 Explique comment les interfaces sont déclarées et implémentées en Visual Basic.

- [Définition de classes](programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 Décrit comment déclarer une classe et ses champs, propriétés, méthodes et événements.

- [Écriture de requêtes dans Visual Basic](programming-guide/concepts/linq/walkthrough-writing-queries.md)  
 Montre comment vous pouvez utiliser les fonctionnalités du langage Visual Basic pour écrire des expressions de requête [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].

- [Implémentation d’IEnumerable (Of T) en Visual Basic](programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)  
 Montre comment créer une classe qui implémente l’interface `IEnumerable(Of String)` et une classe qui implémente l’interface `IEnumerator(Of String)` pour lire un fichier texte ligne par ligne.

- [Appel des API Windows](programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 Explique comment utiliser les instructions `Declare` et appeler des API Windows. Inclut des informations sur l’utilisation d’attributs pour contrôler le marshaling en vue de l’appel d’API et l’exposition d’un appel d’API sous forme d’une méthode de classe.

- [Création d’objets COM avec Visual Basic](programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 Montre comment créer des objets COM en Visual Basic, avec et sans le modèle de classe COM.

- [Implémentation de l’héritage avec les objets COM](programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 Montre comment créer un objet COM contenant une classe à l’aide de Visual Basic 6.0, puis l’utiliser comme classe de base dans Visual Basic.

- [Détermination de l’emplacement des informations My.Application.Log](developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 Décrit les paramètres `My.Application.Log` par défaut et explique comment déterminer les paramètres de votre application.

- [Modification de l’emplacement des informations My.Application.Log](developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 Indique comment substituer les paramètres `My.Application.Log` et `My.Log` par défaut pour enregistrer des informations sur les événements et forcer l’objet `Log` à écrire dans d’autres écouteurs de journalisation.

- [Filtrage de la sortie de My.Application.Log](developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)  
 Montre comment modifier le filtrage de journal par défaut pour l’objet `My.Application.Log`.

- [Création d’écouteurs de journalisation personnalisés](developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)  
 Illustre comment créer un écouteur de journalisation personnalisé et le configurer pour écouter la sortie de l’objet `My.Application.Log`.

- [Incorporation de types provenant d’assemblys managés](../standard/assembly/embed-types-visual-studio.md)  
 Décrit comment créer un assembly et un programme client qui incorpore des types à partir de celui-ci.

- [Validation de la complexité des mots de passe (Visual Basic)](programming-guide/language-features/strings/walkthrough-validating-that-passwords-are-complex.md)  
 Montre comment rechercher les caractéristiques de mot de passe fort et mettre à jour un paramètre de chaîne avec des informations indiquant les vérifications de mot de passe qui ont échoué.

- [Chiffrement et déchiffrement de chaînes en Visual Basic](programming-guide/language-features/strings/walkthrough-encrypting-and-decrypting-strings.md)  
 Montre comment utiliser la classe <xref:System.Security.Cryptography.DESCryptoServiceProvider> pour chiffrer et déchiffrer des chaînes.

- [Manipulation de fichiers et de dossiers dans Visual Basic](developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 Montre comment utiliser les fonctions Visual Basic pour déterminer les informations relatives à un fichier, rechercher une chaîne dans un fichier et écrire dans un fichier.

- [Manipulation de fichiers à l’aide de méthodes du .NET Framework](developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 Montre comment utiliser les méthodes du .NET Framework pour déterminer les informations relatives à un fichier, rechercher une chaîne dans un fichier et écrire dans un fichier.

- [Persistance d’un objet en Visual Basic](programming-guide/concepts/serialization/walkthrough-persisting-an-object-in-visual-studio.md)  
 Montre comment créer un objet simple et rendre ses données persistantes dans un fichier.

- [Procédure pas à pas : prise en charge du développement basé d’abord sur les tests avec la fonctionnalité Générer à partir de l’utilisation](/visualstudio/ide/walkthrough-test-first-support-with-the-generate-from-usage-feature)  
 Explique comment effectuer le développement par test initial, dans lequel vous écrivez d’abord les tests unitaires et ensuite le code source pour garantir la réussite de ces tests.
