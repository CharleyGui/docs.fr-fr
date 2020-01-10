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
ms.openlocfilehash: 6b202d618d9d2216c8998181303250081de6781c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708982"
---
# <a name="using-standard-exception-types"></a>Utilisation de types d'exceptions standard
Cette section décrit les exceptions standard fournies par l’infrastructure et les détails de leur utilisation. La liste n’est pas exhaustive. Pour plus d’informations sur l’utilisation d’autres types d’exception d’infrastructure, consultez la documentation de référence .NET Framework.  
  
## <a name="exception-and-systemexception"></a>Exception et SystemException  
 **X DO NOT** lever <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X DO NOT** catch `System.Exception` ou `System.SystemException` dans le code d’infrastructure, sauf si vous souhaitez lever de nouveau.  
  
 **X AVOID** interception `System.Exception` ou `System.SystemException`, sauf dans les gestionnaires d’exceptions de niveau supérieur.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** lever ou dériver de <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** lever un <xref:System.InvalidOperationException> si l’objet est dans un état inapproprié.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException et ArgumentOutOfRangeException  
 **✓ DO** lever <xref:System.ArgumentException> ou l’un de ses sous-types si des arguments incorrects sont passés à un membre. Préférer le type d’exception le plus dérivé, le cas échéant.  
  
 **✓ DO** définir le `ParamName` propriété lors de la levée d’une des sous-classes de `ArgumentException`.  
  
 Cette propriété représente le nom du paramètre qui a provoqué la levée de l’exception. Notez que la propriété peut être définie à l’aide de l’une des surcharges de constructeur.  
  
 **✓ DO** utiliser `value` pour le nom du paramètre de valeur implicite d’accesseurs Set de propriété.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException et AccessViolationException  
 **X DO NOT** autoriser API pouvant être appelées publiquement à lever explicitement ou implicitement <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, ou <xref:System.IndexOutOfRangeException>. Ces exceptions sont réservées et levées par le moteur d’exécution et, dans la plupart des cas, indiquent un bogue.  
  
 Procédez à la vérification des arguments pour éviter de lever ces exceptions. La levée de ces exceptions expose les détails d’implémentation de votre méthode qui peuvent changer au fil du temps.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** lever explicitement <xref:System.StackOverflowException>. L’exception doit être levée explicitement uniquement par le CLR.  
  
 **X DO NOT** catch `StackOverflowException`.  
  
 Il est presque impossible d’écrire du code managé qui reste cohérent en présence de dépassements de pile arbitraires. Les parties non managées du CLR restent cohérentes en utilisant des sondes pour déplacer les débordements de pile vers des emplacements bien définis plutôt que en sauvegardant des débordements de pile arbitraires.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** lever explicitement <xref:System.OutOfMemoryException>. Cette exception doit être levée uniquement par l’infrastructure CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>COMException, SEHException et ExecutionEngineException  
 **X DO NOT** lever explicitement <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, et <xref:System.Runtime.InteropServices.SEHException>. Ces exceptions doivent être levées uniquement par l’infrastructure CLR.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Instructions de conception pour les exceptions](../../../docs/standard/design-guidelines/exceptions.md)
