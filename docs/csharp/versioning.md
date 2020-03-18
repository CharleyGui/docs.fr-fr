---
title: Gestion de version C# - Guide C#
description: Comprendre le fonctionnement de la gestion de version C# et .NET
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 124cce51865f04a555bc121fb6ce18cc95591bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156465"
---
# <a name="versioning-in-c"></a>Gestion de versions en C\#

Dans ce didacticiel, vous allez apprendre la signification de la gestion de version .NET. Vous découvrirez également les facteurs à prendre en compte dans le cadre du contrôle de version de votre bibliothèque et de sa mise à niveau vers une nouvelle version.

## <a name="authoring-libraries"></a>Création de bibliothèques

En tant que développeur ayant créé des bibliothèques .NET pour une utilisation publique, vous avez probablement été confronté à des situations où vous deviez déployer de nouvelles mises à jour. Votre manière de procéder est très importante, car vous devez assurer une transition fluide du code existant vers la nouvelle version de votre bibliothèque. Voici quelques points à prendre en compte lors de la création d’une version :

### <a name="semantic-versioning"></a>Gestion sémantique des versions

La [gestion sémantique de version](https://semver.org/) (SemVer en abrégé) est une convention d’affectation de noms appliquée à des versions de votre bibliothèque pour indiquer des événements jalons spécifiques.
Dans l’idéal, les informations de version ajoutées à votre bibliothèque doivent aider les développeurs à déterminer la compatibilité avec les projets qui utilisent des versions antérieures de cette même bibliothèque.

L’approche la plus simple de SemVer est le format à 3 composants `MAJOR.MINOR.PATCH`, où :

- `MAJOR` est incrémenté quand vous apportez des changements d’API incompatibles
- `MINOR` est incrémenté quand vous ajoutez des fonctionnalités à compatibilité descendante
- `PATCH` est incrémenté quand vous apportez des correctifs de bogues à compatibilité descendante

Il existe également des moyens de spécifier d’autres scénarios, tels que des préversions, lors de l’application des informations de version à votre bibliothèque .NET.

### <a name="backwards-compatibility"></a>Compatibilité descendante

Quand vous publiez de nouvelles versions de votre bibliothèque, l’une de vos principales préoccupations concerne la compatibilité descendante avec les versions précédentes.
Une nouvelle version de la bibliothèque est compatible au format source avec une version précédente si le code qui dépend de la version précédente est utilisable avec la nouvelle version une fois qu’il est recompilé.
Une nouvelle version de la bibliothèque est compatible au format binaire si une application qui dépendait de l’ancienne version est utilisable avec la nouvelle version sans recompilation.

Voici quelques éléments à prendre en compte quand vous tentez de maintenir la compatibilité descendante avec d’anciennes versions de votre bibliothèque  :

- Méthodes virtuelles : quand vous rendez une méthode virtuelle non virtuelle dans la nouvelle version, cela signifie que les projets qui substituent cette méthode doivent être mis à jour. Il s’agit là d’une modification avec rupture importante qui est vivement déconseillée.
- Signatures de méthode : Lors de la mise à jour d’un comportement de méthode vous oblige à changer sa signature ainsi, vous devriez plutôt créer une surcharge de sorte que le code appelant dans cette méthode fonctionnera toujours.
Vous pouvez toujours manipuler l’ancienne signature de méthode pour appeler la nouvelle signature de méthode afin que l’implémentation reste cohérente.
- [Attribut obsolète](programming-guide/concepts/attributes/common-attributes.md#Obsolete) : vous pouvez utiliser cet attribut dans votre code pour spécifier des classes ou membres de classe dépréciés et susceptibles d’être supprimés dans les prochaines versions. Cela garantit que les développeurs utilisant votre bibliothèque sont mieux préparés pour les modifications avec rupture.
- Arguments de méthode facultatifs : quand vous rendez obligatoires des arguments de méthode auparavant facultatifs ou modifiez leur valeur par défaut, tout le code qui ne fournit pas ces arguments doit être mis à jour.

> [!NOTE]
> Rendre les arguments obligatoires facultatifs devrait avoir très peu d’effet, surtout si cela ne change pas le comportement de la méthode.

Plus il est facile pour vos utilisateurs d’effectuer la mise à niveau vers la nouvelle version de votre bibliothèque, plus il est probable qu’ils le feront rapidement.

### <a name="application-configuration-file"></a>Fichier de configuration de l'application

En tant que développeur .NET, il est très probable que vous ayez rencontré [le fichier `app.config`](../framework/configure-apps/file-schema/index.md), présent dans la plupart des types de projets.
Ce simple fichier de configuration peut s’avérer très utile pour améliorer le déploiement de nouvelles mises à jour. Vous devez généralement concevoir vos bibliothèques de telle sorte que les `app.config` informations qui sont susceptibles de changer régulièrement sont stockées dans le fichier, de cette façon lorsque ces informations sont mises à jour, le fichier config des anciennes versions doit juste être remplacé par la nouvelle sans avoir besoin de recomplification de la bibliothèque.

## <a name="consuming-libraries"></a>Utilisation des bibliothèques

En tant que développeur qui utilise les bibliothèques .NET générées par d’autres développeurs, vous savez probablement qu’une nouvelle version d’une bibliothèque peut ne pas être totalement compatible avec votre projet et vous pouvez souvent être obligé de mettre à jour votre code pour vous adapter à ces modifications.

Heureusement pour vous, C et l’écosystème .NET est livré avec des fonctionnalités et des techniques qui nous permettent de mettre à jour facilement notre application pour travailler avec de nouvelles versions de bibliothèques qui pourraient introduire des changements de rupture.

### <a name="assembly-binding-redirection"></a>Redirection des liaisons d'assembly

Vous pouvez utiliser le fichier *app.config* pour mettre à jour la version d’une bibliothèque que votre application utilise. En ajoutant ce qu’on appelle une [*redirection de liaison,*](../framework/configure-apps/redirect-assembly-versions.md)vous pouvez utiliser la nouvelle version de la bibliothèque sans avoir à recomposer votre application. L’exemple suivant montre comment vous mettre à jour le `1.0.1` fichier *app.config* de votre application pour utiliser la version patch au lieu de `ReferencedLibrary` la `1.0.0` version avec laquelle il a été initialement compilé.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Cette approche fonctionne uniquement si la nouvelle version de `ReferencedLibrary` est compatible au format binaire avec votre application.
> Consultez la section [Compatibilité descendante](#backwards-compatibility) ci-dessus pour connaître les changements à rechercher lors de la détermination de la compatibilité.

### <a name="new"></a>new

Vous utilisez le modificateur `new` pour masquer les membres hérités d’une classe de base. Il s’agit d’une façon pour les classes dérivées de pouvoir répondre aux mises à jour dans les classes de base.

Prenons l’exemple suivant :

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

**Sortie**

```console
A base method
A derived method
```

Dans l’exemple ci-dessus, vous pouvez voir comment `DerivedClass` masque la méthode `MyMethod` présente dans `BaseClass`.
Cela signifie que, quand une classe de base dans la nouvelle version d’une bibliothèque ajoute un membre qui existe déjà dans votre classe dérivée, vous pouvez simplement utiliser le modificateur `new` sur le membre de la classe dérivée pour masquer le membre de la classe de base.

Quand aucun modificateur `new` n’est spécifié, une classe dérivée masque par défaut des membres en conflit dans une classe de base ; même si un avertissement du compilateur est généré, le code est toujours compilé. Cela signifie que le fait d’ajouter simplement de nouveaux membres à une classe existante rend cette nouvelle version de votre bibliothèque compatible au format source et binaire avec le code qui en dépend.

### <a name="override"></a>override

Le modificateur `override` indique qu’une implémentation dérivée étend l’implémentation d’un membre de classe de base au lieu de la masquer. Le modificateur `virtual` doit être appliqué au membre de classe de base.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

**Sortie**

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

Le modificateur `override` est évalué au moment de la compilation et génère une erreur s’il ne trouve pas un membre virtuel à substituer.

Votre connaissance des techniques discutées et votre compréhension des situations dans lesquelles les utiliser, contribueront grandement à faciliter la transition entre les versions d’une bibliothèque.
