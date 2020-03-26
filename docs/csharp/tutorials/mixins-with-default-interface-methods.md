---
title: Créez des types de mixine à l’aide de méthodes d’interface par défaut
description: En utilisant des membres d’interface par défaut, vous pouvez étendre les interfaces avec des implémentations par défaut facultatives pour les implémenteurs.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: ee0536ef51f9bea3e6851be23cc19fa28cc6916b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134373"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Tutorial: Mix fonctionnalité dans la création de classes en utilisant des interfaces avec des méthodes d’interface par défaut

Depuis C# 8.0 sur .NET Core 3.0, vous pouvez définir une implémentation lorsque vous déclarez un membre d’une interface. Cette fonctionnalité fournit de nouvelles fonctionnalités où vous pouvez définir les implémentations par défaut pour les fonctionnalités déclarées dans les interfaces. Les classes peuvent choisir quand remplacer les fonctionnalités, quand utiliser la fonctionnalité par défaut et quand ne pas déclarer la prise en charge pour les fonctionnalités discrètes.

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> * Créez des interfaces avec des implémentations qui décrivent des fonctionnalités discrètes.
> * Créez des classes qui utilisent les implémentations par défaut.
> * Créez des classes qui remplacent une partie ou la totalité des implémentations par défaut.

## <a name="prerequisites"></a>Prérequis

Vous aurez besoin de configurer votre machine pour exécuter .NET Core, y compris le compilateur C 8.0. Le compilateur C 8.0 est disponible à partir de [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), ou le [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) ou plus tard.

## <a name="limitations-of-extension-methods"></a>Limitations des méthodes d’extension

Une façon d’implémenter un comportement qui apparaît dans le cadre d’une interface est de définir les [méthodes d’extension](../programming-guide/classes-and-structs/extension-methods.md) qui fournissent le comportement par défaut. Interfaces déclarer un ensemble minimum de membres tout en fournissant une plus grande surface pour toute classe qui implémente cette interface. Par exemple, les <xref:System.Linq.Enumerable> méthodes d’extension pour fournir la mise en œuvre de toute séquence à être la source d’une requête LINQ.

Les méthodes d’extension sont résolues au moment de la compilation, en utilisant le type déclaré de la variable. Les classes qui implémentent l’interface peuvent fournir une meilleure implémentation pour n’importe quelle méthode d’extension. Les déclarations variables doivent correspondre au type d’implémentation pour permettre au compilateur de choisir cette implémentation. Lorsque le type de compilation-temps correspond à l’interface, la méthode appelle résoudre à la méthode d’extension. Une autre préoccupation des méthodes d’extension est que ces méthodes sont accessibles partout où la classe contenant les méthodes d’extension est accessible. Les classes ne peuvent pas déclarer si elles doivent ou ne devraient pas fournir des fonctionnalités déclarées dans les méthodes d’extension.

En commençant par le C 8.0, vous pouvez déclarer les implémentations par défaut comme méthodes d’interface. Ensuite, chaque classe utilise automatiquement l’implémentation par défaut. Toute classe qui peut fournir une meilleure implémentation peut remplacer la définition de la méthode d’interface avec un meilleur algorithme. Dans un sens, cette technique ressemble à la façon dont vous pourriez utiliser des [méthodes d’extension](../programming-guide/classes-and-structs/extension-methods.md).

Dans cet article, vous apprendrez comment les implémentations d’interface par défaut permettent de nouveaux scénarios.

## <a name="design-the-application"></a>Concevoir l’application

Envisagez une application de domotique. Vous avez probablement beaucoup de différents types de lumières et d’indicateurs qui pourraient être utilisés dans toute la maison. Chaque lumière doit prendre en charge les API pour les activer et les éteindre, et pour signaler l’état actuel. Certaines lumières et indicateurs peuvent prendre en charge d’autres caractéristiques, telles que :

- Allumez la lumière, puis éteignez-la après une minuterie.
- Clignotez la lumière pendant un certain temps.

Certaines de ces capacités étendues pourraient être imitées dans des dispositifs qui prennent en charge l’ensemble minimal. Cela indique la fourniture d’une implémentation par défaut. Pour les appareils qui ont plus de capacités intégrées, le logiciel de l’appareil utiliserait les capacités natives. Pour d’autres lumières, ils peuvent choisir d’implémenter l’interface et d’utiliser la implémentation par défaut.

Les membres de l’interface par défaut sont une meilleure solution pour ce scénario que les méthodes d’extension. Les auteurs de classe peuvent contrôler les interfaces qu’ils choisissent d’implémenter. Ces interfaces qu’ils choisissent sont disponibles comme méthodes. En outre, parce que les méthodes d’interface par défaut sont virtuelles par défaut, l’expédition de méthode choisit toujours l’implémentation dans la classe.

Créons le code pour démontrer ces différences.

## <a name="create-interfaces"></a>Créer des interfaces

Commencez par créer l’interface qui définit le comportement pour toutes les lumières :

[!code-csharp[Declare base interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

Un luminaire de base peut implémenter cette interface comme indiqué dans le code suivant :

[!code-csharp[First overhead light](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

Dans ce tutoriel, le code ne conduit pas les appareils IoT, mais imite ces activités en écrivant des messages à la console. Vous pouvez explorer le code sans automatiser votre maison.

Ensuite, définissons l’interface pour une lumière qui peut automatiquement s’éteindre après un délai d’attente:

[!code-csharp[pure Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Vous pouvez ajouter une implémentation de base à la lumière aérienne, mais une meilleure solution est de modifier cette définition d’interface pour fournir une `virtual` implémentation par défaut:

[!code-csharp[Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

En ajoutant ce `OverheadLight` changement, la classe peut implémenter la fonction de minuterie en déclarant le support de l’interface :

```csharp
public class OverheadLight : ITimerLight { }
```

Un type de lumière différent peut prendre en charge un protocole plus sophistiqué. Il peut fournir sa `TurnOnFor`propre implémentation pour , comme indiqué dans le code suivant:

[!code-csharp[Override the timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

Contrairement aux méthodes de classe virtuelle `TurnOnFor` dominantes, la déclaration de dans la `HalogenLight` classe n’utilise pas le `override` mot clé.

## <a name="mix-and-match-capabilities"></a>Capacités de mélange et de correspondance

Les avantages des méthodes d’interface par défaut deviennent plus clairs lorsque vous introduisez des capacités plus avancées. L’utilisation d’interfaces vous permet de mélanger et de assortir les capacités. Il permet également à chaque auteur de classe de choisir entre la mise en œuvre par défaut et une implémentation personnalisée. Ajoutons une interface avec une implémentation par défaut pour une lumière clignotante :

[!code-csharp[Define the blinking light interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

L’implémentation par défaut permet à n’importe quelle lumière de clignoter. La lumière aérienne peut ajouter à la fois des capacités de minuterie et de clignotement à l’aide de la implémentation par défaut :

[!code-csharp[Use the default blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

Un nouveau type `LEDLight` de lumière, le prend en charge à la fois la fonction de minuterie et la fonction de clignotement directement. Ce style léger implémente à la fois le et `ITimerLight` `IBlinkingLight` les interfaces, et l’emporte sur la `Blink` méthode:

[!code-csharp[Override the blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

Un `ExtraFancyLight` peut prendre en charge directement les fonctions de clignotement et de minuterie :

[!code-csharp[Override the blink and timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

Le `HalogenLight` que vous avez créé plus tôt ne prend pas en charge les clignotements. Donc, n’ajoutez `IBlinkingLight` pas la liste de ses interfaces prises en charge.

## <a name="detect-the-light-types-using-pattern-matching"></a>Détecter les types de lumière à l’aide de l’appariement du modèle

Ensuite, écrivons du code de test. Vous pouvez utiliser la fonction de correspondance des [modèles](../pattern-matching.md) de C pour déterminer les capacités d’une lumière en examinant les interfaces qu’elle prend en charge.  La méthode suivante exerce les capacités supportées de chaque lumière :

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

Le code suivant `Main` dans votre méthode crée chaque type de lumière dans l’ordre et les tests qui s’allument:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Comment le compilateur détermine la meilleure implémentation

Ce scénario affiche une interface de base sans aucune implémentation. L’ajout d’une méthode dans l’interface `ILight` introduit de nouvelles complexités. Les règles linguistiques régissant les méthodes d’interface par défaut minimisent l’effet sur les classes concrètes qui implémentent plusieurs interfaces dérivées. Améliorons l’interface d’origine avec une nouvelle méthode pour montrer comment cela change son utilisation. Chaque voyant indicateur peut déclarer son statut de puissance comme une valeur énumérée :

[!code-csharp[Enumeration for power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

La mise en œuvre par défaut n’assume aucune puissance :

[!code-csharp[Report a default power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

Ces changements compilent proprement, `ExtraFancyLight` même si `ILight` le déclare le support `ITimerLight` `IBlinkingLight`pour l’interface et les deux interfaces dérivées, et . Il n’y a qu’une `ILight` seule implémentation « la plus proche » déclarée dans l’interface. Toute classe qui a déclaré un remplacement deviendrait la mise en œuvre la plus « proche ». Vous avez vu des exemples dans les classes précédentes qui ont dépassé les membres d’autres interfaces dérivées.

Évitez de passer outre la même méthode dans plusieurs interfaces dérivées. Cela crée un appel de méthode ambigu chaque fois qu’une classe implémente les deux interfaces dérivées. Le compilateur ne peut pas choisir une seule meilleure méthode de sorte qu’il émet une erreur. Par exemple, si `IBlinkingLight` `ITimerLight` le et mis `PowerStatus`en `OverheadLight` œuvre un remplacement de , le devrait fournir un remplacement plus spécifique. Sinon, le compilateur ne peut pas choisir entre les implémentations dans les deux interfaces dérivées. Vous pouvez généralement éviter cette situation en gardant les définitions d’interface petites et axées sur une seule fonctionnalité. Dans ce scénario, chaque capacité d’une lumière est sa propre interface; plusieurs interfaces ne sont héritées que par les classes.

Cet exemple montre un scénario où vous pouvez définir des fonctionnalités discrètes qui peuvent être mélangées en classes. Vous déclarez tout ensemble de fonctionnalités prises en déclarant quelles interfaces une classe prend en charge. L’utilisation de méthodes d’interface par défaut virtuelles permet aux classes d’utiliser ou de définir une implémentation différente pour l’une ou l’autre des méthodes d’interface. Cette capacité linguistique offre de nouvelles façons de modéliser les systèmes du monde réel que vous construisez. Les méthodes d’interface par défaut offrent un moyen plus clair d’exprimer des classes connexes qui peuvent mélanger et assortir différentes fonctionnalités à l’aide d’implémentations virtuelles de ces capacités.
