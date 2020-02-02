---
title: Créer des types mixin à l’aide de méthodes d’interface par défaut
description: À l’aide des membres d’interface par défaut, vous pouvez étendre les interfaces avec des implémentations par défaut facultatives pour les implémenteurs.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: f97410124a4ca5bbb10972ab5e7942fa4af68d72
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921447"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Didacticiel : combiner les fonctionnalités dans lors de la création de classes à l’aide d’interfaces avec les méthodes d’interface par défaut

Depuis C# 8.0 sur .NET Core 3.0, vous pouvez définir une implémentation lorsque vous déclarez un membre d’une interface. Cette fonctionnalité offre de nouvelles fonctionnalités qui vous permettent de définir des implémentations par défaut pour les fonctionnalités déclarées dans les interfaces. Les classes peuvent choisir quand remplacer les fonctionnalités, quand utiliser les fonctionnalités par défaut et quand ne pas déclarer la prise en charge des fonctionnalités discrètes.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Créez des interfaces avec des implémentations qui décrivent des fonctionnalités discrètes.
> * Créez des classes qui utilisent les implémentations par défaut.
> * Créez des classes qui remplacent une partie ou la totalité des implémentations par défaut.

## <a name="prerequisites"></a>Prerequisites

Vous devez configurer votre ordinateur pour exécuter .NET Core, y compris le C# compilateur 8,0. Le C# compilateur 8,0 est disponible à partir de [Visual Studio 2019 version 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)ou du [Kit de développement logiciel (SDK) .net Core 3,0](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.

## <a name="limitations-of-extension-methods"></a>Limitations des méthodes d’extension

L’une des façons dont vous pouvez implémenter le comportement qui s’affiche dans le cadre d’une interface est de définir des [méthodes d’extension](../programming-guide/classes-and-structs/extension-methods.md) qui fournissent le comportement par défaut. Les interfaces déclarent un ensemble minimal de membres tout en fournissant une plus grande surface d’exposition pour toute classe qui implémente cette interface. Par exemple, les méthodes d’extension dans <xref:System.Linq.Enumerable> fournissent l’implémentation pour toute séquence comme source d’une requête LINQ.

Les méthodes d’extension sont résolues au moment de la compilation, à l’aide du type déclaré de la variable. Les classes qui implémentent l’interface peuvent fournir une meilleure implémentation pour toute méthode d’extension. Les déclarations de variables doivent correspondre au type d’implémentation pour permettre au compilateur de choisir cette implémentation. Lorsque le type au moment de la compilation correspond à l’interface, les appels de méthode sont résolus à la méthode d’extension. Une autre préoccupation avec les méthodes d’extension est que ces méthodes sont accessibles partout où la classe qui contient les méthodes d’extension est accessible. Les classes ne peuvent pas déclarer si elles doivent ou ne doivent pas fournir des fonctionnalités déclarées dans les méthodes d’extension.

À partir C# de 8,0, vous pouvez déclarer les implémentations par défaut en tant que méthodes d’interface. Ensuite, chaque classe utilise automatiquement l’implémentation par défaut. Toute classe pouvant fournir une meilleure implémentation peut remplacer la définition de méthode d’interface par un meilleur algorithme. Dans un sens, cette technique ressemble à la façon dont vous pouvez utiliser les [méthodes d’extension](../programming-guide/classes-and-structs/extension-methods.md).

Dans cet article, vous allez découvrir comment les implémentations d’interface par défaut permettent de nouveaux scénarios.

## <a name="design-the-application"></a>Concevoir l’application

Prenons l’exemple d’une application domotique. Vous disposez probablement de nombreux types d’éclairages et d’indicateurs qui peuvent être utilisés dans l’ensemble de la maison. Chaque lumière doit prendre en charge les API pour les activer et les désactiver, et pour signaler l’état actuel. Certains éclairages et indicateurs peuvent prendre en charge d’autres fonctionnalités, telles que :

- Activez le voyant, puis désactivez-le après une minuterie.
- Faire clignoter la lumière pendant une période donnée.

Certaines de ces fonctionnalités étendues peuvent être émulées sur les appareils qui prennent en charge l’ensemble minimal. Qui indique la fourniture d’une implémentation par défaut. Pour les appareils qui ont plus de fonctionnalités intégrées, le logiciel de l’appareil utilise les fonctionnalités natives. Pour les autres lumières, elles peuvent choisir d’implémenter l’interface et d’utiliser l’implémentation par défaut.

Les membres d’interface par défaut sont une meilleure solution pour ce scénario que les méthodes d’extension. Les auteurs de classe peuvent contrôler les interfaces qu’ils choisissent d’implémenter. Les interfaces qu’ils choisissent sont disponibles en tant que méthodes. En outre, étant donné que les méthodes d’interface par défaut sont virtuelles par défaut, la distribution de méthode choisit toujours l’implémentation dans la classe.

Créons le code pour illustrer ces différences.

## <a name="create-interfaces"></a>Créer des interfaces

Commencez par créer l’interface qui définit le comportement de toutes les lumières :

[!code-csharp[Declare base interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

Un dispositif d’éclairage de surcharge de base peut implémenter cette interface comme indiqué dans le code suivant :

[!code-csharp[First overhead light](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

Dans ce didacticiel, le code ne pilote pas les appareils IoT, mais émule ces activités en écrivant des messages sur la console. Vous pouvez explorer le code sans automatiser votre maison.

Ensuite, nous allons définir l’interface pour une lumière qui peut s’éteindre automatiquement après un délai d’attente :

[!code-csharp[pure Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Vous pouvez ajouter une implémentation de base à la lumière de la surcharge, mais une meilleure solution consiste à modifier cette définition d’interface pour fournir une implémentation `virtual` par défaut :

[!code-csharp[Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

En ajoutant cette modification, la classe `OverheadLight` peut implémenter la fonction timer en déclarant la prise en charge de l’interface :

```csharp
public class OverheadLight : ITimerLight { }
```

Un type de lumière différent peut prendre en charge un protocole plus sophistiqué. Il peut fournir sa propre implémentation pour `TurnOnFor`, comme illustré dans le code suivant :

[!code-csharp[Override the timer function](~/samples/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

Contrairement aux méthodes de la classe virtuelle de substitution, la déclaration de `TurnOnFor` dans la classe `HalogenLight` n’utilise pas le mot clé `override`.

## <a name="mix-and-match-capabilities"></a>Fonctionnalités Mix et match

Les avantages des méthodes d’interface par défaut deviennent plus clairs lorsque vous introduisez des fonctionnalités plus avancées. L’utilisation d’interfaces vous permet de mélanger et de faire correspondre des fonctionnalités. Il permet également à chaque auteur de classe de choisir entre l’implémentation par défaut et une implémentation personnalisée. Nous allons ajouter une interface avec une implémentation par défaut pour une lumière clignotante :

[!code-csharp[Define the blinking light interface](~/samples/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

L’implémentation par défaut permet à tout éclairage de clignoter. La lumière de la surcharge peut ajouter des fonctionnalités de minuterie et de clignotement à l’aide de l’implémentation par défaut :

[!code-csharp[Use the default blink function](~/samples/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

Un nouveau type de lumière, le `LEDLight` prend en charge la fonction de minuteur et la fonction Blink directement. Ce style clair implémente à la fois les interfaces `ITimerLight` et `IBlinkingLight`, et remplace la méthode `Blink` :

[!code-csharp[Override the blink function](~/samples/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

Une `ExtraFancyLight` peut prendre en charge les fonctions de clignotement et de minuteur directement :

[!code-csharp[Override the blink and timer function](~/samples/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

Le `HalogenLight` que vous avez créé précédemment ne prend pas en charge le clignotement. Par conséquent, n’ajoutez pas le `IBlinkingLight` à la liste des interfaces prises en charge.

## <a name="detect-the-light-types-using-pattern-matching"></a>Détecter les types de lumière à l’aide de critères spéciaux

Nous allons ensuite écrire du code de test. Vous pouvez utiliser la fonctionnalité C#de mise en [correspondance des modèles](../pattern-matching.md) de pour déterminer les capacités d’un éclairage en examinant les interfaces qu’il prend en charge.  La méthode suivante exerce les fonctionnalités prises en charge de chaque lumière :

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

Le code suivant dans votre méthode `Main` crée chaque type de lumière dans la séquence et teste ce qui est clair :

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Comment le compilateur détermine la meilleure implémentation

Ce scénario montre une interface de base sans implémentation. L’ajout d’une méthode dans l’interface `ILight` introduit de nouvelles complexités. Les règles de langage régissant les méthodes d’interface par défaut réduisent l’effet sur les classes concrètes qui implémentent plusieurs interfaces dérivées. Nous allons améliorer l’interface d’origine avec une nouvelle méthode pour montrer comment cela modifie son utilisation. Chaque témoin lumineux peut signaler son état d’alimentation comme une valeur énumérée :

[!code-csharp[Enumeration for power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

L’implémentation par défaut suppose une alimentation secteur :

[!code-csharp[Report a default power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

Ces modifications sont compilées correctement, même si le `ExtraFancyLight` déclare la prise en charge de l’interface `ILight` et des deux interfaces dérivées, `ITimerLight` et `IBlinkingLight`. Il n’y a qu’une seule implémentation « la plus proche » déclarée dans l’interface `ILight`. Toute classe qui a déclaré une substitution devient l’implémentation « la plus proche ». Vous avez vu des exemples dans les classes précédentes qui a remplacé les membres d’autres interfaces dérivées.

Évitez de substituer la même méthode dans plusieurs interfaces dérivées. Si vous procédez ainsi, un appel de méthode ambigu est créé chaque fois qu’une classe implémente les deux interfaces dérivées. Le compilateur ne peut pas choisir une méthode unique pour qu’il génère une erreur. Par exemple, si les `IBlinkingLight` et `ITimerLight` implémentent une substitution de `PowerStatus`, le `OverheadLight` doit fournir une substitution plus spécifique. Sinon, le compilateur ne peut pas choisir entre les implémentations dans les deux interfaces dérivées. Vous pouvez généralement éviter cette situation en conservant les définitions d’interface de petite taille et en vous concentrant sur une seule fonctionnalité. Dans ce scénario, chaque fonctionnalité d’une lumière est sa propre interface ; plusieurs interfaces sont héritées uniquement par les classes.

Cet exemple illustre un scénario dans lequel vous pouvez définir des fonctionnalités discrètes qui peuvent être mélangées dans des classes. Vous déclarez tout ensemble de fonctionnalités prises en charge en déclarant les interfaces prises en charge par une classe. L’utilisation de méthodes d’interface par défaut virtuelles permet aux classes d’utiliser ou de définir une implémentation différente pour toute ou partie des méthodes d’interface. Cette fonctionnalité de langage offre de nouvelles façons de modéliser les systèmes réels que vous créez. Les méthodes d’interface par défaut offrent un moyen plus clair d’exprimer des classes connexes qui peuvent combiner et faire correspondre des fonctionnalités différentes à l’aide d’implémentations virtuelles de ces fonctionnalités.
