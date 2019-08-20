---
title: Exceptions et performances
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: KrzysztofCwalina
ms.openlocfilehash: 967692092186b81802a7ab635ea8fe4dbacd49ed
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611520"
---
# <a name="exceptions-and-performance"></a>Exceptions et performances
L’une des préoccupations courantes liées aux exceptions est que, si des exceptions sont utilisées pour du code qui échoue régulièrement, les performances de l’implémentation seront inacceptables. Il s’agit d’un problème valide. Lorsqu’un membre lève une exception, ses performances peuvent être plus lentes. Toutefois, il est possible d’obtenir de bonnes performances tout en respectant strictement les règles d’exception qui interdisent l’utilisation de codes d’erreur. Deux modèles décrits dans cette section montrent comment procéder.

 **X DO NOT** utiliser des codes d’erreur en raison de problèmes qu’exceptions peuvent affecter négativement les performances.

 Pour améliorer les performances, il est possible d’utiliser le modèle testeur-Doer ou le modèle try-Parse, décrit dans les deux sections suivantes.

## <a name="tester-doer-pattern"></a>Modèle testeur-Doer
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

 Le membre utilisé pour tester une condition, qui, dans notre exemple, est `IsReadOnly`la propriété, est appelé testeur. Le membre utilisé pour effectuer une opération de levée potentielle, `Add` la méthode dans notre exemple, est appelé Doer.

 **✓ CONSIDER** le modèle utilisateur testeur pour les membres qui peuvent lever des exceptions en commun des scénarios pour éviter les problèmes de performances liés aux exceptions.

## <a name="try-parse-pattern"></a>Modèle try-parse
 Pour les API très performantes, il est préférable d’utiliser un modèle encore plus rapide que le modèle testeur-Doer décrit dans la section précédente. Le modèle appelle pour ajuster le nom de membre afin qu’un cas de test bien défini fasse partie de la sémantique de membre. Par exemple, <xref:System.DateTime> définit une <xref:System.DateTime.Parse%2A> méthode qui lève une exception en cas d’échec de l’analyse d’une chaîne. Il définit également une méthode <xref:System.DateTime.TryParse%2A> correspondante qui tente d’analyser, mais retourne la valeur false si l’analyse échoue et retourne le résultat d’une analyse réussie à l’aide `out` d’un paramètre.

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

 **✓ CONSIDER** le modèle d’analyse de Try pour les membres qui peuvent lever des exceptions en commun des scénarios pour éviter les problèmes de performances liés aux exceptions.

 **✓ DO** utilisent le préfixe « Try » et la valeur booléenne de type de retour pour les méthodes d’implémentation de ce schéma.

 **✓ DO** fournissent un membre levant des exceptions pour chaque membre de l’utilisation du modèle d’analyse de Try.

 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé par l’autorisation de Pearson Education, Inc. à [partir des instructions de conception d’infrastructure: Conventions, idiomes et modèles pour les bibliothèques .net réutilisables, 2nd](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Edition de Krzysztof Cwalina et Brad Abrams, publié le 22 octobre, 2008 de Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Instructions de conception pour les exceptions](../../../docs/standard/design-guidelines/exceptions.md)
