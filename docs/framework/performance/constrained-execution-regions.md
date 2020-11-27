---
title: régions d'exécution limitée
description: Prise en main des régions d’exécution limitée (CER), qui font partie d’un mécanisme de création de code managé fiable.
ms.date: 03/30/2017
helpviewer_keywords:
- constrained execution regions
- CERs
ms.assetid: 99354547-39c1-4b0b-8553-938e8f8d1808
ms.openlocfilehash: 5014885e186b1fff16543c09d5652958f2463e3d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266855"
---
# <a name="constrained-execution-regions"></a>régions d'exécution limitée

Une région d’exécution limitée (CER, Constrained Execution Region) fait partie d’un mécanisme pour la création de code managé fiable. Elle définit une zone dans laquelle le Common Language Runtime (CLR) ne peut pas lever d’exceptions hors-bande qui empêcheraient le code dans la zone de s’exécuter dans son intégralité. Dans cette région, le code utilisateur ne peut pas exécuter de code qui entraînerait la levée d’exceptions hors-bande. La méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> doit précéder immédiatement un bloc `try`, et marque les blocs `catch`, `finally` et `fault` en tant que régions d’exécution limitée. Une fois marqué comme région limitée, le code doit appeler uniquement du code avec des contrats de fiabilité forts, et il ne doit pas allouer ou effectuer des appels virtuels à des méthodes non préparées ou non fiables, sauf s’il est prêt à gérer les échecs. Le CLR retarde les abandons de thread pour le code qui s’exécute dans une région CER.  

> [!IMPORTANT]
> CER est pris en charge uniquement dans .NET Framework. Cet article ne s’applique pas à .NET Core ou .NET 5 et versions ultérieures.

 Les régions d’exécution limitée sont utilisées sous des formes différentes dans le CLR en plus d’un bloc `try` annoté, notamment sous forme de finaliseurs critiques exécutés dans des classes dérivées de la classe <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> et de code exécuté à l’aide de la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A>.  
  
## <a name="cer-advance-preparation"></a>Préparation avancée de région CER  

 Le CLR prépare les régions CER à l’avance pour éviter toute condition de mémoire insuffisante. Une préparation est nécessaire pour que le CLR ne provoque pas d’insuffisance de mémoire pendant le chargement de type ou la compilation juste-à-temps.  
  
 Le développeur doit obligatoirement indiquer qu’une région de code est une région CER :  
  
- La région CER et les méthodes de niveau supérieur dans le graphique des appels complet auxquels l’attribut <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> est appliqué sont préparées à l’avance. Le <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> peut déclarer uniquement des garanties <xref:System.Runtime.ConstrainedExecution.Cer.Success> ou <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>.  
  
- La préparation ne peut pas être effectuée pour les appels qui ne peuvent pas être déterminés statiquement, comme par exemple en cas de dispatch virtuel. Dans ces cas-là, utilisez la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>. Quand vous utilisez la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A>, l’attribut <xref:System.Runtime.ConstrainedExecution.PrePrepareMethodAttribute> doit être appliqué au code de nettoyage.  
  
## <a name="constraints"></a>Contraintes  

 Les utilisateurs sont limités quant au type de code qu’ils peuvent écrire dans une région CER. Le code ne peut pas provoquer d’exceptions hors-bande, telles que celles dues aux opérations suivantes :  
  
- Allocation explicite  
  
- Boxing  
  
- Acquisition d’un verrou  
  
- Appel de méthodes non préparées de manière virtuelle  
  
- Appel de méthodes avec un contrat de fiabilité faible ou inexistant  
  
 Dans le .NET Framework version 2.0, ces contraintes sont des recommandations. Des diagnostics sont fournis par les outils d’analyse du code.  
  
## <a name="reliability-contracts"></a>Contrats de fiabilité  

 <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> est un attribut personnalisé qui documente les garanties de fiabilité et l’état d’altération d’une méthode donnée.  
  
### <a name="reliability-guarantees"></a>Garanties de fiabilité  

 Les garanties de fiabilité, représentées par des valeurs d’énumération <xref:System.Runtime.ConstrainedExecution.Cer>, indiquent le degré de fiabilité d’une méthode donnée :  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.MayFail>. Dans des conditions exceptionnelles, la méthode peut échouer. Dans ce cas, elle indique à la méthode appelante si elle a réussi ou échoué. La méthode doit être contenue dans une région CER pour que vous soyez sûr qu’elle puisse signaler la valeur de retour.  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.None>. La méthode, le type et l’assembly n’ont aucun concept de région CER. Il est probablement risqué de les appeler dans une région CER sans atténuation substantielle contre les risques d’altération de l’état. Ils ne tirent pas parti des garanties offertes par les régions CER. Cela implique ce qui suit :  
  
    1. Dans des conditions exceptionnelles, la méthode peut échouer.  
  
    2. La méthode ne signale pas nécessairement qu’elle a échoué.  
  
    3. La méthode n’est pas écrite pour utiliser une région CER, le scénario le plus probable.  
  
    4. Si une méthode, un type ou un assembly n’est pas identifié de manière explicite pour réussir, il est implicitement identifié comme <xref:System.Runtime.ConstrainedExecution.Cer.None>.  
  
- <xref:System.Runtime.ConstrainedExecution.Cer.Success>. Dans des conditions exceptionnelles, la réussite de la méthode est garantie. Pour atteindre ce niveau de fiabilité, vous devez toujours construire une région CER autour de la méthode appelée, même quand elle est appelée dans une région non-CER. Une méthode réussit si elle accomplit ce qui est prévu, bien que la réussite puisse être considérée comme subjective. Par exemple, le fait de marquer Count avec `ReliabilityContractAttribute(Cer.Success)` implique qu’en cas d’exécution dans une région CER, elle retourne toujours le nombre d’éléments dans le <xref:System.Collections.ArrayList> et ne peut jamais laisser les champs internes dans un état indéterminé.  Toutefois, la méthode <xref:System.Threading.Interlocked.CompareExchange%2A> est aussi marquée comme ayant réussi, étant entendu que la réussite peut signifier que la valeur n’a pas pu être remplacée par une nouvelle valeur à cause d’une condition de concurrence.  Le point essentiel est que la méthode se comporte de la manière documentée, et que le code de région CER n’a pas besoin d’être écrit pour s’attendre à un comportement inhabituel au-delà de ce à quoi peut ressembler du code correct mais non fiable.  
  
### <a name="corruption-levels"></a>Niveaux d’altération  

 Les niveaux d’altération, représentés par des valeurs d’énumération <xref:System.Runtime.ConstrainedExecution.Consistency>, indiquent dans quelle mesure l’état peut être altéré dans un environnement donné :  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptAppDomain>. Dans des conditions exceptionnelles, le CLR n’offre aucune garantie quant à la cohérence de l’état dans le domaine d’application actuel.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance>. Dans des conditions exceptionnelles, il est garanti que la méthode limite l’altération de l’état à l’instance actuelle.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.MayCorruptProcess>. Dans des conditions exceptionnelles, le CLR n’offre aucune garantie quant à la cohérence de l’état. Autrement dit, la condition peut endommager le processus.  
  
- <xref:System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState>. Dans des conditions exceptionnelles, il est garanti que la méthode n’altère pas l’état.  
  
## <a name="reliability-trycatchfinally"></a>Bloc try/catch/finally de fiabilité  

 Le bloc `try/catch/finally` de fiabilité est un mécanisme de gestion des exceptions offrant les mêmes garanties de prévisibilité que la version non managée. Le bloc `catch/finally` est la région CER. Les méthodes dans le bloc exigent une préparation et doivent être non interruptibles.  
  
 Dans le .NET Framework version 2.0, le code informe le runtime qu’une tentative est fiable en appelant <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> juste avant un bloc try. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> est un membre de <xref:System.Runtime.CompilerServices.RuntimeHelpers>, une classe de prise en charge du compilateur. Appelez <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> directement en attendant sa disponibilité par le biais des compilateurs.  
  
## <a name="noninterruptible-regions"></a>Régions non interruptibles  

 Une région non interruptible regroupe un ensemble d’instructions dans une région CER.  
  
 Dans le .NET Framework version 2.0, dans l’attente de la disponibilité par le biais de la prise en charge du compilateur, le code utilisateur crée des régions non interruptibles avec un bloc try/catch/finally fiable qui contient un bloc try/catch vide précédé d’un appel de méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.  
  
## <a name="critical-finalizer-object"></a>Objet finaliseur critique  

 Un <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject> garantit que le garbage collection exécutera le finaliseur. Lors de l’allocation, le finaliseur et son graphique des appels sont préparés à l’avance. La méthode de finaliseur s’exécute dans une région CER et doit respecter toutes les contraintes sur les régions CER et les finaliseurs.  
  
 Pour tout type héritant de <xref:System.Runtime.InteropServices.SafeHandle> et <xref:System.Runtime.InteropServices.CriticalHandle>, il est garanti que son finaliseur s’exécute dans une région CER. Implémentez <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> dans les classes dérivées <xref:System.Runtime.InteropServices.SafeHandle> pour exécuter tout code devant libérer le handle.  
  
## <a name="code-not-permitted-in-cers"></a>Code non autorisé dans les régions CER  

 Les opérations suivantes ne sont pas autorisées dans les régions CER :  
  
- Allocations explicites  
  
- Acquisition d’un verrou  
  
- Boxing  
  
- Accès à un tableau multidimensionnel  
  
- Appels de méthode par réflexion  
  
- <xref:System.Threading.Monitor.Enter%2A> ou <xref:System.IO.FileStream.Lock%2A>.  
  
- Vérifications de sécurité. N’effectuez pas de demande, mais uniquement des demandes de liaison.  
  
- <xref:System.Reflection.Emit.OpCodes.Isinst> et <xref:System.Reflection.Emit.OpCodes.Castclass> pour les proxys et les objets COM  
  
- Obtention ou définition de champs sur un proxy transparent.  
  
- Sérialisation.  
  
- Pointeurs de fonction et délégués.  
  
## <a name="see-also"></a>Voir aussi

- [Meilleures pratiques pour la fiabilité](reliability-best-practices.md)
