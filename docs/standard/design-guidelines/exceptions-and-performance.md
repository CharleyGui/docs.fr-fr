---
title: Exceptions et performances
ms.date: 10/22/2008
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: babe378e0d61357709006e08f71ff578492f116c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734749"
---
# <a name="exceptions-and-performance"></a>Exceptions et performances

L’une des préoccupations courantes liées aux exceptions est que, si des exceptions sont utilisées pour du code qui échoue régulièrement, les performances de l’implémentation seront inacceptables. Cette inquiétude est tout à fait valide. Lorsqu’un membre lève une exception, ses performances peuvent être plus lentes. Toutefois, il est possible d’obtenir de bonnes performances tout en respectant strictement les règles d’exception qui interdisent l’utilisation de codes d’erreur. Deux modèles décrits dans cette section montrent comment procéder.

 ❌ N’utilisez pas de codes d’erreur en raison de problèmes liés au fait que les exceptions peuvent affecter les performances de manière négative.

 Pour améliorer les performances, il est possible d’utiliser le modèle de Tester-Doer ou le modèle de Try-Parse, décrit dans les deux sections suivantes.

## <a name="tester-doer-pattern"></a>Modèle de Tester-Doer

 Parfois, les performances d’un membre levant une exception peuvent être améliorées en divisant le membre en deux. Examinons la <xref:System.Collections.Generic.ICollection%601.Add%2A> méthode de l' <xref:System.Collections.Generic.ICollection%601> interface.

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 La méthode `Add` lève une exception si la collection est en lecture seule. Il peut s’agir d’un problème de performances dans les scénarios où l’appel de méthode est supposé échouer souvent. L’une des façons d’atténuer le problème consiste à tester si la collection est accessible en écriture avant d’essayer d’ajouter une valeur.

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 Le membre utilisé pour tester une condition, qui, dans notre exemple, est la propriété `IsReadOnly` , est appelé testeur. Le membre utilisé pour effectuer une opération de levée potentielle, la `Add` méthode dans notre exemple, est appelé Doer.

 ✔️ PRENDRE en compte le modèle de Tester-Doer pour les membres qui peuvent lever des exceptions dans des scénarios courants afin d’éviter les problèmes de performances liés aux exceptions.

## <a name="try-parse-pattern"></a>Modèle de Try-Parse

 Pour les API très performantes, il est préférable d’utiliser un modèle encore plus rapide que le modèle d' Tester-Doer décrit dans la section précédente. Le modèle appelle pour ajuster le nom de membre afin qu’un cas de test bien défini fasse partie de la sémantique de membre. Par exemple, <xref:System.DateTime> définit une <xref:System.DateTime.Parse%2A> méthode qui lève une exception en cas d’échec de l’analyse d’une chaîne. Il définit également une <xref:System.DateTime.TryParse%2A> méthode correspondante qui tente d’analyser, mais retourne la valeur false si l’analyse échoue et retourne le résultat d’une analyse réussie à l’aide d’un `out` paramètre.

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 Lors de l’utilisation de ce modèle, il est important de définir la fonctionnalité try en termes stricts. Si le membre échoue pour une raison autre que la tentative bien définie, le membre doit toujours lever une exception correspondante.

 ✔️ PRENDRE en compte le modèle de Try-Parse pour les membres qui peuvent lever des exceptions dans des scénarios courants afin d’éviter les problèmes de performances liés aux exceptions.

 ✔️ Utilisez le préfixe « try » et le type de retour booléen pour les méthodes qui implémentent ce modèle.

 ✔️ fournissez un membre levant des exceptions pour chaque membre à l’aide du modèle Try-Parse.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Instructions de conception pour les exceptions](exceptions.md)
