---
title: Comprendre AssemblyLoadContext-.NET Core
description: Concepts clés pour comprendre l’objectif et le comportement de AssemblyLoadContext dans .NET Core.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8a73a432bf8cc72cced77cf6c62a785b72032913
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291261"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>Fonctionnement de System. Runtime. Loader. AssemblyLoadContext

La classe <xref:System.Runtime.Loader.AssemblyLoadContext> est propre à .NET Core. Cet article tente de compléter la documentation de l’API <xref:System.Runtime.Loader.AssemblyLoadContext> à l’aide d’informations conceptuelles.

Cet article s’applique aux développeurs qui implémentent le chargement dynamique, en particulier les développeurs d’infrastructures de chargement dynamique.

## <a name="what-is-the-assemblyloadcontext"></a>Qu’est-ce que le AssemblyLoadContext ?

Chaque application .NET Core utilise implicitement l' <xref:System.Runtime.Loader.AssemblyLoadContext>.
Il s’agit du fournisseur du runtime pour la localisation et le chargement des dépendances. Chaque fois qu’une dépendance est chargée, une <xref:System.Runtime.Loader.AssemblyLoadContext> instance est appelée pour la localiser.

- Il fournit un service de localisation, de chargement et de mise en cache des assemblys managés et d’autres dépendances.

- Pour prendre en charge le chargement et le déchargement de code dynamique, il crée un contexte isolé pour le chargement du code et de ses dépendances dans leur propre instance <xref:System.Runtime.Loader.AssemblyLoadContext>.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Quand avez-vous besoin de plusieurs instances AssemblyLoadContext ?

Une seule instance de <xref:System.Runtime.Loader.AssemblyLoadContext> est limitée au chargement d’une seule version d’une <xref:System.Reflection.Assembly> par nom d’assembly simple, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>.

Cette restriction peut devenir un problème lors du chargement dynamique des modules de code. Chaque module est compilé indépendamment et peut dépendre de différentes versions d’un <xref:System.Reflection.Assembly>. Ce problème se produit généralement lorsque les différents modules dépendent de différentes versions d’une bibliothèque couramment utilisée.

Pour prendre en charge le chargement dynamique du code, l’API <xref:System.Runtime.Loader.AssemblyLoadContext> permet de charger les versions conflictuelles d’un <xref:System.Reflection.Assembly> dans la même application. Chaque instance de <xref:System.Runtime.Loader.AssemblyLoadContext> fournit un mappage de dictionnaire unique chaque <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> à une instance de <xref:System.Reflection.Assembly> spécifique.

Il fournit également un mécanisme pratique pour regrouper les dépendances liées à un module de code en vue d’un déchargement ultérieur.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>Qu’est-ce qui est spécial à propos de l’instance AssemblyLoadContext. default ?

L’instance de <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> est automatiquement renseignée par le runtime au démarrage.  Elle utilise la [détection par défaut](default-probing.md) pour rechercher et rechercher toutes les dépendances statiques.

Il résout les scénarios de chargement de dépendances les plus courants.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>Comment AssemblyLoadContext prend-il en charge les dépendances dynamiques ?

<xref:System.Runtime.Loader.AssemblyLoadContext> a plusieurs événements et fonctions virtuelles qui peuvent être substitués.

L’instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> ne prend en charge que le remplacement des événements.

Les articles [algorithme de chargement d’assembly géré](loading-managed.md), [algorithme de chargement d’assembly satellite](loading-resources.md)et [algorithme de chargement de bibliothèque non managée (natif)](loading-unmanaged.md) font référence à tous les événements et fonctions virtuelles disponibles.  Les articles montrent la position relative de chaque événement et de chaque fonction dans les algorithmes de chargement. Cet article ne reproduit pas ces informations.

Cette section décrit les principes généraux des événements et des fonctions pertinents.

- **Soyez renouvelable**. Une requête pour une dépendance spécifique doit toujours aboutir à la même réponse. La même instance de dépendance chargée doit être retournée. Cette exigence est fondamentale pour la cohérence du cache. Pour les assemblys managés, en particulier, nous créons un cache de <xref:System.Reflection.Assembly>. La clé de cache est un nom d’assembly simple, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>.
- **En général, ne levez pas d’exception**.  Il est supposé que ces fonctions retournent `null` au lieu d’une exception Throw lorsqu’il est impossible de trouver la dépendance demandée. La levée met fin prématurément à la recherche et propage une exception à l’appelant. La levée doit être limitée à des erreurs inattendues, telles qu’un assembly endommagé ou une condition de mémoire insuffisante.
- **Évitez la récursivité**. N’oubliez pas que ces fonctions et gestionnaires implémentent les règles de chargement pour localiser les dépendances. Votre implémentation ne doit pas appeler les API qui déclenchent la récursivité. Votre code doit généralement appeler des fonctions de chargement **AssemblyLoadContext** qui requièrent un argument de référence de mémoire ou un chemin d’accès spécifique.
- **Chargez dans le bon AssemblyLoadContext**. Le choix de l’emplacement de chargement des dépendances est spécifique à l’application.  Le choix est implémenté par ces événements et fonctions. Lorsque votre code appelle des fonctions de chargement par chemin d’accès **AssemblyLoadContext** , appelez-les sur l’instance où vous souhaitez que le code soit chargé. L’option la plus simple consiste à retourner des `null` et à laisser le <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> gérer la charge.
- **Tenez compte des concurrences de thread**. Le chargement peut être déclenché par plusieurs threads. AssemblyLoadContext gère les courses de threads en ajoutant atomiquement des assemblys à son cache. L’instance de la course perdante est ignorée. Dans votre logique d’implémentation, n’ajoutez pas de logique supplémentaire qui ne gère pas correctement plusieurs threads.

## <a name="how-are-dynamic-dependencies-isolated"></a>Comment les dépendances dynamiques sont-elles isolées ?

Chaque <xref:System.Runtime.Loader.AssemblyLoadContext> instance représente une étendue unique pour les définitions de <xref:System.Type> et les instances de <xref:System.Reflection.Assembly>.

Il n’y a pas d’isolation binaire entre ces dépendances. Elles sont isolées uniquement si elles ne se trouvent pas mutuellement par nom.

Dans chaque <xref:System.Runtime.Loader.AssemblyLoadContext>:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> peut faire référence à une autre <xref:System.Reflection.Assembly> instance.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType> peut retourner une instance de type différente pour le même `name`de type.

## <a name="how-are-dependencies-shared"></a>Comment les dépendances sont-elles partagées ?

Les dépendances peuvent facilement être partagées entre des instances de <xref:System.Runtime.Loader.AssemblyLoadContext>. Le modèle général correspond à un <xref:System.Runtime.Loader.AssemblyLoadContext> pour charger une dépendance.  L’autre partage la dépendance à l’aide d’une référence à l’assembly chargé.

Ce partage est requis pour les assemblys du Runtime. Ces assemblys peuvent uniquement être chargés dans le <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>. Il en est de même pour les infrastructures comme `ASP.NET`, `WPF`ou `WinForms`.

Il est recommandé de charger les dépendances partagées dans <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>. Ce partage est le modèle de conception courant.

Le partage est implémenté dans le codage de l’instance de <xref:System.Runtime.Loader.AssemblyLoadContext> personnalisée. <xref:System.Runtime.Loader.AssemblyLoadContext> a plusieurs événements et fonctions virtuelles qui peuvent être substitués. Quand l’une de ces fonctions retourne une référence à une instance de <xref:System.Reflection.Assembly> qui a été chargée dans une autre <xref:System.Runtime.Loader.AssemblyLoadContext> instance, l’instance <xref:System.Reflection.Assembly> est partagée. L’algorithme de chargement standard diffère pour <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> pour le chargement afin de simplifier le modèle de partage commun.  Consultez [algorithme de chargement d’assembly managé](loading-managed.md).

## <a name="complications"></a>Complications

### <a name="type-conversion-issues"></a>Problèmes de conversion de type

Lorsque deux instances <xref:System.Runtime.Loader.AssemblyLoadContext> contiennent des définitions de type avec le même `name`, elles ne sont pas du même type. Ils sont du même type si et seulement s’ils proviennent de la même instance de <xref:System.Reflection.Assembly>.

Pour compliquer les choses, les messages d’exception concernant ces types incompatibles peuvent prêter à confusion. Les types sont référencés dans les messages d’exception par leurs noms de types simples. Dans ce cas, le message d’exception courant se présente sous la forme suivante :

> L’objet de type’IsolatedType’ne peut pas être converti en type’IsolatedType'.

### <a name="debugging-type-conversion-issues"></a>Débogage des problèmes de conversion de type

À partir d’une paire de types incompatibles, il est également important de savoir :

- <xref:System.Type.Assembly?displayProperty=nameWithType> de chaque type
- <xref:System.Runtime.Loader.AssemblyLoadContext>de chaque type, qui peut être obtenu via la fonction <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType>.

À partir de deux objets `a` et `b`, l’évaluation de ce qui suit dans le débogueur s’avère utile :

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>Résolution des problèmes de conversion de type

Il existe deux modèles de conception pour résoudre ces problèmes de conversion de type.

1. Utilisez les types partagés communs. Ce type partagé peut être un type de Runtime primitif, ou il peut impliquer la création d’un nouveau type partagé dans un assembly partagé.  Le type partagé est souvent une [interface](../../csharp/language-reference/keywords/interface.md) définie dans un assembly d’application. Voir aussi : [Comment les dépendances sont-elles partagées ?](#how-are-dependencies-shared).

2. Utilisez les techniques de marshaling pour convertir d’un type en un autre.
