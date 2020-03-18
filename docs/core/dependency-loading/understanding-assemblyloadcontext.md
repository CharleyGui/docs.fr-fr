---
title: Comprendre AssemblyLoadContext - .NET Core
description: Concepts clés pour comprendre le but et le comportement de AssemblyLoadContext dans .NET Core.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8a73a432bf8cc72cced77cf6c62a785b72032913
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72291261"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>Comprendre System.Runtime.Loader.AssemblyLoadContext

La <xref:System.Runtime.Loader.AssemblyLoadContext> classe est unique à .NET Core. Cet article tente <xref:System.Runtime.Loader.AssemblyLoadContext> de compléter la documentation de l’API avec des informations conceptuelles.

Cet article est pertinent pour les développeurs mettant en œuvre le chargement dynamique, en particulier les développeurs de cadres de chargement dynamiques.

## <a name="what-is-the-assemblyloadcontext"></a>Qu’est-ce que le texte AssemblyLoadContext?

Chaque application .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext>utilise implicitement le .
C’est le fournisseur de l’heure d’exécution pour localiser et charger les dépendances. Chaque fois qu’une <xref:System.Runtime.Loader.AssemblyLoadContext> dépendance est chargée, une instance est invoquée pour la localiser.

- Il fournit un service de localisation, de chargement et de mise en cache d’assemblages gérés et d’autres dépendances.

- Pour prendre en charge le chargement et le déchargement dynamiques du code, il crée un contexte isolé pour le code de chargement et ses dépendances dans leur propre <xref:System.Runtime.Loader.AssemblyLoadContext> cas.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Quand avez-vous besoin de plusieurs instances AssemblyLoadContext ?

Une <xref:System.Runtime.Loader.AssemblyLoadContext> seule instance se limite au <xref:System.Reflection.Assembly> chargement exactement <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>d’une version d’un nom d’assemblage simple, .

Cette restriction peut devenir un problème lors du chargement dynamique des modules de code. Chaque module est compilé indépendamment et peut dépendre de différentes versions d’un <xref:System.Reflection.Assembly>. Ce problème se produit généralement lorsque différents modules dépendent de différentes versions d’une bibliothèque couramment utilisée.

Pour prendre en charge <xref:System.Runtime.Loader.AssemblyLoadContext> le code de chargement dynamique, <xref:System.Reflection.Assembly> l’API prévoit le chargement des versions contradictoires d’une application dans la même application. Chaque <xref:System.Runtime.Loader.AssemblyLoadContext> instance fournit une <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> cartographie unique <xref:System.Reflection.Assembly> de dictionnaire chacun à une instance spécifique.

Il fournit également un mécanisme pratique pour regrouper les dépendances liées à un module de code pour décharger plus tard.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>Qu’y a-t-il de spécial dans l’instance AssemblyLoadContext.Default ?

L’instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> est automatiquement peuplée par le temps d’exécution au démarrage.  Il utilise [l’enquête par défaut](default-probing.md) pour localiser et trouver toutes les dépendances statiques.

Il résout les scénarios de chargement de dépendance les plus courants.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>Comment AssemblyLoadContext soutient-il les dépendances dynamiques ?

<xref:System.Runtime.Loader.AssemblyLoadContext>a divers événements et fonctions virtuelles qui peuvent être remplacés.

L’instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> ne prend en charge que la suppression des événements.

Les articles [Managed assembly loading algorithm](loading-managed.md), Satellite assembly loading [algorithm](loading-resources.md), et [Unmanaged (native) library loading algorithm](loading-unmanaged.md) se réfèrent à tous les événements disponibles et les fonctions virtuelles.  Les articles montrent la position relative de chaque événement et de la fonction dans les algorithmes de chargement. Cet article ne reproduit pas cette information.

Cette section couvre les principes généraux des événements et fonctions pertinents.

- **Soyez reproductible**. Une requête en une dépendance spécifique doit toujours donner lieu à la même réponse. La même instance de dépendance chargée doit être retournée. Cette exigence est fondamentale pour la cohérence des caches. Pour les assemblages gérés en particulier, nous créons un <xref:System.Reflection.Assembly> cache. La clé cache est un <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>nom d’assemblage simple, .
- **Typiquement ne jetez pas**.  On s’attend à ce `null` que ces fonctions reviennent plutôt que de jeter lorsqu’elles ne sont pas en mesure de trouver la dépendance demandée. Le lancer mettra fin prématurément à la recherche et propagera une exception à l’appelant. Le lancer doit être limité à des erreurs inattendues comme un assemblage corrompu ou un état hors mémoire.
- **Évitez la récursion**. Sachez que ces fonctions et les gestionnaires mettent en œuvre les règles de chargement pour localiser les dépendances. Votre implémentation ne devrait pas appeler les API qui déclenchent la récursion. Votre code devrait généralement appeler les fonctions **de chargement AssemblyLoadContext** qui nécessitent un argument spécifique de référence de voie ou de mémoire.
- **Chargez-vous dans le correct AssemblyLoadContext**. Le choix de l’endroit où charger les dépendances est spécifique à l’application.  Le choix est mis en œuvre par ces événements et fonctions. Lorsque votre code appelle les fonctions de charge par voie **AssemblyLoadContext,** appelez-les dans l’instance où vous voulez que le code soit chargé. Parfois, `null` le <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> retour et laisser la poignée de la charge peut être l’option la plus simple.
- **Soyez conscient des courses de fil**. Le chargement peut être déclenché par plusieurs threads. L’AssemblageLoadContext gère les courses de threads en ajoutant atomiquement des assemblages à son cache. L’instance du perdant de la course est écartée. Dans votre logique d’implémentation, n’ajoutez pas de logique supplémentaire qui ne gère pas correctement plusieurs threads.

## <a name="how-are-dynamic-dependencies-isolated"></a>Comment les dépendances dynamiques sont-elles isolées?

Chaque <xref:System.Runtime.Loader.AssemblyLoadContext> instance représente une <xref:System.Reflection.Assembly> portée <xref:System.Type> unique pour les instances et les définitions.

Il n’y a pas d’isolement binaire entre ces dépendances. Ils sont isolés en ne se trouvant pas par leur nom.

Dans <xref:System.Runtime.Loader.AssemblyLoadContext>chaque :

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>peut se référer <xref:System.Reflection.Assembly> à un autre cas.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>peut retourner une instance de `name`type différente pour le même type .

## <a name="how-are-dependencies-shared"></a>Comment les dépendances sont-elles partagées?

Les dépendances peuvent facilement <xref:System.Runtime.Loader.AssemblyLoadContext> être partagées entre les instances. Le modèle général <xref:System.Runtime.Loader.AssemblyLoadContext> est pour un de charger une dépendance.  L’autre partage la dépendance en utilisant une référence à l’assemblage chargé.

Ce partage est exigé des assemblées de runtime. Ces assemblages ne peuvent <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>être chargés que dans le . La même chose est `ASP.NET`nécessaire `WPF`pour `WinForms`les cadres comme , , ou .

Il est recommandé que les dépendances <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>partagées devraient être chargées dans . Ce partage est le modèle de conception commun.

Le partage est mis en <xref:System.Runtime.Loader.AssemblyLoadContext> œuvre dans le codage de l’instance personnalisée. <xref:System.Runtime.Loader.AssemblyLoadContext>a divers événements et fonctions virtuelles qui peuvent être remplacés. Lorsque l’une de ces fonctions renvoie une référence à une <xref:System.Reflection.Assembly> instance qui a été chargée dans un autre <xref:System.Runtime.Loader.AssemblyLoadContext> cas, l’instance <xref:System.Reflection.Assembly> est partagée. L’algorithme de charge <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> standard s’en remet au chargement pour simplifier le modèle de partage commun.  Voir [l’algorithme de chargement d’assemblage géré](loading-managed.md).

## <a name="complications"></a>Complications

### <a name="type-conversion-issues"></a>Problèmes de conversion de type

Lorsque <xref:System.Runtime.Loader.AssemblyLoadContext> deux instances contiennent des `name`définitions de type avec la même, elles ne sont pas du même type. Ils sont du même type si et seulement <xref:System.Reflection.Assembly> s’ils viennent de la même instance.

Pour compliquer les choses, les messages d’exception au sujet de ces types dépareillés peuvent être déroutants. Les types sont mentionnés dans les messages d’exception par leurs noms de type simple. Le message d’exception commun en l’espèce serait du formulaire :

> L’objet de type 'IsolatedType' ne peut pas être converti en type 'IsolatedType'.

### <a name="debugging-type-conversion-issues"></a>Problèmes de conversion de type de débogage

Compte tenu d’une paire de types dépareillés, il est important de savoir aussi:

- Chaque type<xref:System.Type.Assembly?displayProperty=nameWithType>
- Chaque <xref:System.Runtime.Loader.AssemblyLoadContext>type, qui peut être obtenu <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> via la fonction.

Compte tenu `a` `b`de deux objets et , l’évaluation de ce qui suit dans le débbuggeur sera utile:

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>Résoudre les problèmes de conversion de type

Il existe deux modèles de conception pour résoudre ces problèmes de conversion de type.

1. Utilisez des types partagés courants. Ce type partagé peut être soit un type de temps d’exécution primitif, soit il peut impliquer la création d’un nouveau type partagé dans un assemblage partagé.  Souvent, le type partagé est une [interface](../../csharp/language-reference/keywords/interface.md) définie dans un assemblage d’applications. Voir aussi : [Comment les dépendances sont-elles partagées ?](#how-are-dependencies-shared).

2. Utilisez des techniques de marshaling pour convertir d’un type à un autre.
