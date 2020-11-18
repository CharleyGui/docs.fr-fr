---
title: Utilisation de types d'exceptions standard
description: En savoir plus sur les types d’exceptions standard dans .NET. En savoir plus sur SystemException, ApplicationException, ArgumentException, COMException et bien plus encore.
ms.date: 10/22/2008
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: d8e75f7104b755476f255563c9c1f7ece14f67db
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828463"
---
# <a name="using-standard-exception-types"></a>Utilisation de types d'exceptions standard
Cette section décrit les exceptions standard fournies par l’infrastructure et les détails de leur utilisation. La liste n’est pas exhaustive. Pour plus d’informations sur l’utilisation d’autres types d’exception d’infrastructure, consultez la documentation de référence .NET Framework.

## <a name="exception-and-systemexception"></a>Exception et SystemException
 ❌ NE levez pas <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType> .

 ❌ N’interceptez pas `System.Exception` ou `System.SystemException` dans le code d’infrastructure, sauf si vous envisagez de lever à nouveau.

 ❌ Évitez d’intercepter `System.Exception` ou `System.SystemException` , sauf dans les gestionnaires d’exceptions de niveau supérieur.

## <a name="applicationexception"></a>ApplicationException
 ❌ NE levez pas ou ne dérivez pas de <xref:System.ApplicationException> .

## <a name="invalidoperationexception"></a>InvalidOperationException
 ✔️ Levez une exception <xref:System.InvalidOperationException> si l’objet est dans un État inapproprié.

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException et ArgumentOutOfRangeException
 ✔️ ne levez pas <xref:System.ArgumentException> d’exception ou un de ses sous-types si des arguments incorrects sont passés à un membre. Préférer le type d’exception le plus dérivé, le cas échéant.

 ✔️ définir la propriété lors de la levée de l' `ParamName` une des sous-classes de `ArgumentException` .

 Cette propriété représente le nom du paramètre qui a provoqué la levée de l’exception. Notez que la propriété peut être définie à l’aide de l’une des surcharges de constructeur.

 ✔️ Utilisez `value` pour le nom du paramètre de valeur implicite des accesseurs set de propriété.

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException et AccessViolationException
 ❌ N’autorisez pas les API pouvant être appelées publiquement à lever explicitement ou implicitement <xref:System.NullReferenceException> , <xref:System.AccessViolationException> ou <xref:System.IndexOutOfRangeException> . Ces exceptions sont réservées et levées par le moteur d’exécution et, dans la plupart des cas, indiquent un bogue.

 Procédez à la vérification des arguments pour éviter de lever ces exceptions. La levée de ces exceptions expose les détails d’implémentation de votre méthode qui peuvent changer au fil du temps.

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌ NE levez pas explicitement <xref:System.StackOverflowException> . L’exception doit être levée explicitement uniquement par le CLR.

 ❌ N’interceptez pas `StackOverflowException` .

 Il est presque impossible d’écrire du code managé qui reste cohérent en présence de dépassements de pile arbitraires. Les parties non managées du CLR restent cohérentes en utilisant des sondes pour déplacer les débordements de pile vers des emplacements bien définis plutôt que en sauvegardant des débordements de pile arbitraires.

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌ NE levez pas explicitement <xref:System.OutOfMemoryException> . Cette exception doit être levée uniquement par l’infrastructure CLR.

## <a name="comexception-sehexception-and-executionengineexception"></a>COMException, SEHException et ExecutionEngineException
 ❌ NE levez pas explicitement <xref:System.Runtime.InteropServices.COMException> ,  <xref:System.ExecutionEngineException> et <xref:System.Runtime.InteropServices.SEHException> . Ces exceptions doivent être levées uniquement par l’infrastructure CLR.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Instructions de conception pour les exceptions](exceptions.md)
