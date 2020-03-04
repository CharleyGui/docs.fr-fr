---
title: Bonnes pratiques pour l’écriture de tests unitaires
description: Découvrez les bonnes pratiques pour écrire des tests unitaires qui améliorent la qualité du code et la résilience pour les projets .NET Core et .NET Standard.
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 586373381bcb18384cbf29bb2ca2bd220a2b2d3d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240959"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a>Meilleures pratiques pour les tests unitaires avec .NET Core et .NET Standard

Il existe de nombreux avantages à écrire des tests unitaires. Ils facilitent la régression, fournissent de la documentation et simplifient la conception. Toutefois, les tests unitaires difficiles à lire et fragiles peuvent faire des ravages dans votre code base. Cet article décrit certaines meilleures pratiques concernant la conception de tests unitaires pour vos projets .NET Core et .NET Standard.

Dans ce guide, vous allez découvrir certaines bonnes pratiques à suivre pour écrire des tests unitaires résilients et faciles à comprendre.

Par [John Reese](https://reese.dev) avec des remerciements particuliers à [Roy Osherove](https://osherove.com/)

## <a name="why-unit-test"></a>Pourquoi un test unitaire ?

### <a name="less-time-performing-functional-tests"></a>Moins de temps pour effectuer des tests fonctionnels
Les tests fonctionnels sont coûteux. Ils impliquent généralement d’ouvrir l’application et d’effectuer une série d’étapes que vous (ou quelqu’un d’autre) devez suivre pour valider le comportement attendu. Dans la mesure où le testeur ne connaît pas toujours ces étapes, il doit contacter une personne plus compétente dans le domaine concerné pour effectuer le test. Le test lui-même peut prendre quelques secondes pour des changements mineurs, ou quelques minutes pour des changements plus importants. Enfin, ce processus doit être répété pour chaque changement apporté au système.

Les tests unitaires, en revanche, prennent quelques millisecondes. Vous pouvez les exécuter en appuyant sur un bouton sans nécessairement connaître le système dans son ensemble. La réussite ou non du test dépend du programme d’exécution de tests et non de la personne qui effectue le test.

### <a name="protection-against-regression"></a>Protection contre la régression
Les défauts de régression sont des défauts introduits quand un changement est apporté à l’application. Il est courant pour les testeurs de tester non seulement les nouvelles fonctionnalités, mais également les fonctionnalités antérieures afin de vérifier que ces dernières fonctionnent toujours comme prévu.

Avec les tests unitaires, vous pouvez réexécuter l’intégralité de votre suite de tests après chaque build ou même après avoir changé une ligne de code. Ainsi, vous avez l’assurance que votre nouveau code ne perturbe pas les fonctionnalités existantes.

### <a name="executable-documentation"></a>Documentation exécutable
Il n’est pas toujours évident de déterminer ce que fait une méthode particulière, ou comment elle se comporte en fonction d’une entrée spécifique. Vous pouvez vous demander : comment se comporte cette méthode si je lui passe une chaîne vide ? Null ?

Quand vous avez une suite de tests unitaires correctement nommés, chaque test doit pouvoir expliquer clairement la sortie attendue pour une entrée donnée. De plus, il doit pouvoir vérifier son bon fonctionnement.

### <a name="less-coupled-code"></a>Code moins couplé
Quand le code est fortement couplé, il peut être difficile d’effectuer des tests unitaires. Si vous ne créez pas de tests unitaires pour le code que vous écrivez, le couplage peut être moins apparent.

L’écriture de tests pour votre code permet de le découpler de manière naturelle. Sinon, il est plus difficile à tester.

## <a name="characteristics-of-a-good-unit-test"></a>Caractéristiques d’un bon test unitaire

- **Rapide**. Il n’est pas rare pour des projets matures de comporter des milliers de tests unitaires. Les tests unitaires doivent durer très peu de temps. Millisecondes.
- **Isolé**. Les tests unitaires sont autonomes et peuvent être exécutés de manière isolée. Ils ne dépendent d’aucun facteur externe, par exemple un système de fichiers ou une base de données.
- **Répétable**. L’exécution d’un test unitaire doit être cohérente avec ses résultats. En d’autres termes, il retourne toujours le même résultat si vous ne changez rien entre les exécutions.
- **Autovérification**. Le test doit pouvoir détecter automatiquement son état de réussite ou d’échec sans aucune interaction humaine.
- **Délai approprié**. Écrire un test unitaire ne doit pas prendre un temps disproportionné par rapport au code testé. Si vous trouvez que le test du code prend beaucoup de temps par rapport à son écriture, optez pour une conception plus facile à tester.

## <a name="lets-speak-the-same-language"></a>Parlons la même langue
Le terme *mock* (élément fictif) est malheureusement utilisé à très mauvais escient quand il s’agit de tests. Voici une définition des types les plus courants de *fakes* (éléments fictifs) pour l’écriture de tests unitaires :

*Fake* - Il s’agit d’un terme générique qui permet de décrire un stub ou un mock (objet fictif). Seul le contexte permet de déterminer s’il s’agit d’un stub ou d’un mock (objet fictif). En d’autres termes, un fake (élément fictif) peut être un stub ou un mob (objet fictif).

*Mock* - Il s’agit d’un objet fictif du système qui détermine la réussite ou l’échec d’un test unitaire. Un mock commence par être un Fake jusqu’à ce qu’il soit différencié par une assertion.

*Stub* - Un stub permet de remplacer de manière contrôlée une dépendance existante (ou collaborateur) dans le système. À l’aide d’un stub, vous pouvez tester votre code sans avoir à gérer directement la dépendance. Par défaut, un fake commence comme par être un stub.

Prenez l'exemple de l'extrait de code suivant :

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

Il s’agit d’un exemple de stub appelé mock. Dans le cas présent, il s’agit bien d’un stub. Vous passez simplement Order pour instancier `Purchase` (le système testé). Le nom `MockOrder` est également très trompeur, car encore une fois, order n’est pas un mock.

Il existe une meilleure approche

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

En renommant la classe en `FakeOrder`, vous avez rendu celle-ci beaucoup plus générique. Vous pouvez utiliser la classe en tant que mock ou stub. Selon ce qui est le plus approprié pour le cas de test. Dans l’exemple ci-dessus, `FakeOrder` est utilisé en tant que stub. Vous n’utilisez pas `FakeOrder` sous quelque forme que ce soit durant l’assertion. `FakeOrder` a simplement été passé à la classe `Purchase` pour répondre aux exigences du constructeur.

Pour l’utiliser en tant que Mock, vous pouvez faire quelque chose qui ressemble à ceci

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

Dans le cas présent, vous vérifiez une propriété sur le Fake (en le différenciant par assertion). Ainsi, dans l’extrait de code ci-dessus, `mockOrder` est un Mock.

> [!IMPORTANT]
> Il est important que cette terminologie soit correcte. Si vous appelez vos stubs « mocks », les autres développeurs vont faire de fausses hypothèses par rapport à votre intention.

Le point principal à retenir à propos des mocks et des stubs est que les mocks sont comme des stubs. Toutefois, vous différenciez le mock (objet fictif) par assertion, contrairement au stub.

## <a name="best-practices"></a>Meilleures pratiques

### <a name="naming-your-tests"></a>Nommage de vos tests
Le nom de votre test doit être composé de trois parties :

- Nom de la méthode testée
- Scénario de test utilisé
- Comportement attendu quand le scénario est appelé

#### <a name="why"></a>Pourquoi ?

- Les standards de nommage sont importants, car ils expriment explicitement la finalité du test.

Les tests ne se limitent pas à la vérification du bon fonctionnement de votre code, ils fournissent également de la documentation. En examinant simplement la suite de tests unitaires, vous devez pouvoir en déduire le comportement de votre code. De plus, en cas d’échec des tests, vous pouvez voir exactement quels sont les scénarios qui ne répondent pas à vos attentes.

#### <a name="bad"></a>Mauvais :
[!code-csharp[BeforeNaming](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a>Mieux :
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a>Organisation de vos tests
**Organisation, Action, Assertion** est un modèle courant pour les tests unitaires. Comme son nom l’indique, il comporte trois actions principales :

- *Organisation*, création et configuration des objets selon les besoins
- *Action* sur un objet
- *Assertion* de ce qui est prévu

#### <a name="why"></a>Pourquoi ?

- Permet de séparer clairement ce qui est testé des étapes *organisation* et *assertion*.
- Moins de risques de mélanger les assertions avec le code de l’étape « Action ».

La lisibilité est l’un des aspects les plus importants durant l’écriture d’un test. La séparation de chacune de ces actions dans le test met clairement en évidence les dépendances nécessaires à l’appel du code, le mode d’appel du code, ainsi que le contenu de l’assertion. Bien qu’il soit possible de combiner certaines étapes et de réduire la taille du test, l’objectif principal est de rendre le test aussi lisible que possible.

#### <a name="bad"></a>Mauvais :
[!code-csharp[BeforeArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a>Mieux :
[!code-csharp[AfterArranging](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a>Écrire des tests concluants minimaux
L’entrée à utiliser dans un test unitaire doit être la plus simple possible pour vérifier le comportement testé.

#### <a name="why"></a>Pourquoi ?

- Les tests deviennent plus résilients face aux futurs changements du code base.
- Plus proche du comportement de test que de l’implémentation.

Les tests qui contiennent plus d’informations que nécessaire pour être réussis ont plus de chances d’introduire des erreurs et peuvent rendre l’intention moins claire. Quand vous écrivez des tests, vous devez vous concentrer sur le comportement. La définition de propriétés supplémentaires pour les modèles ou l’utilisation de valeurs différentes de zéro quand cela n’est pas nécessaire, ne fait que nuire à ce que vous essayez de prouver.

#### <a name="bad"></a>Mauvais :
[!code-csharp[BeforeMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a>Mieux :
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a>Éviter les chaînes magiques
Le nommage des variables dans les tests unitaires est aussi important, sinon plus, que le nommage des variables dans le code de production. Les tests unitaires ne doivent pas contenir de chaînes magiques.

#### <a name="why"></a>Pourquoi ?

- Évite au lecteur du test d’inspecter le code de production pour déterminer ce qui rend la valeur spéciale.
- Montre explicitement ce que vous essayez de *prouver* et non ce que vous essayez d’*accomplir*.

Les chaînes magiques peuvent être sources de confusion pour le lecteur de vos tests. Si une chaîne semble inhabituelle, il peut se demander pourquoi une certaine valeur a été choisie pour un paramètre ou une valeur de retour. Cela peut l’amener à examiner de plus près les détails de l’implémentation, au lieu de se concentrer sur le test.

> [!TIP]
> Quand vous écrivez des tests, concentrez-vous au maximum sur l’expression de l’intention. Dans le cas des chaînes magiques, une bonne approche consiste à assigner ces valeurs à des constantes.

#### <a name="bad"></a>Mauvais :
[!code-csharp[BeforeMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a>Mieux :
[!code-csharp[AfterMagicString](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a>Éviter la logique dans les tests
Durant l’écriture des tests unitaires, évitez la concaténation manuelle des chaînes et les conditions logiques telles que `if`, `while`, `for`, `switch`, etc.

#### <a name="why"></a>Pourquoi ?

- Moins de risques d’introduire un bogue dans vos tests.
- Concentrez-vous sur le résultat final plutôt que sur les détails de l’implémentation.

Quand vous introduisez une logique dans votre suite de tests, le risque d’introduction d’un bogue augmente considérablement. Votre suite de tests est bien le dernier endroit où vous devez trouver un bogue. Le fonctionnement de vos tests doit présenter un niveau de fiabilité élevé, sinon vous n’aurez pas confiance en ces derniers. Les tests auxquels vous ne faites pas confiance n’ont aucune valeur. L’échec d’un test vous donne l’impression que quelque chose ne va pas dans votre code, et que vous ne pouvez pas l’ignorer.

> [!TIP]
> Si le recours à la logique dans votre test semble inévitable, scindez-le en deux ou plusieurs tests distincts.

#### <a name="bad"></a>Mauvais :
[!code-csharp[LogicInTests](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a>Mieux :
[!code-csharp[AfterTestLogic](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a>Préférez les méthodes d’assistance à setup et teardown
Si vous avez besoin d’un objet ou d’un état similaire pour vos tests, préférez une méthode d’assistance aux attributs Setup et Teardown, s’ils existent.

#### <a name="why"></a>Pourquoi ?

- Moins de confusion durant la lecture des tests, car l’ensemble du code est visible à partir de chaque test.
- Moins de risques d’effectuer une configuration excessive ou insuffisante pour le test donné.
- Moins de risques de partager l’état entre les tests, ce qui entraîne la création de dépendances indésirables entre eux.

Dans les frameworks de tests unitaires, `Setup` est appelé avant chaque test unitaire de votre suite de tests. Bien que certains puissent le voir comme un outil utile, cela aboutit généralement à des tests compliqués et difficiles à lire. Chaque test a généralement des exigences différentes pour être opérationnel. Malheureusement, `Setup` vous oblige à utiliser exactement les mêmes exigences pour chaque test.

> [!NOTE]
> xUnit a supprimé SetUp et TearDown depuis la version 2.x

#### <a name="bad"></a>Mauvais :
[!code-csharp[BeforeSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a>Mieux :
[!code-csharp[AfterHelperMethod](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a>Éviter les assertions multiples
Durant l’écriture des tests, essayez d’inclure uniquement une instruction Assert par test. Voici les approches courantes pour utiliser une seule assertion :

- Créez un test distinct pour chaque assertion.
- Utilisez des tests paramétrables.

#### <a name="why"></a>Pourquoi ?

- En cas d’échec d’une instruction Assert, les assertions qui suivent ne sont pas évaluées.
- Permet de vérifier que vous n’effectuez pas l’assertion de plusieurs cas dans vos tests.
- Vous donne une idée complète des causes de l’échec des tests.

Quand vous introduisez plusieurs assertions dans un cas de test, vous n’avez pas la garantie que toutes les assertions vont être exécutées. Dans la plupart des frameworks de tests unitaires, une fois qu’une assertion a été l’objet d’un échec dans un test unitaire, les tests en cours d’exécution sont automatiquement considérés comme défaillants. Cela peut être déroutant, car les fonctionnalités qui fonctionnent réellement indiquent un état d’échec.

> [!NOTE]
> Il existe une exception usuelle à cette règle : l’assertion d’un objet par différenciation. Dans ce cas, il est généralement acceptable d’avoir plusieurs assertions sur chaque propriété pour vérifier que l’objet se trouve dans l’état prévu.

#### <a name="bad"></a>Mauvais :
[!code-csharp[BeforeMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a>Mieux :
[!code-csharp[AfterMultipleAsserts](../../../samples/snippets/core/testing/unit-testing-best-practices/csharp/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a>Valider les méthodes privées en effectuant un test unitaire des méthodes publiques
Dans la plupart des cas, il n’est pas nécessaire de tester une méthode privée. Les méthodes privées sont un détail d’implémentation. Vous pouvez considérer la chose ainsi : les méthodes privées n’existent jamais de manière isolée. À un moment donné, une méthode publique appelle la méthode privée dans le cadre de son implémentation. Vous devez prendre en compte le résultat final de la méthode publique qui appelle la méthode privée.

Prenons le cas suivant

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = TrimInput(input);
    return sanitizedInput;
}

private string TrimInput(string input)
{
    return input.Trim();
}
```

Votre première réaction peut être de commencer à écrire un test pour `TrimInput`, car vous souhaitez vérifier que la méthode fonctionne comme prévu. Toutefois, il est tout à fait possible que `ParseLogLine` manipule `sanitizedInput` de manière inattendue, ce qui rend inutile tout test de `TrimInput`.

Le véritable test doit être effectué sur la méthode publique `ParseLogLine`, car c’est ce qui vous intéresse en fin de compte.

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

Ainsi, si vous voyez une méthode privée, recherchez la méthode publique et écrivez vos tests par rapport à cette méthode. Le fait qu’une méthode privée retourne le résultat attendu ne signifie pas que le système qui appelle la méthode privée utilise ce résultat correctement.

### <a name="stub-static-references"></a>Références statiques de stub
L’un des principes d’un test unitaire est qu’il doit avoir le contrôle total du système testé. Cela peut être problématique quand le code de production inclut des appels à des références statiques (par exemple `DateTime.Now`). Examinez le code suivant

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now.DayOfWeek == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

Comment ce code peut-il faire l’objet d’un test unitaire ? Vous pouvez tenter l’approche suivante

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

Malheureusement, vous allez vite réaliser que vos tests posent quelques problèmes.

- Si la suite de tests est exécutée un mardi, le second test est une réussite, mais le premier test est un échec.
- Si la suite de tests est exécutée un autre jour, le premier test est une réussite, mais le second test est un échec.

Pour résoudre ces problèmes, vous allez devoir introduire un *seam* dans votre code de production. Il existe une approche qui consiste à inclure dans un wrapper le code que vous devez contrôler dans une interface, et à faire en sorte que le code de production dépende de cette interface.

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday)
    {
        return price / 2;
    }
    else
    {
        return price;
    }
}
```

Votre suite de tests devient

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

Désormais, la suite de tests a un contrôle total sur `DateTime.Now` et peut créer un stub de n’importe quelle valeur au moment d’appeler la méthode.
