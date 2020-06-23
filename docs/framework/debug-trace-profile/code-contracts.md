---
title: Contrats de code
description: Explorez les contrats de code, qui fournissent un moyen de spécifier des conditions préalables, des post-conditions et des invariants d’objet dans votre code .NET.
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
ms.openlocfilehash: 60f794373af75bd3f745c224e0a8c7a84192e4c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904141"
---
# <a name="code-contracts"></a>Contrats de code

Les contrats de code offrent un moyen de spécifier des conditions préalables, des post-conditions et des invariants d'objet dans votre code. Les conditions préalables sont des exigences qui doivent être satisfaites à l'entrée d'une méthode ou d'une propriété. Les post-conditions décrivent les attentes à la sortie de la méthode ou de la propriété. Les invariants d'objet décrivent l'état attendu pour une classe présentant un état correct.

Les contrats de code incluent des classes pour le marquage de votre code, un analyseur statique pour l'analyse au moment de la compilation, ainsi qu'un analyseur au moment de l'exécution. Les classes des contrats de code se trouvent dans l'espace de noms <xref:System.Diagnostics.Contracts>.

Les contrats de code offrent les avantages suivants :

- Tests améliorés : les contrats de code permettent la vérification de contrat statique, la vérification au moment de l'exécution et la génération de documentation.

- Outils de test automatique : vous pouvez utiliser les contrats de code pour générer des tests unitaires plus explicites en filtrant les arguments de test sans signification qui ne remplissent pas les conditions préalables.

- Vérification statique : le vérificateur statique peut déterminer s'il existe des violations de contrat sans exécuter le programme. Il recherche des contrats implicites, tels que des déréférencements et des limites de tableau null, ainsi que des contrats explicites.

- Documentation de référence : le générateur de documentation complète les fichiers de documentation XML existants avec des informations de contrat. Des feuilles de style peuvent également être utilisées avec [Sandcastle](https://github.com/EWSoftware/SHFB) pour ajouter des sections de contrat dans les pages de documentation générées.

Tous les langages .NET Framework peuvent directement utiliser les contrats, sans que vous ayez besoin de développer un analyseur ou compilateur spécial. Un complément Visual Studio vous permet de spécifier le niveau d'analyse de contrats de code à effectuer. Les analyseurs peuvent vérifier que les contrats sont correctement écrits (contrôle de type et résolution de noms), et créer un formulaire compilé des contrats au format MSIL (Microsoft Intermediate Language). La création de contrats dans Visual Studio vous permet de tirer parti de la fonctionnalité IntelliSense standard fournie par l'outil.

La plupart des méthodes dans la classe de contrat sont compilées de façon conditionnelle, à savoir que le compilateur effectue des appels à ces méthodes uniquement si vous définissez le symbole spécial CONTRACTS_FULL à l'aide de la directive `#define`. Avec CONTRACTS_FULL, vous pouvez écrire des contrats dans votre code sans utiliser de directives `#ifdef`, et générer ainsi différentes builds, avec et sans contrats.

Pour obtenir des outils et des instructions détaillées sur l’utilisation des contrats de code, consultez [contrats de code](https://marketplace.visualstudio.com/items?itemName=RiSEResearchinSoftwareEngineering.CodeContractsforNET) sur le site Visual Studio Marketplace.

## <a name="preconditions"></a>Preconditions

Vous pouvez spécifier des conditions préalables à l'aide de la méthode <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType>. Les conditions préalables définissent l'état à l'appel d'une méthode. Elles sont généralement utilisées pour indiquer des valeurs de paramètre valides. Tous les membres spécifiés dans les conditions préalables doivent être au moins aussi accessibles que la méthode elle-même. Autrement, la condition préalable risque de ne pas être comprise par tous les appelants de la méthode. La condition ne doit pas avoir d'effets secondaires. Le comportement au moment de l'exécution des conditions préalables non réussies est déterminé par l'analyseur au moment de l'exécution.

Par exemple, la condition préalable suivante spécifie que le paramètre `x` ne doit pas être null.

```csharp
Contract.Requires(x != null);
```

Si votre code doit lever une exception particulière en cas d'échec d'une condition préalable, utilisez la surcharge générique de <xref:System.Diagnostics.Contracts.Contract.Requires%2A> comme suit.

```csharp
Contract.Requires<ArgumentNullException>(x != null, "x");
```

### <a name="legacy-requires-statements"></a>Instructions Requires héritées

Dans la plupart des cas, le code contient du code de validation de paramètres sous la forme d’instructions `if`-`then`-`throw`. Les outils de contrat reconnaissent ces instructions comme étant des conditions préalables dans les cas suivants :

- Ces instructions sont placées avant toutes les autres instructions dans une méthode.

- L'ensemble de ces instructions est suivi d'un appel de méthode <xref:System.Diagnostics.Contracts.Contract> explicite, tel qu'un appel à la méthode <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A> ou <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>.

Quand les instructions `if`-`then`-`throw` apparaissent sous cette forme, les outils les reconnaissent en tant qu’instructions `requires` héritées. Si aucun autre contrat ne suit la séquence `if`-`then`-`throw`, terminez le code par la méthode <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType>.

```csharp
if (x == null) throw new ...
Contract.EndContractBlock(); // All previous "if" checks are preconditions
```

Notez que la condition du test précédent est une condition préalable négative (La condition préalable réelle est `x != null` .) Une condition préalable négative est très restreinte : elle doit être écrite comme indiqué dans l’exemple précédent. autrement dit, il ne doit pas contenir `else` de clauses, et le corps de la `then` clause doit être une `throw` instruction unique. Le test `if` est soumis aux règles de pureté et à celles de visibilité (voir [Indications relatives à l’utilisation](#usage_guidelines)), mais l’expression `throw` est soumise uniquement aux règles de pureté. Toutefois, le type de l'exception levée doit être aussi visible que la méthode dans laquelle le contrat se produit.

## <a name="postconditions"></a>Postconditions

Les post-conditions sont des contrats relatifs à l'état d'une méthode qui se termine. La post-condition est vérifiée juste avant la sortie de la méthode. Le comportement au moment de l'exécution des post-conditions non réussies est déterminé par l'analyseur au moment de l'exécution.

Contrairement aux conditions préalables, les post-conditions peuvent référencer des membres ayant moins de visibilité. Il est possible qu'un client ne puisse pas comprendre ou utiliser certaines des informations spécifiées par une post-condition avec un état privé, mais cela n'empêche pas le client d'utiliser la méthode correctement.

### <a name="standard-postconditions"></a>Post-conditions standard

Vous pouvez spécifier les post-conditions standard à l'aide de la méthode <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>. Les post-conditions expriment une condition qui doit être `true` à l'arrêt normal de la méthode.

```csharp
Contract.Ensures(this.F > 0);
```

### <a name="exceptional-postconditions"></a>Post-conditions exceptionnelles

Les post-conditions exceptionnelles sont des post-conditions qui doivent être `true` quand une exception particulière est levée par une méthode. Vous pouvez les spécifier à l'aide de la méthode <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType>, comme le montre l'exemple suivant.

```csharp
Contract.EnsuresOnThrow<T>(this.F > 0);
```

L’argument est la condition qui doit être `true` chaque fois qu’une exception qui est un sous-type de `T` est levée.

Certains types d'exception sont difficiles à utiliser dans une post-condition exceptionnelle. Par exemple, l'utilisation du type <xref:System.Exception> pour `T` nécessite que la méthode garantisse la condition indépendamment du type d'exception levée, même s'il s'agit d'un dépassement de capacité de la pile ou d'une autre exception impossible à contrôler. Utilisez les post-conditions exceptionnelles uniquement pour des exceptions spécifiques qui peuvent être levées après l'appel d'un membre, par exemple, quand une exception <xref:System.InvalidTimeZoneException> est levée pour un appel de méthode <xref:System.TimeZoneInfo>.

### <a name="special-postconditions"></a>Post-conditions spéciales

Les méthodes suivantes peuvent être utilisées uniquement au sein de post-conditions :

- Vous pouvez faire référence aux valeurs de retour de la méthode dans les post-conditions à l'aide de l'expression `Contract.Result<T>()`, où `T` est remplacé par le type de retour de la méthode. Si le compilateur ne peut pas déduire le type, vous devez le fournir explicitement. Par exemple, le compilateur C# ne peut pas déduire les types des méthodes qui ne prennent pas d'arguments. Il nécessite donc la post-condition suivante : `Contract.Ensures(0 <Contract.Result<int>())`. Les méthodes possédant le type de retour `void` ne peuvent pas faire référence à `Contract.Result<T>()` dans leurs post-conditions.

- Une valeur de « pré-état » dans une post-condition fait référence à la valeur d'une expression au début d'une méthode ou d'une propriété. Elle utilise l'expression `Contract.OldValue<T>(e)`, où `T` est le type de `e`. Vous pouvez omettre l'argument de type générique chaque fois que le compilateur est en mesure de déduire son type (Par exemple, le compilateur C# déduit toujours le type, car il accepte un argument.) Il existe plusieurs restrictions sur ce qui peut se produire dans `e` et les contextes dans lesquels une expression ancienne peut apparaître. Une expression ancienne ne peut pas contenir une autre expression ancienne. Encore plus important, une expression ancienne doit faire référence à une valeur qui a existé dans l'état de condition préalable de la méthode. En d'autres termes, il doit s'agir d'une expression qui peut être évaluée tant que la condition préalable de la méthode est `true`. Voici plusieurs instances de cette règle :

  - La valeur doit exister dans l'état de condition préalable de la méthode. Pour pouvoir référencer un champ sur un objet, les conditions préalables doivent garantir que l’objet est toujours non null.

  - Vous ne pouvez pas faire référence à la valeur de retour de la méthode dans une expression ancienne :

      ```csharp
      Contract.OldValue(Contract.Result<int>() + x) // ERROR
      ```

  - Vous ne pouvez pas faire référence aux paramètres `out` dans une expression ancienne.

  - Une expression ancienne ne peut pas dépendre de la variable liée d'un quantificateur si la plage du quantificateur dépend de la valeur de retour de la méthode :

      ```csharp
      Contract.ForAll(0, Contract.Result<int>(), i => Contract.OldValue(xs[i]) > 3); // ERROR
      ```

  - Une expression ancienne ne peut pas faire référence au paramètre du délégué anonyme dans un appel <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> ou <xref:System.Diagnostics.Contracts.Contract.Exists%2A>, sauf si elle est utilisée en tant qu’indexeur ou argument pour un appel de méthode :

      ```csharp
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(xs[i]) > 3); // OK
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(i) > 3); // ERROR
      ```

  - Une expression ancienne ne peut pas s'utiliser dans le corps d'un délégué anonyme si la valeur de l'expression ancienne dépend de l'un des paramètres du délégué anonyme, à moins que le délégué anonyme ne soit un argument de la méthode <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> ou <xref:System.Diagnostics.Contracts.Contract.Exists%2A> :

      ```csharp
      Method(... (T t) => Contract.OldValue(... t ...) ...); // ERROR
      ```

  - Les paramètres `Out` posent un problème, car les contrats sont placés avant le corps de la méthode, et la plupart des compilateurs n'autorisent pas les références aux paramètres `out` dans les post-conditions. Pour résoudre ce problème, la classe <xref:System.Diagnostics.Contracts.Contract> fournit la méthode <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A>, qui permet d'utiliser une post-condition basée sur un paramètre `out`.

      ```csharp
      public void OutParam(out int x)
      {
          Contract.Ensures(Contract.ValueAtReturn(out x) == 3);
          x = 3;
      }
      ```

      Comme avec la méthode <xref:System.Diagnostics.Contracts.Contract.OldValue%2A>, vous pouvez omettre le paramètre de type générique chaque fois que le compilateur est en mesure de déduire son type. Le module de réécriture de contrat remplace l'appel de méthode par la valeur du paramètre `out`. La méthode <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> peut apparaître uniquement dans des post-conditions. L’argument de la méthode doit être un paramètre `out` ou un champ d’un paramètre `out` de structure. Ce dernier est également utile pour faire référence aux champs dans la post-condition d'un constructeur de structure.

      > [!NOTE]
      > Actuellement, les outils d'analyse de contrat de code ne vérifient pas si les paramètres `out` sont correctement initialisés et ignorent leur mention dans la post-condition. Si, dans l'exemple précédent, la ligne après le contrat avait utilisé la valeur de `x` au lieu de lui assigner un nombre entier, un compilateur n'aurait donc pas généré l'erreur correspondante. Toutefois, dans une build où le symbole de préprocesseur CONTRACTS_FULL n’est pas défini (telle qu’une build de mise en production), le compilateur génère une erreur.

## <a name="invariants"></a>Invariants

Les invariants d'objet sont des conditions qui doivent être remplies (true) pour chaque instance d'une classe dès que cet objet est visible par un client. Ils spécifient les conditions sous lesquelles l'objet est considéré comme étant correct.

Les méthodes invariantes sont identifiées par l'attribut <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute>. Elles ne doivent contenir aucun code à l'exception d'une séquence d'appels à la méthode <xref:System.Diagnostics.Contracts.Contract.Invariant%2A>, chacun spécifiant un invariant individuel, comme indiqué dans l'exemple suivant.

```csharp
[ContractInvariantMethod]
protected void ObjectInvariant ()
{
    Contract.Invariant(this.y >= 0);
    Contract.Invariant(this.x > this.y);
    ...
}
```

Les invariants sont définis de façon conditionnelle par le symbole de préprocesseur CONTRACTS_FULL. Ils sont vérifiés au moment de l'exécution à la fin de chaque méthode publique. Si un invariant spécifie une méthode publique dans la même classe, la vérification d'invariant prévue normalement à la fin de cette méthode publique est désactivée. À la place, la vérification se produit uniquement à la fin de l'appel de méthode le plus à l'extérieur de cette classe. Cela se produit également si la classe est à nouveau entrée à cause d'un appel à une méthode sur une autre classe. Les invariants ne sont pas vérifiés pour un finaliseur d’objet et une <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implémentation.

<a name="usage_guidelines"></a>

## <a name="usage-guidelines"></a>Instructions d’utilisation

### <a name="contract-ordering"></a>Classement de contrat

Le tableau suivant indique l'ordre des éléments à utiliser quand vous écrivez des contrats de méthode.

|`If-then-throw statements`|Conditions préalables publiques à compatibilité descendante|
|-|-|
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|Toutes les conditions préalables publiques|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Toutes les post-conditions standard publiques|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Toutes les post-conditions exceptionnelles publiques|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Toutes les post-conditions standard privées/internes|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Toutes les post-conditions exceptionnelles privées/internes|
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|Si vous utilisez des conditions préalables de style `if`-`then`-`throw` sans autres contrats, ajoutez un appel à <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> pour indiquer que toutes les vérifications if précédentes sont des conditions préalables.|

<a name="purity"></a>

### <a name="purity"></a>Pureté

Toutes les méthodes appelées dans un contrat doivent être pures, c'est-à-dire qu'elles ne doivent pas mettre à jour un état préexistant. Une méthode pure peut modifier des objets qui ont été créés après l'entrée dans la méthode pure.

Les outils de contrat de code considèrent actuellement que les éléments de code suivants sont purs :

- Méthodes marquées avec l'attribut <xref:System.Diagnostics.Contracts.PureAttribute>.

- Types marqués avec l'attribut <xref:System.Diagnostics.Contracts.PureAttribute> (cet attribut s'applique à toutes les méthodes du type).

- Accesseurs get de propriété.

- Opérateurs (méthodes statiques dont le nom commence par « op », qui comportent un ou deux paramètres et dont le type de retour n’est pas void).

- Méthodes dont le nom qualifié complet commence par « System.Diagnostics.Contracts.Contract », « System.String », « System.IO.Path » ou « System.Type ».

- Les délégués appelés, à condition que le type délégué lui-même soit attribué avec l'attribut <xref:System.Diagnostics.Contracts.PureAttribute>. Les types délégués <xref:System.Predicate%601?displayProperty=nameWithType> et <xref:System.Comparison%601?displayProperty=nameWithType> sont considérés comme purs.

<a name="visibility"></a>

### <a name="visibility"></a>Visibilité

Tous les membres indiqués dans un contrat doivent être au moins aussi visibles que la méthode dans laquelle ils apparaissent. Par exemple, un champ privé ne peut pas être spécifié dans une condition préalable pour une méthode publique, car les clients ne peuvent pas valider un tel contrat avant d'appeler la méthode. Cependant, si le champ est marqué avec l'attribut <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, il est exempté de ces règles.

## <a name="example"></a>Exemple

L'exemple suivant illustre l'utilisation des contrats de code.

[!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
[!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
