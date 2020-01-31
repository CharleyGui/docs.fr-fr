---
title: Utilisation de types d'exceptions standard
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743538"
---
# <a name="using-standard-exception-types"></a>Utilisation de types d'exceptions standard
Cette section décrit les exceptions standard fournies par l’infrastructure et les détails de leur utilisation. La liste n’est pas exhaustive. Pour plus d’informations sur l’utilisation d’autres types d’exception d’infrastructure, consultez la documentation de référence .NET Framework.

## <a name="exception-and-systemexception"></a>Exception et SystemException
 ❌ ne levez pas <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.

 ❌ n’interceptez pas `System.Exception` ou `System.SystemException` dans le code d’infrastructure, sauf si vous envisagez de lever à nouveau.

 ❌ éviter d’intercepter `System.Exception` ou `System.SystemException`, sauf dans les gestionnaires d’exceptions de niveau supérieur.

## <a name="applicationexception"></a>ApplicationException
 ❌ ne levez pas ou ne dérivez pas de <xref:System.ApplicationException>.

## <a name="invalidoperationexception"></a>InvalidOperationException
 ✔️ lèvent une <xref:System.InvalidOperationException> si l’objet est dans un État inapproprié.

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException et ArgumentOutOfRangeException
 ✔️ lèvent <xref:System.ArgumentException> ou l’un de ses sous-types si des arguments incorrects sont passés à un membre. Préférer le type d’exception le plus dérivé, le cas échéant.

 ✔️ définir la propriété `ParamName` lors de la levée de l’une des sous-classes de `ArgumentException`.

 Cette propriété représente le nom du paramètre qui a provoqué la levée de l’exception. Notez que la propriété peut être définie à l’aide de l’une des surcharges de constructeur.

 ✔️ Utilisez `value` pour le nom du paramètre de valeur implicite des accesseurs set de propriété.

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException et AccessViolationException
 ❌ n’autorisez pas les API pouvant être appelées publiquement à lever <xref:System.NullReferenceException>, <xref:System.AccessViolationException>ou <xref:System.IndexOutOfRangeException>de manière explicite ou implicite. Ces exceptions sont réservées et levées par le moteur d’exécution et, dans la plupart des cas, indiquent un bogue.

 Procédez à la vérification des arguments pour éviter de lever ces exceptions. La levée de ces exceptions expose les détails d’implémentation de votre méthode qui peuvent changer au fil du temps.

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌ ne levez pas explicitement <xref:System.StackOverflowException>. L’exception doit être levée explicitement uniquement par le CLR.

 ❌ n’interceptent pas `StackOverflowException`.

 Il est presque impossible d’écrire du code managé qui reste cohérent en présence de dépassements de pile arbitraires. Les parties non managées du CLR restent cohérentes en utilisant des sondes pour déplacer les débordements de pile vers des emplacements bien définis plutôt que en sauvegardant des débordements de pile arbitraires.

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌ ne levez pas explicitement <xref:System.OutOfMemoryException>. Cette exception doit être levée uniquement par l’infrastructure CLR.

## <a name="comexception-sehexception-and-executionengineexception"></a>COMException, SEHException et ExecutionEngineException
 ❌ ne levez pas explicitement <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>et <xref:System.Runtime.InteropServices.SEHException>. Ces exceptions doivent être levées uniquement par l’infrastructure CLR.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Instructions de conception pour les exceptions](../../../docs/standard/design-guidelines/exceptions.md)
